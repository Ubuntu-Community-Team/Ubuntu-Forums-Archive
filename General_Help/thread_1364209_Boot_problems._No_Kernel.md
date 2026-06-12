---
title: "Boot problems. No Kernel"
date: 2009-12-25
forum: General Help
---

### Post by jimbo3 on 2009-12-25
Hi All, I have been using Ubuntu 9.10 dual boot for a few weeks now and after installing some upgrades it now fails to boot up. I get to a prompt which says Grub and after trying various things I am told that there is no Kernel installed. I would reinstall the system but I have files which I don't want to loose. Could anyone point me in the right direction as I am not in the least a Techie.

---

### Post by gsmanners on 2009-12-25
If you have an external storage device, you could simply boot the live (desktop) CD and use that to make backups of your data. Then you could reinstall without too much to worry about.

---

### Post by ic2 on 2009-12-25
I have not done anything with ubuntu yet but I think it a good idea to have extra Linux partitions and now I plan to use one of those partitions I created on my hard drive and call it Home_Home or something and mount it when needed or I call it Home_Backup_1.  Because of your experience, from now on end I will only use ubuntu partition to install the OS/update/experiments/etc, and I will never save none of my important work inside that partition ...

I'll mount Home_Home and save it there.  So if something ever go wrong with any of my Linux install or upgrades, Home_Home will NEVER be touch, especially if that partition is formatted in an entirely difference Linux filesystem that is not the same as the others.  This is very important.  You'll never loss your data again unless the entire HDD burn-out.

I wish I knew why or someone else could explain this "Boot problems. No Kernel" but all I can do is suggest an idea for  future avoidance and that is no fun because we never learn nothing technical wise.  It only get passed to the next newbee.  No real answer, just a work around as possible bugs pile-up in the OS.  

Just a thoughts

Good luck


see last part for general idea:
[http://ubuntuforums.org/showthread.php?t=1363864](http://ubuntuforums.org/showthread.php?t=1363864)

---

### Post by ranch hand on 2009-12-25
The first thing I would like you to do is to run this script;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

and post the results here.

You can run it from your Live CD.  While you are there you should take a look at your files on the HDD and see if they are all there.

Gparted is on the LiveCD and you can create another partition, if needed to back up your data.

I suspect that this is not the problem though.  I am thinking that your grub on the MBR has, somehow, become corrupted and needs restored.  This can be fixed.

We need to see your boot info first.  Run the script and we will go on from there.

An important thing to remember in situations like this is to remember to breath, don't do anything rash.

---

### Post by jimbo3 on 2009-12-27
Thanks for all the advice. After trying various things with no success I decided to sacrifice my data and reinstall. Sorry if I wasted your time.

---

