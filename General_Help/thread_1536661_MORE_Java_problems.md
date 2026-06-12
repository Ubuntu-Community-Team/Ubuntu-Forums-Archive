---
title: "MORE Java problems"
date: 2010-07-22
forum: General Help
---

### Post by silvagroup on 2010-07-22
Have a work related training that I have to access.
Browser is Firefox 3.6.6, java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) 64-Bit Server VM (build 16.3-b01, mixed mode)

Once I get past login and the Jave goes through some applets it shows done at status bar but the lights are on and nobody is home !!!!! 
I had Icedtea and openjdk on the system which caused applet initiate problems, removed them and now I just sit looking at a please wait message, forever.
This happens on 9.10 on my desktop.

On my laptop which is 10.04 (upgraded from 9.10) w/icedtea and openjdk still installed it kind of works, except I only get half a screen when I get past the applet initialization, not extremely helpful.
Installed Vista on the laptop just so I can get the training done,sadly, yes site works great w/Firefox and Vista.

Really don't want to have Vista on laptop jsut for one web site so any help solving this would be greatly appreciated, let me know what other info you require, thanks in advance.

---

### Post by endotherm on 2010-07-22
when you installed the sun java, did you update your alternatives? if not, it may be using the openjre or icedtea to run the code despite having a sun jre installed. just a thought.

---

### Post by silvagroup on 2010-07-22
Yes I did that - sudo update-alternatives --config java.

Also checked Firefox config:
java.default_java_location_others;/usr/java
java.default_java_location_solaris;/usr/j2se
java.global_java_version_file;/etc/.java/versions
java.java_plugin_library_name;javaplugin_oji
java.private_java_version_file;~/.java/versions
javascript.enabled;true
javascript.options.jit.chrome;false
javascript.options.jit.content;true
javascript.options.relimit;falsejavascript.options.showInConsole;false
javascript.options.strict;false

Not really sure what I am looking for here though other than the java directories which appear correct, I think.

---

### Post by silvagroup on 2010-07-23
Have a solution, albeit far from the preferred solution, that being that Linux just work with java!!!!!

Here is the solution, I installed ie4linux, this uses wine to run MS Internet Explorer 6, then installed java, and flash player through IE6 and viola I can now do my training on my desktop. Rather interesting that wine uses java just fine but Linux itself doesn't ????  By the way anyone who does this please do not use this to do any internet browsing !!!! Keep using your Firefox.

I can also do this with my laptop but since I have already installed Vista I can just dual boot for now. But I may do it just to free up that half of the disk space that the Vista install took up just to run IE8.

IE4LINUX does have a small but annoying quirk, when I exit IE, wineserver is still running and taking up tons of CPU usage, so I need to kill the process and all is well again in desktop land.

---

### Post by silvagroup on 2010-07-28
Found another partial solution again far from perfect because I am still dependent on Microsoft, and it doesn't do much to save disk space, but don't have to dual boot: one can run Firefox or IE in Windows running in a Virtual Machine.

---

