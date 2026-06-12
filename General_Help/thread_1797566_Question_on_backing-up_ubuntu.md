---
title: "Question on backing-up ubuntu"
date: 2011-07-05
forum: General Help
---

### Post by aoniumo on 2011-07-05
There seems to be a lot of back-up software in the software center.  I would like to back-up my entire hard drive where ubuntu 11.04 is installed including all partitions, software installed, cache, boot files, etc.  The reason I'm doing this is because I am planning to get a faster hard drive and would like to move everything into the new hard drive without having to go through the re-installation process of everything.

I find re-installation a hassle since my log-in, credit card accounts would need to send me verification before I can access my account.  Re-installation of an OS and all software and drivers also takes a long time.

Any recommendation on a "perfect" back-up software that could do the above is appreciated.

Edit: I did search around and found various help sites, but I've only been using ubuntu since 11.04 came out and after having figured a lot of things to make it work perfectly, it is now my only OS installed.  I would like the opinions of users here who have done back-ups.

---

### Post by in-dust-rial on 2011-07-05
hi there,

well the best i can think of is using the 'dd' command.
[http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm)

however, it is not a GUI tool.
but its really handsome, if you ever used a similar tool.
you can just copy everything one-by-one in one command.


but I would go for a reinstall anyways to prevent future problems.

backup /HOME /ETC and the installed packages.
in home all media and personal configurations and also personal data is stored. 
in etc most of the system configurations you might have changed by yourself are saved.
you can save the installed packages as a list:
[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)
or save all installed packages directly:
[http://www.ubuntugeek.com/backup-installed-packages-on-ubuntu.html](http://www.ubuntugeek.com/backup-installed-packages-on-ubuntu.html)

when you install your new linux, restore the HOME folder on a distinct partition and load it via the FSTAB.
then you can reinstall packages and maybe resore some files from the etc folder you backed-up.

no, while your home is save on another partition, reinstall linux base system will not touch you personal files (and your personal settings are also there.)
(just never format that home-partition during install :P)

good luck!

---

### Post by aoniumo on 2011-07-05
> **in-dust-rial said:**
> hi there,

well the best i can think of is using the 'dd' command.
[http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm)

however, it is not a GUI tool.
but its really handsome, if you ever used a similar tool.
you can just copy everything one-by-one in one command.


but I would go for a reinstall anyways to prevent future problems.

backup /HOME /ETC and the installed packages.
in home all media and personal configurations and also personal data is stored. 
in etc most of the system configurations you might have changed by yourself are saved.
you can save the installed packages as a list:
[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)
or save all installed packages directly:
[http://www.ubuntugeek.com/backup-installed-packages-on-ubuntu.html](http://www.ubuntugeek.com/backup-installed-packages-on-ubuntu.html)

when you install your new linux, restore the HOME folder on a distinct partition and load it via the FSTAB.
then you can reinstall packages and maybe resore some files from the etc folder you backed-up.

no, while your home is save on another partition, reinstall linux base system will not touch you personal files (and your personal settings are also there.)
(just never format that home-partition during install :P)

good luck!


Thanks, in-dust-rial.  I will review the documents on the links.  One of the links on backing-up installed packages seem to be for packages installed using synaptic.  I have never used synaptic since I don't know how.  I just go to the software center and find software there.  I'd still prefer a GUI back-up since I am not that good with command line.  This is the reason I've never touched Linux since seven years ago because way back then, most were command line.

---

### Post by nzjethro on 2011-07-05
I used [this guide]("http://ubuntuforums.org/showthread.php?t=35087") to back up my entire system (packages, files, boot info etc), and found it very simple to use (haven't had to use my backup yet, so I can't vouch for that, but there's a lot of good cred on the thread).

Alternatively, Clonezilla can clone your entire drive (all partitions) which will mean you can essentially copy your entire drive to your faster HDD.

---

### Post by Ghost_Mazal on 2011-07-05
Defnitely look into clonezilla. In this case making an image of your drive is gonna be the easiest and fastest and clonezilla is very good at that.

---

### Post by aoniumo on 2011-07-05
Does clonezilla back-up to a internal, external, or network drive?  I don't have a network drive.  It doesn't seem to be in the software center.  I'm very new to ubuntu (only since natty) so I have no idea how to install it via command lines.

I also found more information for clonezilla at: [http://clonezilla.org/](http://clonezilla.org/)

One of the limitations "The destination partition must be equal or larger than the source one."
My ubuntu installation drive is 2 terrabyte drive in a single partition, but I'm only using about 300 gigabytes.  This would mean that I would have to have a 2 terrabyte partition or drive to back it up to even though I'm only backing up 300 gigabytes.  That's not an option.

---

### Post by Ghost_Mazal on 2011-07-05
> **aoniumo said:**
> Does clonezilla back-up to a internal, external, or network drive?  I don't have a network drive.  It doesn't seem to be in the software center.  I'm very new to ubuntu (only since natty) so I have no idea how to install it via command lines.

It's a live boot cd that you boot with. And it clones to any of the above.

You need to dl the .iso. Burn it. And then you boot with it to image your drive to external hdd or 2nd internal hdd.

---

### Post by egalvan on 2011-07-05
the clonezilla website

[http://clonezilla.org/](http://clonezilla.org/)


A mini-distro I have used for all my HD-based partition/clone/etc 
PartedMagic LivdCD
[http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

---

### Post by aoniumo on 2011-07-05
> **Ghost_Mazal said:**
> It's a live boot cd that you boot with. And it clones to any of the above.

You need to dl the .iso. Burn it. And then you boot with it to image your drive to external hdd or 2nd internal hdd.

I don't have a hard drive that's reserved only for back-ups.  I have my installation drive (where ubuntu is now, 2 terrabytes), another internal drive (2terrabytes), but this drive has dvd files, pictures, docs in it, and an external drive which is only 1 gigabyte with dvd files, pictures, and docs in it.  Does clonezilla require a drive/partition solely for back-ups?  I don't want the files getting erased in the drive when I use it as a back-up drive.  Also, the limitation, "The destination partition must be equal or larger than the source one."

---

### Post by egalvan on 2011-07-05
> **aoniumo said:**
> **I don't have a hard drive that's reserved only for back-ups**.  I have my installation drive (where ubuntu is now), another internal drive (2terrabytes), but this drive has dvd files, pictures, docs in it, and an external drive which is only 1 gigabyte with dvd files, pictures, and docs in it.  Does clonezilla require a drive/partition solely for back-ups?  I don't want the files getting erased in the drive when I use it as a back-up drive.

> ...**I am planning to get a faster hard drive** and would like to move everything into the new hard drive

When you get that "faster hard drive", use it as the target drive.

And no, clonezilla does not require a dedicated drive/partition...
you can choose a "file" as the destination.

---

### Post by egalvan on 2011-07-05
> **aoniumo said:**
> 

Any recommendation on a **[COLOR="Red"]"perfect" [/COLOR]**back-up software that could do the above is appreciated.


Oops, how did I miss that?
All software is a matter of compromises between cost, size, functions, features, etc...

But then again, if you had a Bill Gates bank account and Linus Torvalds coding skills.... :KS

---

### Post by aoniumo on 2011-07-05
> **egalvan said:**
> When you get that "faster hard drive", use it as the target drive.

And no, clonezilla does not require a dedicated drive/partition...
you can choose a "file" as the destination.

I thought of that.  Once I get the new drive and use it as the target, can I boot from that drive?  How would I unpack the back-up into the same drive where the back-up is?  Wouldn't that overwrite the back-up and drive?

I'm still reading the info at clonezilla.org.

---

### Post by aoniumo on 2011-07-05
Never mind.  Reading those guides give me a headache.  I'll buy the drive from Amazon and just do a fresh install of everything.

---

### Post by in-dust-rial on 2011-07-05
dont forget to put /home onto a seperate parition.

SHOULD BE FOCKIN RECOMMENDED BY THE INSTALLER :D

---

