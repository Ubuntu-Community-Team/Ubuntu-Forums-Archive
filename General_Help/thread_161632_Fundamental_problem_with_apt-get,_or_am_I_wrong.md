---
title: "Fundamental problem with apt-get, or am I wrong?"
date: 2006-04-17
forum: General Help
---

### Post by sb73542 on 2006-04-17
Hello,

I run Ubuntu on an old laptop with a 3GB harddrive, so disk space is a big issue for me.  It seems there is a problem with the whole concept of how apt-get works.  Here's a situation:

If I want to try out program-X, I do "apt-get install program-X".  But almost always, program-X (1.2 MB) depends on libprog-x (6 MB) and libsomething (3MB), and libsomething requires libhelper (420KB) and libother (390 KB).  

It's all good when I'm installing, but what if I decide I don't like program-X, and want to get rid of it entirely?  I do "apt-get remove program-X".  So this uninstalls "program-X", thus freeing me of 1.2MB of space.  What about the additional 10MB of clutter left on my hard drive from the other dependancies that got auto-installed, but not auto-removed?  Do I just have to make a manual list of dependancies installed every time I try out a program?  Any suggestions?

Thanks!

---

### Post by towsonu2003 on 2006-04-17
not sure, but try deborphan: it reports not-any-more-used libraries for you to see if you wanna uninstall that stuff.

---

### Post by niviche on 2006-04-17
[QUOTE=sb73542]Do I just have to make a manual list of dependancies installed every time I try out a program?[/QUOTE]

Get the latest version of [deborphan](http://packages.debian.org/testing/admin/deborphan), then get [Gtkorphan](http://www.marzocca.net/linux/gtkorphan.html#download). You can use this to uninstall packages who are not needed anymore and erase configuration files for uninstalled programs.

---

### Post by towsonu2003 on 2006-04-17
[QUOTE=niviche]Get the latest version of [deborphan](http://packages.debian.org/testing/admin/deborphan), then get [Gtkorphan](http://www.marzocca.net/linux/gtkorphan.html#download). You can use this to uninstall packages who are not needed anymore and erase configuration files for uninstalled programs.[/QUOTE]
it's available in the repos: sudo apt-get install deborphan

not sure about gtkorphan (check synaptic or packages.ubuntu.com[1]), though it's very easy to use in command line:
```
deborphan
``` and it will list libraries

[1]if not using apt-get, pay special attention to dependencies...

---

### Post by niviche on 2006-04-17
[QUOTE=towsonu2003]it's available in the repos: sudo apt-get install deborphan[/QUOTE]

Yes, but this version is too old for the latest one of GTKorphan.

---

### Post by towsonu2003 on 2006-04-17
[QUOTE=niviche]Yes, but this version is too old for the latest one of GTKorphan.[/QUOTE]
oh ok sorry

---

### Post by sb73542 on 2006-04-17
Thank you guys!  That sounds like a pretty decent solution.  Although it would be nice if apt-get had an option like "remove-all-deps-installed-at-same-if-not-used-by-anything-else". ;)   

So deborphan will only report unused libs?  Would it also report programs upon which nothing depends, i.e. Opera or some other fairly monolithic software?  If so, one would have to make sure they don't delete any currently-used programs.

Thanks again!

---

### Post by jrib on 2006-04-17
[QUOTE=sb73542]Hello,

I run Ubuntu on an old laptop with a 3GB harddrive, so disk space is a big issue for me.  It seems there is a problem with the whole concept of how apt-get works.  Here's a situation:

If I want to try out program-X, I do "apt-get install program-X".  But almost always, program-X (1.2 MB) depends on libprog-x (6 MB) and libsomething (3MB), and libsomething requires libhelper (420KB) and libother (390 KB).  

It's all good when I'm installing, but what if I decide I don't like program-X, and want to get rid of it entirely?  I do "apt-get remove program-X".  So this uninstalls "program-X", thus freeing me of 1.2MB of space.  What about the additional 10MB of clutter left on my hard drive from the other dependancies that got auto-installed, but not auto-removed?  Do I just have to make a manual list of dependancies installed every time I try out a program?  Any suggestions?

Thanks![/QUOTE]

If you use aptitude instead, it will work just like you want it to.
```
sudo aptitude install X
```
will install X with all of its dependencies and remember them
```
sudo aptitude remove X
```
will remove X and the dependencies that got installed along with X as long as they aren't needed anymore (assuming X was installed using aptitude)

---

### Post by towsonu2003 on 2006-04-17
[QUOTE=sb73542]
So deborphan will only report unused libs?  Would it also report programs upon which nothing depends, i.e. Opera or some other fairly monolithic software?  If so, one would have to make sure they don't delete any currently-used programs.
[/QUOTE]
it will only list libraries (lib<blablabla>) but you'll have a chance to keep whatever you might want to keep. 

I used it once and chose to keep library names that were somehow familiar.

---

