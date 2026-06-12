---
title: "Firefox and Java plugin"
date: 2010-08-27
forum: General Help
---

### Post by DeadlyOats on 2010-08-27
I opened Firefox, and tried to use an Internet speed tester that requires Java.  I've always used this with no problems.  Today, I'm having problems with it.  It told me to check that my Java plugin was enabled, or whatnot.  I looked at Tools > Add-Ons > Plugins, and found that Java is gone....

What's up with that?  I'm using the latest version of Firefox (version 3.6.8 / Mozilla Firefox for Ubuntu cononical - 1.0) on Ubuntu 9.10.

I checked with Synaptic Package Manager, and I found sun-java6-jre, and all of it's related packages, openjdk-6jre-* packages, etc. were installed (over ten packages with 'java' or 'jre' and '6' in the package names).

So, I don't understand why Tools > Add-Ons > Plugins doesn't show my java plugin anymore.  I also checked about: plugins (had to put a space between the colon and 'plugins' because a smiley shows up about:plugins), but there was nothing in there about java either.

What's going on?  Has Ubuntu decided it doesn't want to use Java (I remember reading something about Oracle changing the license for Sun Java somewhere)?  Or is this a fluke?

Either way.  I need to fix this.  Plainly, Synaptic Package Manager says Java is installed...  So, what else do I need to do to fix this?  I read other posts about Firefox and Java, but they were about installing java, and the like, and I have Java installed....  It's confusing...

Thank you kindly for your help with this issue.

---

### Post by garvinrick4 on 2010-08-27
Close Firefox:
```
sudo apt-get clean
```
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```Just to check you have them.
If says you have them uninstall and reinstall.
Make sure you apt-get clean first to get a fresh package.
Something to try.

---

### Post by DeadlyOats on 2010-08-27
O.K.  Here are the results:

(This is a true story.  The names were changed to protect the innocent.)

> Username@mymachine:~$ sudo apt-get clean
[sudo] password for Username: 
Username@mymachine:~$ sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="Red"]sun-java6-jre is already the newest version[/COLOR].
The following packages were automatically installed and are no longer required:
  libjline-java rhino
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  sun-java6-plugin
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 1,860B of archives.
After this operation, 61.4kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse sun-java6-plugin 6.20dlj-0ubuntu1.9.10 [1,860B]
Fetched 1,860B in 0s (3,070B/s)          
Selecting previously deselected package sun-java6-plugin.
(Reading database ... 167806 files and directories currently installed.)
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6.20dlj-0ubuntu1.9.10_i386.deb) ...
Setting up sun-java6-plugin (6.20dlj-0ubuntu1.9.10) ...

Username@mymachine:~$ 

It said, the it was already the newest version, but as you can see, it did a re-install anyway.  I think it got rid of some other stuff, but I don't know if that other stuff was replaced, or just made to disappear...

I rebooted Firefox and then took a look at Tools>Add-ons>Plugins, and *LOW AND BEHOLD*, the java plugin is back!  I tested it on various sites requiring java, and they work.  They don't ask me to check to see if java is installed or whatnot.

Thanks a lot, garvinrick4.  That fixed it.

---

