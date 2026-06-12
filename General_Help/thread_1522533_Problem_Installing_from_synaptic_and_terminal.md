---
title: "Problem Installing from synaptic and terminal"
date: 2010-07-02
forum: General Help
---

### Post by The_Pheonix_Project on 2010-07-02
I tried installing some different things this morning in an attempt to get my sound working but every time I use synaptic, installation fails and I get this message:

E: linux-image-2.6.31-22-386: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.31-22-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-image: dependency problems - leaving unconfigured

ANY HELP?

---

### Post by warfacegod on 2010-07-02
Try this. Open Synaptic and click Custom Filters section and highlight Broken. If there are any, fix them.

---

### Post by nothingspecial on 2010-07-02
Try```
 sudo apt-get install -f
```

There seems to be a problem installing a new kernel, try and remove it if you can.

---

### Post by The_Pheonix_Project on 2010-07-02
> **warfacegod said:**
> Try this. Open Synaptic and click Custom Filters section and highlight Broken. If there are any, fix them.

Did this and no packages were listed as broken...how would I uninstall the new kernel and how do I know which one to uninstall?

---

### Post by nothingspecial on 2010-07-02
Hang on, I can see about 3 other users on the forum with this problem. Instead of using my guess work, see if you can find an official (or working) fix.

I got to go and get the kids from school, I`ll check back later.

---

### Post by The_Pheonix_Project on 2010-07-03
I'm still not finding any answers and reallyneed some help- I tried dpkg-a, apt-get install -f, tried booting into recovery mode and fixing broken but this didn'twork... someone HELP?

---

### Post by wojox on 2010-07-03
Go to:

```
cd /var/cache/apt/archives
```

```
sudo dpkg -i linux-image-2.6.31-22-generic
```

---

### Post by The_Pheonix_Project on 2010-07-04
```
guest@Admin:~$ cd /var/cache/apt/archives
guest@Admin:/var/cache/apt/archives$ sudo dpkg -i linux-image-2.6.31-22-generic
[sudo] password for guest: 
dpkg: error processing linux-image-2.6.31-22-generic (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.31-22-generic
guest@Admin:/var/cache/apt/archives$ 



```
I tried thaat buddy-still no help...thank you all for helping me though and I welcome any more advice...I also tried booting into an alternate kernel that was already installed when I did the network upgrade-2.6.31.17 I think-because with the kernel unconfigured it will not allow apt or synaptic to install anything and anyways the alternate kernel ended up running in low graphics mode...also I tried installing a new kernel-no good...

---

### Post by warfacegod on 2010-07-04
Try one of these:

```
sudo dpkg --configure -a
```

```
sudo dpkg --force all --remove
```

---

### Post by The_Pheonix_Project on 2010-07-04
[CODE][guest@Admin:~$ sudo dpkg --force all --remove
dpkg: --remove needs at least one package name argument
/CODE]

That is that and as far as using dpkg --configure -a I have showed the output of that in the preceding posts...

---

### Post by warfacegod on 2010-07-04
> **The_Pheonix_Project said:**
> [CODE][guest@Admin:~$ sudo dpkg --force all --remove
dpkg: --remove needs at least one package name argument
/CODE]

That is that and as far as using dpkg --configure -a I have showed the output of that in the preceding posts...

Must have missed that, sorry.

I'm noticing that you are logged in as guest@Admin. Is guest your actual username or are you actually logged in as a guest. I'm fairly certain that the guest account doesn't have the proper permissions to fix this.

---

### Post by The_Pheonix_Project on 2010-07-04
no-my guest account does-I gave it administrative priviledges because my normal user account crashed gnome and will no longer work-that was under Intrepid...so I gave guest admin priviledges via the root account...

---

### Post by philinux on 2010-07-04
What does post #9 first command spit out?

---

### Post by The_Pheonix_Project on 2010-07-04
guest@Admin:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.31-22-386 (2.6.31-22.60) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-22-386
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.31-22-386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-22-generic (2.6.31-22.60) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-22-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.31-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-22-generic; however:
  Package linux-image-2.6.31-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-alsa-2.6.31-22-generic:
 linux-backports-modules-alsa-2.6.31-22-generic depends on linux-image-2.6.31-22-generic; however:
  Package linux-image-2.6.31-22-generic is not configured yet.
dpkg: error processing linux-backports-modules-alsa-2.6.31-22-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.22.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.31.22.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-alsa-karmic-generic:
 linux-backports-modules-alsa-karmic-generic depends on linux-backports-modules-alsa-2.6.31-22-generic; however:
  Package linux-backports-modules-alsa-2.6.31-22-generic is not configured yet.
dpkg: error processing linux-backports-modules-alsa-karmic-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-22-386
 linux-image-2.6.31-22-generic
 linux-image-generic
 linux-backports-modules-alsa-2.6.31-22-generic
 linux-generic
 linux-image
 linux-backports-modules-alsa-karmic-generic
guest@Admin:~$ 


That's what happens every time!

---

### Post by warfacegod on 2010-07-04
So... Your Primary User Account is broken. You're having major issues with a failed kernel update, presumably through the Guest Account that has Admin. privileges (From a security standpoint, I would question the validity of doing this but I just don't know). And you are having sound issues that appear to have led you into the situation you are in now.

Have you considered backing up your Home Folder and doing a fresh install?

---

### Post by The_Pheonix_Project on 2010-07-04
Looks like I'm not going to have a choice...Is there a way that I can save some of my documents/music files when doing a fresh install?

---

### Post by dino99 on 2010-07-04
when things goes wrong its time to check & clean the system:

- is sources.list clean (synaptic repo): only genuine ubuntu repo from main server (deactivate all other repo such as third party & ppa if any, and of course no mixed distro or releases)

- clean the system: 
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo update
sudo apt-get install -f
sudo dpkg --configure -a

sudo shutdown -r now
(force a fsck on next reboot)

---

### Post by warfacegod on 2010-07-04
Looking at that output, I *think* it means that the update-grub command is missing from your system.

If that is the case then Section #13 should help: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by The_Pheonix_Project on 2010-07-04
Also I don't have CD's to burn an image right now and may not have the $ for a while!  I'm almost afraid to go to 10.04 if I am already having thee kinds of problems with Karmic-I have a really high end computer that Linux doesn't seem to write drivers for historically, I have had to do a lot to get everything on line and working and then like with Backtrack 2 and 3 my CRT monitor wouldn't even work because the refresh rate was off giving me a "Frequency out of Range" error-I am always afraid with this old Compaq MV720 that this will happen with Ubuntu so I only upgrade from a working system when I absolutely have to...

---

### Post by warfacegod on 2010-07-04
I'm not suggesting you go with Lucid. By all means don't if you're not comfortable with it. But if we can't get you fixed up you may have no choice but to do a Fresh Install, whatever version you decide to go with. I'm *not* trying to force this upon you but I do think you need to be prepared for the possibility.

---

### Post by The_Pheonix_Project on 2010-07-04
I am prepared for the possibility but I would really like to try and fix this first!  I really need to fix my regular user account...it's saying there is some error with gconf and so the gnome desktop is crashing but then I also have several different WM's and it won't load up the account under any of them either!  Right now my first concern is this unconfigured kernel...

---

### Post by warfacegod on 2010-07-04
Figured out why I missed the output of ```
sudo dpkg --configure -a
```

You posted it in your other Thread, [http://ubuntuforums.org/showthread.php?p=9535772#post9535772](http://ubuntuforums.org/showthread.php?p=9535772#post9535772), not this one.

Double threads. Naughty, naughty.:P

Have you tried reinstalling GRUB2 yet?

---

### Post by The_Pheonix_Project on 2010-07-06
no but I will right now!

---

### Post by The_Pheonix_Project on 2010-07-06
That did it!  Problem solved-now all I have to do is figure out how to get sound working!

---

### Post by warfacegod on 2010-07-06
Victory! Post a link to your sound problem thread.

---

### Post by The_Pheonix_Project on 2010-07-06
Wha do you mean?  I am still without sound but haven't started a thread yet

---

### Post by warfacegod on 2010-07-06
> **The_Pheonix_Project said:**
> Wha do you mean?  I am still without sound but haven't started a thread yet

Then start one!:biggrin:

---

### Post by The_Pheonix_Project on 2010-07-06
Here you go!!!  **[http://ubuntuforums.org/showthread.php?p=9556938#post9556938](http://ubuntuforums.org/showthread.php?p=9556938#post9556938)**

And Thanks again for your patience and help!

---

