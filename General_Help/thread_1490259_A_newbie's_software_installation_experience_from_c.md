---
title: "A newbie's software installation experience from command line"
date: 2010-05-22
forum: General Help
---

### Post by unagimiyagi on 2010-05-22
Hi there,

Totally new but motivated to learn linux and the command line.  I understand the software center; it's kind of like an app store like itunes.  However, I want to become good at the command line.  Can someone comment as to whether my learning curve is normal?  I am finding that I need to unlearn everything about windows.

For example,  I just tried to install adobe flash from the command line.  

I have no idea what package and repository adobe flash is in.  So I went to google and searched for it.  I got a few hits, but none of these worked.  Finally on the fifth site, I found out that the package name is something like:

sudo apt-get install flash-plugin-installer

I must admit that I was frustrated at how hard I perceived this to be.  With flash, I had tried the graphical way as well, and even that was hard.  I got wrong architecture i386.  I downloaded the .deb file which I believe is a package file.  In my newbie head I was like "surely a company as huge as  Adobe would have an idiot-proof way of installing flash."  But idiot I  felt like.

In general, I can pretty easily use the software center. Synpatic is ok as well, but sometimes the multitude of choices is overwhelming.  Take java and eclipse, for example.  There are some packages that are dependent on each other, but all packages are listed separately.    So for eclipse, do I need to download eclipse with jdt and eclipse base package, or just eclipse with jdt, b/c in the description it states that this package contains all you need.  But in the base package it states that you always need the base package.  So this is where confusion lies.  As a newbie, I don't like the feeling of not knowing if I "got" all of the packages that I need.  I keep feeling like I need to check all the boxes just in case something doesn't work down the road.

But nevermind that for now.  I'm interested in how gurus install new software from the command line.  It seems like a catch-22--you gotta know the name of the package before you install it.  But finding out the name requires googling or trying to piece together which packages and subpackages you need, so I'm wondering how long it takes before this command line method is faster than the traditional gui method.  Right now I don't find the command line to be much faster for installing software b/c you really really have to know alot of command line kungfu to install software like adobe flash.

---

### Post by James78 on 2010-05-22
You can find the right software package through a GUI like Synaptic, then just 'sudo apt-get install <package>'. It is not recommended to install .deb's from the internet unless, a), you know they are trusted, b) there is no repository that has that specific package in it (or it's outdated), and c) it's not in the main repository.

Flash is in the main repository, so all you need to do is find out the name by doing a simple search in Synaptic, then sudo apt-get install <package>

A useful technique to remember, is that if you don't know how to use a specific utility, you can either search Google for how to use it, or take <command> --help or <command> -h, sometimes just <command>. Example: apt-get --help

For some help beginning with the CLI...
[http://www.computerworld.com/s/article/9030259/Linux_Command_Line_Cheat_Sheet?pageNumber=1](http://www.computerworld.com/s/article/9030259/Linux_Command_Line_Cheat_Sheet?pageNumber=1)

And for some more advanced BASH (BASH is the most common command line shell used) specific commands...
[http://www.hypexr.org/bash_tutorial.php](http://www.hypexr.org/bash_tutorial.php)

Understanding how Linux specifically works takes time, but in due time you will become more familiar and comfortable with it. It's worth the effort to try understanding it, and it pays off! Just keep up at it! :)

---

### Post by jamesisin on 2010-05-22
If you are setting up a new system I would recommend going through this excellent setup post for media:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

You will get some excellent practice at running installations from the command line.  You can simply copy and paste the commands from the post, but at the same time you can inspect them to see what you are doing.  Also, it will help you get your system ready for all kinds of media support (including Flash).

---

### Post by v1ad on 2010-05-22
you can search from command line also.

sudo apt-cache search flash

---

### Post by ankspo71 on 2010-05-22
Here is a very resourceful link:
"How to install anything in Uubntu" (includes tips for commands)
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)
Hope this helps.

---

