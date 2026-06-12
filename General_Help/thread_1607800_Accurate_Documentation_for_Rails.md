---
title: "Accurate Documentation for Rails?"
date: 2010-10-28
forum: General Help
---

### Post by newb85 on 2010-10-28
I was starting to teach myself Django, when I found out the site I want to create needs to be written in Ruby (hosting specs).  Django's documentation was extensive, easy-to-read, and build-specific.  My experience with Rails so far has been like a nightmare from the Twilight Zone: everything is actually something else.  :confused:

To teach myself, I thought I would use tutorial given at rubyonrails.org.  The tutorial said to use "rails new blog" to create a new project called "blog".  Instead, it created a new project called "new".  The syntax I really wanted was simply "rails blog".  To see the syntax specific to my build (for a few immediate objectives), I had to run "man rails" from the terminal and follow its instructions to use the instructions buried in "/usr/share/doc/rails/README.Debian".  

The next step in the tutorial was to install the required gems using "bundle install".  This simply issued the error message "bundle: command not found".  I could not find a variant of this that worked, so I'm hoping that the required gems are already installed.

To start up the web server, the tutorial said to use the command "rails server", but fortunately, I noticed that the README told me to use "script/server".  The default page I saw was just like the one shown in the tutorial, except that all the commands recommended in the page were different (no surprise there).

Unfortunately, when I tried to generate a controller and a view, I used the tutorial's "rails generate controller home index" instead of translating it using the default page on the server into "script/generate controller home index".  The result was that it did indeed create a bunch of folders and files, but not the ones I wanted.  (I think it created a new project within my project called "generate".)

I'm inducing from this that the syntax of my build has "rails ****" meaning what the tutorial means by "rails new ****".  This then bumps any commands the tutorial has listed as "rails ****" to "script/****".  I'm really hoping that not too much else has been switched, or that I at least find a central rosetta stone.

Does anyone have suggestions to make this less of an uphill battle?

---

### Post by newb85 on 2010-11-02
So I realize that my initial post was long-winded, and probably listed in the wrong category.

For anyone who finds themselves in the position I was in, here's what I concluded.

Accurate documentation for different versions of Ruby and Rails are available at railsapi.com.  At least, the API for different versions is there.  That's great for someone already familiar with the language who needs a reference (although, if they're familiar, they probably have a good reference).  However, the tutorial available there (by Michael Hartl), while excellent, is written for the latest version of Rails only.

My suggestion is for anyone looking to learn Rails to NOT insist on using the versions of Ruby and Rails in the Ubuntu repo.  Instead, follow the installation instructions in Hartl's tutorial to use RVM.  This will solve most of the headaches.

One drawback to Hartl's tutorial is that he is a Mac user, so at a few points, he states that a given step will be different for other systems, and leaves such users to find their version of that step on their own.

---

