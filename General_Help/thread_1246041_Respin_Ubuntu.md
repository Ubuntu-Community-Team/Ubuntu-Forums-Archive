---
title: "Respin Ubuntu"
date: 2009-08-21
forum: General Help
---

### Post by kdroxx on 2009-08-21
Hello, I've been using Ubuntu for a week & would like to switch to it completely.
I need to completely fomat my PC.
Does respinning installed Ubuntu include installed apps?
Is there any other way to import all apps?

---

### Post by kiridude on 2009-08-21
Please clarify what you mean by this:

> Does respinning installed Ubuntu include installed apps?

You can reformat your drive with the Ubuntu live CD. All default applications are also included on the CD.

---

### Post by P4man on 2009-08-21
no, if you do a reinstall, you will lose all your apps. But why reinstall? If you want to change your partitioning, boot from the live cd and grow / shrink / rearrange without wiping the ubuntu install. You may need to reconfigure grub after that (especially if you delete partitions left of ubuntu) but other than that you should be fine.

If you do want to export a list of apps currently installed, you can use this:

[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by kdroxx on 2009-08-21
My HDD currently has WinXP & Win7 installed on it.
+ I also need to install the same OS on another PC.
I've read a guide on respinning Ubuntu, but it doesn't mention if apps installed on the system will be bundled in the new OS.
Installing the apps all over again isn't possible as I'm currently using dial-up connection.

---

### Post by P4man on 2009-08-21
what do you mean by respinning? What tutorial are you looking at?
If you mean remastering with an app like remastersys, then yes, your apps will be included.

---

### Post by kdroxx on 2009-08-21
Yes, the tut is based on Remastersys, it's featured in Digit(India) this month.
Anyway, thanks for the help.

---

### Post by mdmarmer on 2009-08-21
Avoid a reinstall if you can -- gparted can delete partitions and grow your install so that it takes up the whole disk.

If you use Remastersys, Back up your data!

And be careful with Remastersys -- it's a great program but  simplified --

If you specify a separate home partition, it will format that partition as well -- it's intended mainly for a new install

If you already have a separate home partition, don't specify that when you install from your remaster -- add it later.

Take a look at the wiki and the forum
 [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Mike

---

### Post by Twittery on 2009-08-21
Whatever you do make sure that you backup your apps because it maybe likely that you lose your data

---

