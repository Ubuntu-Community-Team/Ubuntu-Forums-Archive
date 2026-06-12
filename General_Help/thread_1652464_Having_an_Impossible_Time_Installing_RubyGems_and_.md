---
title: "Having an Impossible Time Installing RubyGems and Ruby 1.92"
date: 2010-12-24
forum: General Help
---

### Post by fastveg on 2010-12-24
Hey all,

I am having an extremely difficult time installing RubyGems and Ruby 1.9.2 onto a fresh install of ubuntu 10.10. I've been working at it for hours now, and things always seems to break new and exciting ways.

The end goal is just to install sproutcore, using the command "gem install sproutcore"  Sounds easy right?  I really need some assistance if anyone can help me through the process.

Right now I think 1.9.2 is installed, but ruby -v doesn't return a version.  And rubygems 1.3.7 should be installed as well, but gem -v doesn't return a version either.  How can I make ruby and rubygems work?

---

### Post by RavensKrag on 2011-01-02
What's happening is that when Ubuntu installs the ruby1.9.1 stuff, it makes all the executables have 1.9.1 at the end.  Thus, you would have to do ruby1.9.1 -v to get the version.  This is very odd in 10.10, as the package ruby1.9.1 actually installs ruby 1.9.2.  Likewise, gem is installed as part of the ruby1.9.1 package, but the executable is called gem1.9.1.

If you want to simply be able to use commands like 'ruby' and 'gem', then follow the instructions in this thread.

[http://ubuntuforums.org/showthread.php?p=10306714#post10306714](http://ubuntuforums.org/showthread.php?p=10306714#post10306714)

---

