---
title: "from 10.10 to 11.10"
date: 2011-11-15
forum: General Help
---

### Post by monteagus on 2011-11-15
Hi I’m currently running Ubuntu 11.10 on an inspiron laptop.
 I’m asking so I don’t screw it up hehe :) .
I used to run 10.10  but one day I decided to install 11.10 (yesterday) and install it from a live cd. I have the "/" and the "home" directories in different partitions so when the installation program asked me to chose where to install it I pick manual then I proceed to install only the "/" in the partition where it used to be.And I didn’t touch the previous home partition.
(yes I didn’t choose to upgrade it the automatic way)
So now have like 2 homes one in the same directory as the "/" and the old one *the one i want to restore as my home* in anotehr aprtition.
I know there are ways to tell ubuntu to boot my previus "home".But i dont know if there is something that i need to change in my hiddent files on the previus home.

here are some screencaps if they help.maybe i need to copy something or delete duno..
thanks in advance

old home
[[IMG]http://img593.imageshack.us/img593/8915/oldone.th.png[/IMG]](http://imageshack.us/photo/my-images/593/oldone.png/)


new home(the one I don’t care about)

[[IMG]http://img210.imageshack.us/img210/9899/newhome.th.png[/IMG]](http://imageshack.us/photo/my-images/210/newhome.png/)

maybe I don’t know there an easier way to do it by reinstalling and choosing a different way in the installation.so I don’t lose any files in my previous home.

hope that it ain’t that confusing. if you need any more info ask me please. thanks

---

### Post by Bobhuber on 2011-11-15
You will be better off moving the files you need to the new installation. There are too many differences in the new operating system to use the entire Home directory from your old install. You would just be asking for trouble.

---

### Post by monteagus on 2011-11-15
I&#8217;m probably going to install some of the software I used to have, so I know which ones I can move .but there are a bunch of folders that I don&#8217;t know if I need to move them or keep the new ones.
anyone in the same situation?
maybe if I move everything I need to an external drive.them I proceed to format the partition and set it as home and move the files back.
I&#8217;m kind of new to this.

any recommendation for what and how to do it?

---

### Post by monteagus on 2011-11-16
OK so I’m buying an external drive formatting it to ext4 moving all the files I want to keep,say video images documents etc... and erasing everything of my the partition I used to have my home. then I just tell Ubuntu to make a new home in that partition.BUT I don’t know how to do that...

---

### Post by gordintoronto on 2011-11-16
In the manual install, first you tell it where to put the root (/) then you can tell it to mount such-and-such partition as /home, and make sure the "format" button is not clicked if you want to keep your files.

---

### Post by monteagus on 2011-11-17
> **gordintoronto said:**
> In the manual install, first you tell it where to put the root (/) then you can tell it to mount such-and-such partition as /home, and make sure the "format" button is not clicked if you want to keep your files.

sorry i ask but are you sure it wont delete my images and etc...? is a complete diferent partition.
does it also deletes ".name" folders ?
also do i need to go trhoug all the instalation proces or i can just (while installing) chose to write the /home in the partition i choose *** you said, whitout reinstalling the "/"

---

### Post by gordintoronto on 2011-11-17
I have followed this procedure several times without losing a single byte.

However: hard drives fail! If you don't have proper backup, you could lose everything tomorrow when you turn on your computer. This has nothing to do with your operating system, it's a hardware issue.

Make sure you have backup! If you can't do it any other way, use Ubuntu One and Dropbox.

The procedure I described is something you do at installation. I think there is a procedure which can be used to move /home later, but I have no experience with it.

---

