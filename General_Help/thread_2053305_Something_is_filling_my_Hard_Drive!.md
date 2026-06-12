---
title: "Something is filling my Hard Drive!"
date: 2012-09-05
forum: General Help
---

### Post by brsmits on 2012-09-05
Disk Usage Analyzer says my HDD had 445.8 GB used.  5 Min later, it was about a Gig higher.  This has been happening for the past few days.  I'm trying to find out what program is doing this but all my searches either come up with no useful information or results that I don't know how to interpret.  I don't think a failing HDD would do this.  Any suggestions?

---

### Post by brsmits on 2012-09-05
Just verified, it's only happening on my /home partition.

---

### Post by mcduck on 2012-09-05
First things to look would be any backup service you are using (or have used in past, or have tried to get working in the past :D), and system logs located in /var/log.

In case some log file is growing extrememly large and filling your disk, please don't remove log but instead read through it to find out what is causing the error messages (as the large log would only be a symptom of the problem, and only fixing the actual issue causing the error messages will provide a permanent solution).

Anyway, the Disc Usage Analyzer should give you a fair idea what directories are taking a lot of space, and the "du" tool in command line should also be helpful.

---

### Post by houseworkshy on 2012-09-05
Knowing whether this happens when offline, actually turn the router/modem off, would help to shorten the list of possible causes.  As would the name of the file.  If you look at the /home, including hidden files, a couple of times in list view you will be able to see what is getting bigger.  It won't be long, at 1g every five minets,  before the monster is top of the list.

If you are ok with the command line this suggests another way of finding it  [https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

---

### Post by 2F4U on 2012-09-05
In your home directory, the file .xsession-errors comes to my mind first. It is a log file for the desktop environment.

---

### Post by brsmits on 2012-09-05
Update: I did a search for all files being modified by date, and it came up with nothing useful.  I found the .xsession-errors files a deleted them, they were about 20 Gb each.  After that my space was still shrinking.  

I unplugged the Ethernet, restarted my computer and got all my space back. (YAY!)  I waited for about 10 min, checking if the space was going to shrink again.  It did not.  Plugged the ethernet back in, it's been sitting idle for about 10 min now, and no shrinking space.  The only program/file change that I did was delete the .xsession-errors files.

Aha!  So, I actually caught the bugger in the act.  It's the .xsession-errors file that is growing really quick.  I made a copy and checked what was happening.  I get the line 

```
(nautilus:1813): GLib-GObject-CRITICAL **: g_value_get_object: assertion 'G_Value_Holds_Object (value{' failed
```

---

### Post by ramsharan065 on 2012-09-05
This means you have solved your probem by deleting .xsession-errors file.

---

### Post by mcduck on 2012-09-05
> **ramsharan065 said:**
> This means you have solved your probem by deleting .xsession-errors file.

deleting a log file is never a solution to a problem, it's just removing all the clues that would help to figure out what the real problem is... ;)

edit: based on the errors, it might be related to some Nautilus extension you have installed. There's an existing bug report, and also some people have suggested that removing/reinstalling nautilus-open-terminal or ubuntuone-client-gnome might help:

[http://askubuntu.com/questions/66993/nautilus-keeps-force-closing]("http://askubuntu.com/questions/66993/nautilus-keeps-force-closing")
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/738203]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/738203")

---

### Post by vasa1 on 2012-09-05
> **ramsharan065 said:**
> This means you have solved your probem by deleting .xsession-errors file.

It most certainly doesn't mean that.

---

### Post by brsmits on 2012-09-05
> **ramsharan065 said:**
> This means you have solved your probem by deleting .xsession-errors file.

Somewhat.  It's still popping up and filling up rapidly, but I at least know what file is filling up.  Now the question becomes, what the hell is causing it?  Google is not helping.

---

### Post by Elfy on 2012-09-05
me too this bug - [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1006675](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1006675)

this might help as well - [http://askubuntu.com/questions/93718/how-do-i-prevent-xsession-errors-from-eating-disk-space](http://askubuntu.com/questions/93718/how-do-i-prevent-xsession-errors-from-eating-disk-space)

---

### Post by houseworkshy on 2012-09-05
Now you know the name of the file go hunting for the process.   System monitor is good for that, left clicking on a process opens a menu, in that menu is "open files".  
You *may* need to open the system monitor from the command line with a "sudo" in front of it in order to get full privalages, so you can see everything.  Depending on what it is you may not need to. 
In 10.04 the command line is "sudo gnome-system-monitor" in 12.04 it may be 'unity-system-monitor' but that is only guessing as I'm not using Unity.   If my guess is wrong you can find out the correct name for it via the help from system monitor itself.  Also remember that it is a log file so read it, I expect you will find the same error repeated many times a second.

---

### Post by vasa1 on 2012-09-05
> **Elfy said:**
> me too this bug - [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1006675](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1006675)

this might help as well - [http://askubuntu.com/questions/93718/how-do-i-prevent-xsession-errors-from-eating-disk-space](http://askubuntu.com/questions/93718/how-do-i-prevent-xsession-errors-from-eating-disk-space)

The bug seems slightly different and the poster of the askubuntu question seems to have other problems as well. Some stuff seems to have been removed as well.

---

### Post by fayazvalachil on 2012-09-06
I am also had same problem,it was  	 		[B]"gnash-dbg.log" get filling on home directory.  can anyone help me to find out what will be main cause of this error.after Uninstalled back-up software and deleted this file restarted my system, the problem still exist.
[/B]

---

### Post by mcduck on 2012-09-06
> **fayazvalachil said:**
> I am also had same problem,it was  	 		[B]"gnash-dbg.log" get filling on home directory.  can anyone help me to find out what will be main cause of this error.after Uninstalled back-up software and deleted this file restarted my system, the problem still exist.
[/B]

No, actually you have a different problem, since it's a different log file and specific to a certain program (different one than what's causing the OP's problems).

I recommend starting a new thread of your own (remeber to mention Gnash in the thread title), and posting some of the contents of that log file there so people have something to work with. That's why the log files exist, to provide useful information when something isn't working like it should... :)

---

