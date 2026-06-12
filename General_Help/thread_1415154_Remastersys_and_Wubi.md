---
title: "Remastersys and Wubi"
date: 2010-02-24
forum: General Help
---

### Post by iceage2609 on 2010-02-24
Hi there,i am a newbie but i am really starting to like linux and especially ubuntu.I want to ask two questions.Please your precious help.

1) I  have made a complete backup with the remastersys tool and burn the ISO file in a dvd,which worked fine in virtualbox as bootable.
Now,i want to format my disk,then use the official Desktop live CD 9.10.which i've downloaded from ubuntu site and do the installation.
Then download from synaptic and install remastersys tool,and use Restore function browsing my custom.iso as the backup.
Will that work?Is ti going to bring my OS to the previous situation before format?

2) I have read that wubi dont work with custom.iso or actually it does but i think its too complicated for me to make it happen.
So,i am thinking of formating my disk,installing windows and then through wubi, download and install from the net automatically the karmic coala 9.10 release.Then boot from ubuntu and do the same.Install remastersys,restore and browse my custom backup.iso.
Will that work?Are there any informations included about the bootloader (i am using Grub menu now) in it that will make a conflict with those of wubi?

Thank you very much,sorry for my english

---

### Post by Yogotiss on 2010-02-25
> **iceage2609 said:**
> Hi there,i am a newbie but i am really starting to like linux and especially ubuntu.I want to ask two questions.Please your precious help.

1) I  have made a complete backup with the remastersys tool and burn the ISO file in a dvd,which worked fine in virtualbox as bootable.
Now,i want to format my disk,then use the official Desktop live CD 9.10.which i've downloaded from ubuntu site and do the installation.
Then download from synaptic and install remastersys tool,and use Restore function browsing my custom.iso as the backup.
Will that work?Is ti going to bring my OS to the previous situation before format?

2) I have read that wubi dont work with custom.iso or actually it does but i think its too complicated for me to make it happen.
So,i am thinking of formating my disk,installing windows and then through wubi, download and install from the net automatically the karmic coala 9.10 release.Then boot from ubuntu and do the same.Install remastersys,restore and browse my custom backup.iso.
Will that work?Are there any informations included about the bootloader (i am using Grub menu now) in it that will make a conflict with those of wubi?

Thank you very much,sorry for my english

I feel that finding this post is funny because just a few minutes ago I was thinking the same thing as far as using WUBI with a custom.iso. I make custom Ubuntu images for people and it really would be nice to implement a WUBI install for them and myself for pleasure. I am going to research this some more and try to keep you posted if I find anything that actually works.

---

### Post by Yogotiss on 2010-02-27
From what I've been researching these past couple of days;  you can use UCK to create a [COLOR="Red"]W[/COLOR]UBI install "but", [COLOR="Lime"]U[/COLOR][COLOR="Blue"]C[/COLOR][COLOR="Yellow"]K[/COLOR] will not read my custom.iso....

---

### Post by Mark Phelps on 2010-02-27
If you're experimenting with remastersys to backup/restore Wubi just to see what happens, that's up to you do do as you see fit.

But if you're doing this because you intend to use Wubi long-term and want a way of periodically backing up and restoring your system -- you're asking for trouble.

Wubi is not intended as a long-term solution for using Ubuntu, but only as a means of trying it for a while to see how well it works for you.

I've seen LOTS of posts here of folks who had a working setup and then did something simple like update Ubuntu or update MS Windows -- and suddenly, their Ubuntu install didn't work anymore.

If you intend to use Ubuntu long-term, you would be much better off moving it to its own partitions.  That will insulate you from any MS Windows related problems.

---

### Post by Yogotiss on 2010-03-01
> **Mark Phelps said:**
> If you're experimenting with remastersys to backup/restore Wubi just to see what happens, that's up to you do do as you see fit.

But if you're doing this because you intend to use Wubi long-term and want a way of periodically backing up and restoring your system -- you're asking for trouble.

Wubi is not intended as a long-term solution for using Ubuntu, but only as a means of trying it for a while to see how well it works for you.

I've seen LOTS of posts here of folks who had a working setup and then did something simple like update Ubuntu or update MS Windows -- and suddenly, their Ubuntu install didn't work anymore.

If you intend to use Ubuntu long-term, you would be much better off moving it to its own partitions.  That will insulate you from any MS Windows related problems.

Thanks for the tip, I'm actually just doing this for the fun of it. I would never use a wubi installation on my pc because I feel it is unstable. I also use Ubuntu by itself so no dual booting for me lol.

---

### Post by bemental on 2010-10-06
> **Mark Phelps said:**
> If you're experimenting with remastersys to backup/restore Wubi just to see what happens, that's up to you do do as you see fit.

But if you're doing this because you intend to use Wubi long-term and want a way of periodically backing up and restoring your system -- you're asking for trouble.

Wubi is not intended as a long-term solution for using Ubuntu, but only as a means of trying it for a while to see how well it works for you.

I've seen LOTS of posts here of folks who had a working setup and then did something simple like update Ubuntu or update MS Windows -- and suddenly, their Ubuntu install didn't work anymore.

If you intend to use Ubuntu long-term, you would be much better off moving it to its own partitions.  That will insulate you from any MS Windows related problems.

I've actually been using WUBI on a Windows install for quite some time now and haven't had a single hiccup (luckily, I suppose).

My situation doesn't allow for me to repartition the machine and I wanted a convenient way to provide security for my files while still utilizing the awesomeness that is Linux.  I am a college student who works as a lab consultant on campus (fill printer paper, change ink cartridges, push in chairs, etc) and while we have admin rights on the machines I figured WUBI would just be a much easier way to go, especially in the case I had to jump ship.

Considering I spend the majority of my work day in the cloud (Google Apps, Dropbox, etc) it works out perfectly.

---

