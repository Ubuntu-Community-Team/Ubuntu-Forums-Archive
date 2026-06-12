---
title: "Power loss during upgrade to new version"
date: 2010-04-02
forum: General Help
---

### Post by gldearman on 2010-04-02
Hi, all.

Today, I was upgrading my desktop from Jaunty to Karmic (a little behind schedule, I know).  All packages downloaded successfully, and then the computer began the process of applying all of the updates.  During this period, at some point, it lost power.  Now, of course, it won't boot.

Fortunately, I have a separate /home/ partition, and it was unmounted during the upgrade process.  So, my personal data and settings are fine.  But the OS is useless.

I'm guessing that I'm completely buggered here, and there is nothing that I can do except re-format the Ubuntu partition and clean install Karmic from an install disk.  Am I right, or is there some way that I can fix this?

Thanks!

---

### Post by Chronon on 2010-04-02
Some things to try:
1) Try booting recovery mode and choose "fix broken packages" -- if you can get this far in the boot process.

2) Boot from a Karmic LiveCD, mount your system's root partition and chroot to it.  Then run "sudo apt-get -f install" and "sudo apt-get dist-upgrade".

3) Do a fresh install of Karmic.  Make sure you manually choose the partition layout and assign your existing /home partition as the new /home and make sure not to format it.  This will definitely work and shouldn't be too troublesome.  You are also more likely to end up with a properly configured system when doing a clean install versus upgrading.  (Though, I have had pretty good success with upgrading, personally.)

---

### Post by gldearman on 2010-04-02
As far as #1 - I cannot get that far in the boot proccess.

I'll give #2 a try.  Probably you're right, though; a clean install is going to be the most painless thing.  Only, really, a handful of issues. Like making sure that everything in the home directory ends up being assigned to the proper owner, since I have to re-create all of my users.  And remembering what extra packages I chose to install (only one program that I remember was built from source).  And re-installing all of the extra fonts that I installed manually (most of which, fortunately, I backed up to my home directory). And re-enabling restricted formats and DVD play. And re-configuring my video card, a process that Ubuntu has yet to make seamless or even painless.

Still, could be a lot worse.

Thanks.

---

### Post by Chronon on 2010-04-02
It should be pretty painless to install from scratch.  Many programs will create hidden folders in the user's home folder.  These folders can give a good idea of applications you had installed in the previous installation.  I don't think you have to worry about recreating the user accounts.  I believe that these should carry over since you're retaining the /home partition.

---

