---
layout: narrow_page
title: Deploy Your Ruby App Right Now
comments: false
sharing: false
sidebar: false
footer: true
no_navbar: true
---
## Ruby Mad Science

On a Mac? Here's how to deploy a test app to Vagrant.

    gem madscience install
    rvmsudo madscience setup  # install tools
    git clone https://github.com/noahgibbs/madscience
    cd madscience
    vagrant up --provision
    vagrant push development

Edit nodes/all_nodes.json.erb in that repo you cloned and it will clone your
own real Rails (or Rack) app instead.

After that, here's the same thing to real production:

    vagrant up --provision --provider=digital_ocean
    vagrant push digital_ocean

If you edited that file to put in your app, and one more to add your Digital
Ocean creds... Then your app is running on Digital Ocean.

<img class="pull-right" src="/images/mad_scientist_01.jpg" alt="A scientist with a steaming flask"></img>

Want to get started?

<a href="http://github.com/noahgibbs/madscience">Here's the GitHub repo</a>.

(Worried about the license? It's MIT.)

### Why Not Just Use Chef or Ansible or Whatever For Myself?

Ever set those up? There are a lot of steps and the debugging sucks. This uses
Chef under the hood, so you're getting that, but with the first few days of
suck handled already.

Ruby Mad Science uses the right tools - Chef, Capistrano, Vagrant and
Librarian as deploy tools, and NGinX, RVM, Unicorn and more to run your
app. You could set all that up, or you could let Ruby Mad Science do it. Which
one gets you back to coding faster?

It's a solid stack of tools, and every version is carefully locked down so it
keeps working. That takes some doing, even with config management tools like
Chef.

It's secured reasonably. Deploy and provisioning keys are automatically
generated and are easy to change. Passwords and SSH keys are stored outside
the deploy repo in a credentials directory under your home directory. You
could do that, too. But all these things will take time. Want to get back to
coding?

Despite all those tools, Ruby Mad Science has a simple top level -- a JSON
file is used to give the Chef runlist, the set of apps to deploy with
Capistrano and (by default) even the third-party cookbooks to set up using the
Cheffile. Usually deploy tools are all about repeating yourself. Constantly.

Ruby Mad Science is opinionated but customizable. It's easy to add third-party
cookbooks and Capistrano tasks, and you can diverge entirely from the repo you
checked out if you need to -- there's not a huge amount of code and it's
basically all in your deploy repo, in source control.

Out of the box, Ruby Mad Science supports MySQL and Postgres, Redis, MemCache
and more if you need them for your Rails app (please don't use SQLite in
production.) Infrastructure like MemCache with a standard Chef cookbook can be
added in just a few lines. If you need infrastructure that doesn't have a
standard Chef cookbook, write a cookbook and you can use it from your deploy
repo.

By default you can give a convenient list of Rails/Rack apps and static sites
in simple JSON format and they get installed and just work nicely. Start easy,
configure as you go.

### Why Not Heroku?

It's hard to beat Heroku for getting started quick. However, Heroku is
expensive and doesn't always give you the control you need. Also, you have to
rely on them as a third-party service instead of picking your own hosting and
choosing how your server is installed. For more details: <a
href="http://codefol.io/posts/when-should-you-not-use-heroku">When Should You
Not Use Heroku?</a>

Ruby Mad Science is different. It uses normal open source deploy tools. The
Ruby Mad Science source is open (and short!) And it's really easy to modify
your repo to do what you want.

Ruby Mad Science is less of an all-in-one solution and more the jumping-off
point you want when you start a new project on a server.

### How's the Support?

This is an open-source project. It's always nice to get a guarantee of more
support than that, when you can.

I sell documentation and support for this code <a
href="http://rails-deploy-in-an-hour.com">as Rails Deploy In An Hour</a>. It's
the class the code came from originally. But I wanted my customers to be able
to use the code for all kinds of projects, and that means open source under a
permissive license.

### What License?

MIT. That means you can use this for open-source and commercial projects
without a problem. I'd appreciate if you contribute fixes back, but you're not
required to. It's up to you.

<a href="http://github.com/noahgibbs/madscience">The GitHub
project</a> has issues, accepts pull requests and so on like you're used to.

### What? Who? Why?

My name is Noah Gibbs. I wrote the book <a
href="http://rebuilding-rails.com">Rebuilding Rails</a> awhile back. When I
built <a href="http://rails-deploy-in-an-hour.com">Rails Deploy In An Hour</a>
I figured, "why not make the code open source?"

It's easy enough to use, after all. And it'd be a shame to restrict it to
customers. Plus, people using tools like Chef, Capistrano and Vagrant can
<b>really</b> use a quick start instead of one more book telling them how to
use each tool and giving already-out-of-date lists of commands to type and
file contents to cut and paste. This is a pretty darn quick start.

### Misc Credits

The scientist picture is courtesy of San Jose Library, via Flickr.
