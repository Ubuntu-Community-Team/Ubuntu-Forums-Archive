---
title: "reinstalling ubuntu"
date: 2010-05-04
forum: General Help
---

### Post by dbowlin17 on 2010-05-04
When I reinstall, will I have to worry about the file permissions that are associated to the files I have created currently? i just have stupid issues where it won't recognize cds or usb devices and i wanna do a clean 10.04 install...

---

### Post by ratcheer on 2010-05-04
No, everything you had before will be gone.

Tim

---

### Post by spydeyrch on 2010-05-04
If you have any personal files, I would back those up, as doing a clean install will format/wipe your HDD clean and so nothing will remain.

-Spydey :KS

---

### Post by cuberts on 2010-05-04
> **dbowlin17 said:**
> When I reinstall, will I have to worry about the file permissions that are associated to the files I have created currently? i just have stupid issues where it won't recognize cds or usb devices and i wanna do a clean 10.04 install...If you do a clean install, which you should do, then all of the files will be gone. But if you actually share the files with a separate harddrive and then get those back after that then it might now be all gone.

---

### Post by dbowlin17 on 2010-05-04
I have backed up using "Back in Time" and have all my files on an external hd. i plan to reformat the whole drive and do a clean 10.04 install.

---

### Post by QIII on 2010-05-04
Do you have a separate /home partition?

---

### Post by dbowlin17 on 2010-05-04
i don't know. i have a ext4 and a swap

---

### Post by QIII on 2010-05-05
Ah.  For future reference, reinstalling/fresh installing a new version is much easier if you have a separate /home partition.  That way, when you do your partitioning, you can choose not to reformat /home (but always ALWAYS back it up anyway) and, if all goes well, you don't need to restore all your important files.  (But you have them backed up just in case!)

So...

I would recommend this (after you wait for a few others to join the fray and suggest anything I've forgotten):

1)  Create a list of installed applications by running the following in the terminal

```
sudo apt-get install dselect
``````
sudo dpkg --get-selections > selections.txt
```That puts a list of what you have installed into /home.  We'll talk about how to reinstall them later.

I like to copy my /etc/hosts file (at least) to my /home partition as well.  That way I don't have as much wrestling to do when I want to reconnect to my home network.

2)  Copy your /home folder (which should currently reside in your / partition) to an outside medium, such as where ever you did your previous back up.  MAKE SURE you hit CTRL+H to expose all of your hidden files and folders when you select everything to copy!

3)  When installing, create a / partition, a /home partition and, if you like, a /swap partition. 

Make the / partition somewhere between 10 and 30GB.  30 is probably a waste, unless you intend to install a LOT of applications.  15 might be good.  It's a matter of opinion.  Set / as the mount point.

Make your /swap partition 1.25 times your RAM, or, if you plan to upgrade, 1.25 times whatever you might like to upgrade to.  You will hear 2x RAM.  That's a waste.  You should, in theory, be able to save the RAM state in the same amount of space on the drive as the amount of RAM you have.  Unfortunately, due to disk technology and geometry, that rarely works out perfectly.  And since you really want /swap for hibernation and such, there is no reason to have much more.  Using /swap as "extra" RAM is SLOW!

Use the rest of the disk for your /home partition.

(My opinion.  Someone will be on to argue momentarily.  Always happens.)

4)  After installing, copy the entire contents of the /home folder you saved into your new /home partition.  You may have to fiddle a bit with email profiles and browser profiles, but that is pretty easy.  Post that as a new thread if you have issues.

5)  You will now want to reinstall all the applications you have installed (via apt-like programs or .debs.  Most third-party applications will have to be reinstalled.  Sorry.).

If you have Medibuntu or any other "non-standard" sources in your sources list, add them to the new list you will have after your clean installation.  If  you don't some of what you want to re-install will not work.

In the terminal again

```
sudo apt-get install dselect
``````
sudo dpkg --set-selections < selections.txt
``````
sudo apt-get update
``````
sudo apt-get dselect-upgrade
```Like I said, wait a bit for others to chime in with anything I will certainly have forgotten.  You get old, things start to slip your mind, you wander down the street in your neighborhood with only your boxers on...

---

### Post by dbowlin17 on 2010-05-05
so, i used back in time to back up all my personal data like documents and stuff. i can go ahead and reinstall on the hard drive after reformatting it right?

---

