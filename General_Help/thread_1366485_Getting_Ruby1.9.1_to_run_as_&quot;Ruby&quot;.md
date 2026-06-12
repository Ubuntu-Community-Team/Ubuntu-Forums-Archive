---
title: "Getting Ruby1.9.1 to run as &quot;Ruby&quot;"
date: 2009-12-28
forum: General Help
---

### Post by coreills on 2009-12-28
Hi all,

I'm trying to develop something in Rails and am running into a few roadblocks getting things up and running.

I was having a lot of trouble getting Ruby and Rubygems to play nice before, so I ripped out the whole thing in Synaptic and reinstalled Ruby1.9.1, Rubygems1.9.1 and the associated packages using apt-get from the terminal.

This was all well and good up to the point that I could run Ruby using ruby1.9.1 from the terminal. I set up an alias in my bashrc, ruby="ruby1.9.1" and all was good for a while.

When I came to running the server script in Rails, it didn't like it, but I changed the first line from

#!/usr/bin/env ruby
to
#!/usr/bin/env ruby1.9.1

ran it again and it worked fine. A similar thing happened with the console script, but this time it wouldn't play so nice.

My question, then, is what should I do? From what I can gather (I'm pretty new to Linux) I need to do one of two things:
* set a universal bash alias so that ruby goes to ruby1.9.1 for all script commands, not just my own. As I understand it, when I type ruby into the terminal, it will substitute for ruby1.9.1, but any scripts I run it will still try "ruby", which cannot be found. Is this how things work?
* install the ruby package using either Synaptic or apt-get and somehow configure it so that it runs version 1.9.1 of ruby and rubygems, rather than defaulting to version 1.8 as it currently does. Then there will actually be a ruby binary in /usr/bin and not just a ruby1.9.1 one and anything else invoking the ruby command will play nice.

They're the easy options, as I see it. The other seems to involve compiling from source with a --program-suffix argument, which, being relatively new I'm less comfortable doing, but will do if it's the only way!

Any advice on the issue would be greatly appreciated! Also, if I've got something wrong in my understanding that you can explain, please tell me! I've recently made the switch from Windows and would like to get some serious developing done after this, so anything that will add to my understanding would be grand!

All the best,

Christy

P.S. Forgot to mention, I'm using Ubuntu 9.10 64bit Desktop Edition

Edit: It's failing because the console script is trying to run irb, a binary which is actually called irb1.9.1 in the /usr/bin folder. So I guess a solution to the above would also fix this.

---

### Post by coreills on 2009-12-28
Hahar, I fixed it!

For those with similar problems, I created a shell script in /usr/bin called ruby which said simply

ruby1.9.1 $*

and chmodded it to 007.

A cheap hack? Maybe, but that's what Linux is all about, right? =D

All the best,

Christy

---

### Post by ean5533 on 2009-12-28
> **coreills said:**
> A cheap hack? Maybe, but that's what Linux is all about, right? =D

And so it all boils down to that: Linux is about cheap hacks. I love it. :)

---

### Post by instantsaint on 2010-03-31
Couldn't we simply make a symbolic link like
**ln -s ruby1.9.1 ruby**
But what about irb? and there might be some other pieces (ri? gems?) that may still have 1,9,1 suffixed to them.

---

### Post by coreills on 2010-05-21
Upon doing a fresh install of Lucid, I came back here to try and remember what the hell I did to get this to work.

Since I now know what a symlink is - yeah, that definitely works! But you're right, there are 8 different binaries suffixed with 1.9.1 in my /usr/bin.

Gem seems to work independently of Ruby versions, rake can be installed as a gem, so no problem there, but thus far I've had to symlink both ruby and irb like this to get it to play nice. There probably is an easier way, but heyho, it works seamlessly after this, so who's complaining?

---

### Post by krazyd on 2010-11-01
> **coreills said:**
> There probably is an easier way, but heyho, it works seamlessly after this, so who's complaining?

There is actually an easier way. Debian and derivatives such as Ubuntu have a system to handle multiple versions of various apps:

1. install both versions of ruby. note that rubygems is built-in to ruby1.9.1:

```
sudo aptitude install ruby rubygems ri ruby1.9.1 ri1.9.1
```

2. remove the alternative which is set up by default for gem:
```
sudo update-alternatives --remove-all gem
```

2. set up the ruby alternatives:
```
sudo update-alternatives --install /usr/bin/ruby ruby /usr/bin/ruby1.8 500 \
    --slave /usr/share/man/man1/ruby.1.gz ruby.1.gz \
            /usr/share/man/man1/ruby1.8.1.gz \
    --slave /usr/bin/ri ri /usr/bin/ri1.8 \
    --slave /usr/bin/irb irb /usr/bin/irb1.8 \
    --slave /usr/bin/gem gem /usr/bin/gem1.8

sudo update-alternatives --install /usr/bin/ruby ruby /usr/bin/ruby1.9.1 400 \
    --slave /usr/share/man/man1/ruby.1.gz ruby.1.gz \
            /usr/share/man/man1/ruby1.9.1.1.gz \
    --slave /usr/bin/ri ri /usr/bin/ri1.9.1 \
    --slave /usr/bin/irb irb /usr/bin/irb1.9.1 \
    --slave /usr/bin/gem gem /usr/bin/gem1.9.1
```

now to switch versions you just do:
```
sudo update-alternatives --config ruby
```

---

### Post by zalberico on 2010-12-24
Thank you,
Getting an up to date ruby/rails installation working in ubuntu is a nightmare.  I wish they would adopt a rolling release system like arch it would fix all of these annoying problems.  It appears to be working now though at least using 1.9.2.

---

### Post by RavensKrag on 2011-01-02
Thank you for the solution involving update-alternatives.  I had wanted a method using that system, but had been using the symlinks method instead.

If only Ubuntu set this up automatically...

---

### Post by jayrulez on 2011-01-12
> **krazyd said:**
> There is actually an easier way. Debian and derivatives such as Ubuntu have a system to handle multiple versions of various apps:

1. install both versions of ruby. note that rubygems is built-in to ruby1.9.1:

```
sudo aptitude install ruby rubygems ri ruby1.9.1 ri1.9.1
```

2. remove the alternative which is set up by default for gem:
```
sudo update-alternatives --remove-all gem
```

2. set up the ruby alternatives:
```
sudo update-alternatives --install /usr/bin/ruby ruby /usr/bin/ruby1.8 500 \
    --slave /usr/share/man/man1/ruby.1.gz ruby.1.gz \
            /usr/share/man/man1/ruby1.8.1.gz \
    --slave /usr/bin/ri ri /usr/bin/ri1.8 \
    --slave /usr/bin/irb irb /usr/bin/irb1.8 \
    --slave /usr/bin/gem gem /usr/bin/gem1.8

sudo update-alternatives --install /usr/bin/ruby ruby /usr/bin/ruby1.9.1 400 \
    --slave /usr/share/man/man1/ruby.1.gz ruby.1.gz \
            /usr/share/man/man1/ruby1.9.1.1.gz \
    --slave /usr/bin/ri ri /usr/bin/ri1.9.1 \
    --slave /usr/bin/irb irb /usr/bin/irb1.9.1 \
    --slave /usr/bin/gem gem /usr/bin/gem1.9.1
```

now to switch versions you just do:
```
sudo update-alternatives --config ruby
```


I followed this instruction. Everything works except that gem doesn't work with 1.9.2

I get the output when i try to use gem with 1.9.2

jayrulez@localhost:/usr/lib/ruby/1.8/rubygems$ gem -v
<internal:lib/rubygems/custom_require>:29:in `require': no such file to load -- rubygems (LoadError)
	from <internal:lib/rubygems/custom_require>:29:in `require'
	from <internal:gem_prelude>:167:in `load_full_rubygems_library'
	from <internal:gem_prelude>:217:in `try_activate'
	from <internal:lib/rubygems/custom_require>:32:in `rescue in require'
	from <internal:lib/rubygems/custom_require>:29:in `require'
	from /usr/bin/gem:8:in `<main>'

---

### Post by jar349 on 2011-09-18
I have the same problem.  When I use update-alternatives to switch over to ruby1.9.1, gems does not work.

```

$ sudo gem install rails
Building native extensions.  This could take a while...
ERROR:  Error installing rails:
	ERROR: Failed to build gem native extension.

/usr/bin/ruby1.9.1 extconf.rb
<internal:lib/rubygems/custom_require>:29:in `require': no such file to load -- mkmf (LoadError)
	from <internal:lib/rubygems/custom_require>:29:in `require'
	from extconf.rb:36:in `<main>'


Gem files will remain installed in /var/lib/gems/1.9.1/gems/bcrypt-ruby-3.0.1 for inspection.
Results logged to /var/lib/gems/1.9.1/gems/bcrypt-ruby-3.0.1/ext/mri/gem_make.out

```

---

