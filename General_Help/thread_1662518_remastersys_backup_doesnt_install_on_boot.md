---
title: "remastersys backup doesnt install on boot"
date: 2011-01-08
forum: General Help
---

### Post by kanishkdudeja on 2011-01-08
i made a custom live cd of my system using remastersys backup..

but when i try to install it in any system using the install option..

it still starts the live session..

any problems as to why this is happening ?

---

### Post by mike555 on 2011-01-08
There is something you needed to install before making the backup , here is my notes 


remastersys restore - How to do it?
Finally I discovered simple solution. You mast have ubiquity and ubiquity-frontend-gtk or ubiquity-frontend-kde installed, depending on your desktop environment. When you boot from remastersys backup dvd it really doesn't matter whether you chose install or run as LiveCd because both these options works the same. That is a bug of the install option of remastersys, I suppose . Anyway, after you run it go to menu -> administration (or wherever you have it) and chose install (I have Install linux mint). It is the installer that you already know from installation livecd. It allows you to install your backup the same way as a clean liveCd.
-----------------------------------------------------
( [SOLVED] remastersys restore - How to do it? - Ubuntu Forums )
( Tue 03 Aug 2010 08:47:48 AM EST )
( [http://ubuntuforums.org/showthread.php?t=1518235](http://ubuntuforums.org/showthread.php?t=1518235) )

---

### Post by kanishkdudeja on 2011-01-08
okay..so now do i install the software from the live session itself ?

---

### Post by mike555 on 2011-01-08
You can try installing it to the live session , I haven't tried that............... but of course it will be gone after reboot, so if it installs ,then try installing to HD ...

best to install before making remix/backup.

---

### Post by kanishkdudeja on 2011-01-09
well..when i try to install it in live session..it says already installed.

---

### Post by kanishkdudeja on 2011-01-09
when i boot into the live session..

there is no option of install in administration..

and there is icon of install on the desktop either..

---

### Post by mike555 on 2011-01-09
I reread your first post , I'm not sure what your trying to do ......... remastersys makes a live cd, so you can install a custum version of linux, so it must be started as a live cd ,then installed , just like the Ubuntu cd can ,  not added to an already installed version........


 perhaps I miss read your post ?

What version do you have ? the latest is here;
[http://sourceforge.net/projects/remastersys/files/remastersys-ubuntu-karmic-lucid/](http://sourceforge.net/projects/remastersys/files/remastersys-ubuntu-karmic-lucid/)

---

### Post by kanishkdudeja on 2011-01-09
well..

see my ubuntu crashed because of updating to natty narhwal..

i had a custom ubuntu cd made if in case something went bad..

now when i boot that cd..

n i select install option..

it still starts the live session..

when i try to install ubiquity or ubiquity-frontend-gtk from the live session..

it says its already the latest version..

now how do i install ubuntu from the cd ?

there is no option of install anywhere after booting into the live session.

i mean when we run a normal ubuntu live cd..

even after booting into the live session..

der is an option on the desktop to install it..

but no such option appears in the live session of this ubuntu cd..

---

### Post by mike555 on 2011-01-09
ok, I booted into my Maverick partition, installed ubiquity-frontend-gtk , installed Remastersys (from sourceforge site - version 2.0.17.1) , made iso , burned iso, restarted the computer to the dvd and I got a sign in screen that wouldn't take my username or password .... weird ........ so I need to research it more to advise you .... sorry  .. I'll mess with it ,but might take a while ..

ok, now I remember ... the username is " custom ", with a blank password ... then it starts and I have an icon on the desktop to install .......

so bottom line is to install ubiquity-frontend-gtk into your original install, then the latest version of remastersys , then make remaster..

---

### Post by kanishkdudeja on 2011-01-09
okay..thanks mate..:)

btw, now i have reinstalled ubuntu 10.10..from the original cd only...

will have to install all the packages again..:(

---

### Post by wildmanne39 on 2013-02-09
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

