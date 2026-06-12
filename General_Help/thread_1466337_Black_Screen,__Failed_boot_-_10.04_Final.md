---
title: "Black Screen,  Failed boot - 10.04 Final"
date: 2010-04-30
forum: General Help
---

### Post by HistoryMac on 2010-04-30
Hi all,
I'm running into a rather annoying issue with the final release of Lucid on my Toshiba Portege A100. I already had to use the alternate install disk because, I have no idea why, but the regular disk just doesn't work on this one laptop. Anyway, I went through the full installation on the alternate disk and everything was fine until the install finished and I rebooted. When I reboot, this is what happens:

1. The TOSHIBA logo screen appears.
2. The screen goes black, with a pulsing  _  in the top left hand corner.
3. Some time later, the screen momentarily flashes green (less than a second) then goes back to black screen with prompt.
4. A few seconds later, the purple ubuntu splash screen appears for 2 sec, all dots suddenly turn orange and then the screen goes back to black again - no prompt this time, and no disk activity either from here on in.

Any ideas? I'm lost... :confused:

---

### Post by NetFreeDiver on 2010-04-30
I have exact same failure with Toshiba Satellite L-10. Urgent help needed!

Edit: I found a work around?! :)  During grub boot options select previous kernel (2.6.31.21).  Cheers!

---

### Post by HistoryMac on 2010-04-30
> **NetFreeDiver said:**
> 
Edit: I found a work around?! :)  During grub boot options select previous kernel (2.6.31.21).  Cheers!

I don't have that option in GRUB, possibly because I did a clean install. How did you install 10.04, did you update? If so, from what?

---

### Post by nanog on 2010-04-30
Sounds like a graphics issue. What driver are you using?

Can you get a terminal by hitting ctrl-alt-F1? If so, the run something like sudo /etc/init.d/gdm restart  or startx and post any errors. You may also want to look at your log files in /var/log/.

---

### Post by HistoryMac on 2010-04-30
> **nanog said:**
> Sounds like a graphics issue. What driver are you using?

Can you get a terminal by hitting ctrl-alt-F1? If so, the run something like sudo /etc/init.d/gdm restart  or startx and post any errors. You may also want to look at your log files in /var/log/.

No luck with ctrl+alt+F1 (or F2). I'm not sure what driver I'm using, or what graphics chip is actually in this laptop. I only acquired it 2 days ago, but after doing a little research on the 'net I think it may have the Intel 855GM...

---

### Post by not1 on 2010-04-30
I have the same exact symptoms on a Toshiba Portege M300.

---

### Post by GuitarG on 2010-04-30
Same issue here with a Toshiba Satellite. Black screen crash while doing an update from previous version. Doing a clean boot/install results in the same scenario. I am going to try the alternate version doing a clean install.
It is acting like a video driver issue. But that is odd. I've been running Ubuntu on this notebook for the last two years, installing each new version with no issues.

---

### Post by GSF1200S on 2010-04-30
**EDIT** This is a compilation I originally posted on Page 8 of this thread to help others fix their systems with a bit of information from everyone in the thread. It explains the way that has worked for myself as well as a few people throughout this thread.

Load a liveCD or boot from another Linux OS (It MUST be the same architecture as your install [the liveCD or the Linux install you will be doing this from] or the chroot performed later will not work). You can even use a 9.10 liveCD of the same architecture if you are having problems getting the 10.04 liveCD going and you dont have another Linux install to do this from. Open a terminal and run:
> sudo fdisk -l
and determine what partition 10.04 is installed on. Then, mount that partition. Assuming your / (root) partition is /dev/sda1:
> sudo mount /dev/sda1 /mnt
Then open nautilus as root:
> gksudo nautilus /
Then, navigate to /mnt/etc/default/grub and open it. Look for the line that says:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
(or whatever it says inside the " ") and change it to:
(For nvidia)
> GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
(for intel)
> GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=0"
Save and close.

Then, chroot into the system as follows:
> sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
Then, check out dino99's suggestions (you will be able to do them assuming the liveCD is connected to the internet and you are in a chroot environment as described above):
> Some commands to check errors and repair them:

need to open a terminal:
- if you fail to boot completly (GSF1200S Edit: Or if you make it into the liveCD and chroot as described above) but can use the keyboard, (GSF1200S Edit: you dont need to press alt f2 in the live environment, just open a terminal) press ALT+F2 to call a terminal, then:

1) sudo dpkg --configure -a
2) sudo dpkg-reconfigure gdm
3) sudo dpkg-reconfigure plymouth
4) sudo apt-get update
5) sudo apt-get install -f
6) sudo apt-get install ubuntu-desktop (added by GSF1200S)

validate these commands one by one, if errors appear with 5): read and note what is missing or wrong:
a) if missing: sudo apt-get install "the missing package name"
b) if wrong: sudo dpkg-reconfigure "the wrong package name"

Hope that can help some of you (GSF1200S Edit: Make sure you are looking in the directory where you mounted the 10.04 install, NOT the ubuntu live CD location)

- if you can boot but have errors:
look at system --> admin -- log viewer for errors
and .Xsession-errors into /home/your user/.Xsession-errors ( . stand for hidden file, so into menu check "show hidden file"
Then run:
> sudo update-initramfs -u
sudo update-grub2
and then close that terminal. Open another and put in:
> sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /dev/sda1
and then restart and hopefully it will boot.

If you are appalled by the "ugly text" flying across the screen and must have a splash for your boot sequence, you can add quiet splash above (in /etc/default/grub where I told you to remove these terms above) and follow the instructions from this guide:

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by HistoryMac on 2010-04-30
[QUOTE=]
Then, navigate to /etc/default/grub and open it.
[/QUOTE]

Everything worked fine up till that point, but alas I can see no GRUB file. Thoughts?

---

### Post by GSF1200S on 2010-04-30
> **HistoryMac said:**
> Everything worked fine up till that point, but alas I can see no GRUB file. Thoughts?

Crap! I forgot to specify you need to go to the mounted partition. So, if you mounted /dev/sda1 in /mnt, you would go to:
/mnt/etc/default/grub

The live CD wouldnt have a file there because grub isnt installed. The live cd does have /etc and the other directories, but your grub config is located within the directory you mounted. Sorry for the lack of clarification.

---

### Post by HistoryMac on 2010-04-30
> **GSF1200S said:**
> Crap! I forgot to specify you need to go to the mounted partition. So, if you mounted /dev/sda1 in /mnt, you would go to:
/mnt/etc/default/grub


Hmm... Nothing at all in /mnt :confused:

---

### Post by GSF1200S on 2010-04-30
> **HistoryMac said:**
> Hmm... Nothing at all in /mnt :confused:

Where did you mount the root partition to? Is /dev/sda1 the partition you installed Linux on? Give me the printout of:
```
sudo fdisk -l
```

You need to mount whatever partition Ubuntu is installed on, and then navigate to where you mounted it with nautilus started as root user.

---

### Post by HistoryMac on 2010-04-30
> **GSF1200S said:**
> Where did you mount the root partition to? Is /dev/sda1 the partition you installed Linux on? Give me the printout of:
```
sudo fdisk -l
```

You need to mount whatever partition Ubuntu is installed on, and then navigate to where you mounted it with nautilus started as root user.

sudo fdisk - 1 gives:

```

fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK      Change partition table
       fdisk -l [-b SSZ] [-u] DISK   List partition table(s)
       fdisk -s PARTITION            Give partition size(s) in blocks
       fdisk -v                      Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

```

---

### Post by GSF1200S on 2010-04-30
> **HistoryMac said:**
> sudo fdisk - 1 gives:

```

fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK      Change partition table
       fdisk -l [-b SSZ] [-u] DISK   List partition table(s)
       fdisk -s PARTITION            Give partition size(s) in blocks
       fdisk -v                      Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

```
 Thats L not one ;)
sudo fdisk -l
NOT
sudo fdisk -1

Happens :)

---

### Post by HistoryMac on 2010-04-30
> **GSF1200S said:**
> Thats L not one ;)
sudo fdisk -l
NOT
sudo fdisk -1

Happens :)

Flip. Of course, can't believe I missed that. Thanks, will try that now and report back.

---

### Post by HistoryMac on 2010-04-30
Still nothing in /mnt.

sudo fdisk -l (with L not 1 this time) gives:

```

    Device Boot       Start       End     Blocks   Id  System
 /dev/sda1  *             1      4685   37626880   83  Linux
 /dev/sda2             4685      4864    1440769    5  Extended
 /dev/sda5             4685      4864    1440768   82  Linux swap / Solaris

```

So then I ran:

```

sudo mount /dev/sda1 /mnt

```

And it returned:

```

mount: unknown filesystem type 'ext4'

```

I ignored that, went ahead and ran

```

gksudo nautilus /

```

It returned:

```

Initializing nautilus-share extension
seahorse nautilus module initialized
** (nautilus:9036): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed:net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

The window opened, I navigated to /mnt and... it was empty.

---

### Post by GSF1200S on 2010-04-30
> **HistoryMac said:**
> Still nothing in /mnt.

sudo fdisk -l (with L not 1 this time) gives:

```

    Device Boot       Start       End     Blocks   Id  System
 /dev/sda1  *             1      4685   37626880   83  Linux
 /dev/sda2             4685      4864    1440769    5  Extended
 /dev/sda5             4685      4864    1440768   82  Linux swap / Solaris

```

So then I ran:

```

sudo mount /dev/sda1 /mnt

```

And it returned:

```

mount: unknown filesystem type 'ext4'

```

I ignored that, went ahead and ran

```

gksudo nautilus /

```

It returned:

```

Initializing nautilus-share extension
seahorse nautilus module initialized
** (nautilus:9036): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed:net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

The window opened, I navigated to /mnt and... it was empty.

Huh? I dont know whats going on. What liveCD are you using? Im assuming you are on the Ubuntu 10.04 LiveCD. I see mention of samba there- It doesnt matter if it launches and you can see directories and such though..

When fdisk returned EXT4 as an unknown filesystem type, its suggesting to me that you are running a LiveCD without EXT4 filesystem support (I believe 9.10 was the first ubuntu version to support EXT4). Are you perhaps on an older version of Ubuntu doing this or on a different distro without ext4 support? What version of e2fsprogs are you running?

---

### Post by HistoryMac on 2010-04-30
> **GSF1200S said:**
> Huh? I dont know whats going on. What liveCD are you using? Im assuming you are on the Ubuntu 10.04 LiveCD. I see mention of samba there- It doesnt matter if it launches and you can see directories and such though..

When fdisk returned EXT4 as an unknown filesystem type, its suggesting to me that you are running a LiveCD without EXT4 filesystem support (I believe 9.10 was the first ubuntu version to support EXT4). Are you perhaps on an older version of Ubuntu doing this or on a different distro without ext4 support? What version of e2fsprogs are you running?

Ah, that'll be it. I'm using an 8.10 LiveCD I had lying around (because the 10.04 one won't work). Should I go burn a 9.10 LiveCD? And sorry to have to ask, but what is e2fsprogs?

---

### Post by GSF1200S on 2010-04-30
> **HistoryMac said:**
> Ah, that'll be it. I'm using an 8.10 LiveCD I had lying around (because the 10.04 one won't work). Should I go burn a 9.10 LiveCD? And sorry to have to ask, but what is e2fsprogs?

Well, you can use a 10.04 livecd to install as well (if you used a LiveCD). 9.10 will work as well. e2fsprogs is the package that allows manipulation of ext filesystems (ext2, ext3, and now ext4). You dont need to check- I would download a 10.04 liveCD (good to have laying around as you can see) and try those instructions from there..

---

### Post by HistoryMac on 2010-05-01
> **GSF1200S said:**
> Well, you can use a 10.04 livecd to install as well (if you used a LiveCD). 9.10 will work as well. e2fsprogs is the package that allows manipulation of ext filesystems (ext2, ext3, and now ext4). You dont need to check- I would download a 10.04 liveCD (good to have laying around as you can see) and try those instructions from there..

Okay, 10.04 is downloading now. In what Vista suggests will be 58 minutes, I'll boot into a Live session with it and see what I can do. Thanks again.

---

### Post by not1 on 2010-05-01
At fist I thought I had the same problem on my Toshiba Portege, so in order to follow your steps I downloaded and burned 10.04 to use it as a livecd.

However, I noticed that after HistoryMac's splash nothing happened - with me, the hard drive spins like crazy.

I used the LiveCD and hit "Try Ubuntu without installing" 

the splash comes up and processing occurs, but after that I get a black screen with a really noisy system. The same symptoms I have usually.

My CD is fine. Does anybody know what is going on? I'll branch this question into a new thread if no one answers or if that is the proper procedure.

I have been running Ubuntu distros on this laptop for years now. I don't want to try a clean install because I have information I want to retain at least in my home folder.

Regardless of using Ubuntu for a long while I'm still an amateur end user, I wouldn't know where to start without help.

Is this a video/graphics problem?

---

### Post by not1 on 2010-05-01
should i use recovery kernal to use terminal and follow your steps?

EDIT: my problem diverted to [http://ubuntuforums.org/showthread.php?p=9207342#post9207342]("http://ubuntuforums.org/showthread.php?p=9207342#post9207342")

---

### Post by GSF1200S on 2010-05-01
> **HistoryMac said:**
> Okay, 10.04 is downloading now. In what Vista suggests will be 58 minutes, I'll boot into a Live session with it and see what I can do. Thanks again.

Cool, let me know what happens :)

---

### Post by HistoryMac on 2010-05-01
> **GSF1200S said:**
> Cool, let me know what happens :)

Well I burnt the disk, popped it in and booted up. There it was: the purple splash screen in all it's glory. Eureka! I thought.  Alas, it was just messing with me. Some 6 or 7 (Actually, more like 20) seconds later - black screen, no HDD activity. :(

---

### Post by GSF1200S on 2010-05-01
> **HistoryMac said:**
> Well I burnt the disk, popped it in and booted up. There it was: the purple splash screen in all it's glory. Eureka! I thought.  Alas, it was just messing with me. Some 6 or 7 (Actually, more like 20) seconds later - black screen, no HDD activity. :(

Man.. its fighting you all the way. Boot up the live cd again. When you get to the screen which asks for language, select english. BEFORE telling the cd to try ubuntu, press F6 and then ESC- remove: 
```
quiet splash
``` 
from the end of the boot line (its the only line with these words), add ```
nomodeset
``` 
and then proceed to boot the live cd. It should load fine.

---

### Post by HistoryMac on 2010-05-01
> **GSF1200S said:**
> Man.. its fighting you all the way. Boot up the live cd again. When you get to the screen which asks for language, select english. BEFORE telling the cd to try ubuntu, press F6 and then ESC- remove: 
```
quiet splash
``` 
from the end of the boot line (its the only line with these words), add ```
nomodeset
``` 
and then proceed to boot the live cd. It should load fine.

It seems to be pretty determined not to work. Removing quiet splash and adding nomodeset results in a command line as opposed to a splash screen, but the same inevitable black screen.

---

### Post by GSF1200S on 2010-05-01
> **HistoryMac said:**
> It seems to be pretty determined not to work. Removing quiet splash and adding nomodeset results in a command line as opposed to a splash screen, but the same inevitable black screen.

We WILL win!

Go back to the same screen, remove splash and quiet as I said before, but this time add:
```
xdriver=vesa
```

I cant believe this is such a pain.. I guess youre an unlucky one today :( This HAS to work..

---

### Post by HistoryMac on 2010-05-01
> **GSF1200S said:**
> We WILL win!

Go back to the same screen, remove splash and quiet as I said before, but this time add:
```
xdriver=vesa
```

I cant believe this is such a pain.. I guess youre an unlucky one today :( This HAS to work..

I must be a really unlucky one! xdriver=vesa has the same result as nomodeset. Prompt, black screen, frustration.

---

### Post by GSF1200S on 2010-05-01
> **HistoryMac said:**
> I must be a really unlucky one! xdriver=vesa has the same result as nomodeset. Prompt, black screen, frustration.

Man.. im out of ideas.. at this point, im not sure that 10.04 would work even if you managed to chroot into the partition and do the changes I suggested. I had a similar problem to you, and I fixed it as I mentioned on the first page, and its worked for others. I know that 9.10 will likely boot. All I can say is to wipe the partition you installed and put 9.10 back on. I can suggest installing a separate /home so that when you update releases as such, you dont lose anything if you have to revert. If youre really brave, you can install 9.10 on a seperate partition, along with a separate /home and then chroot into 10.04 from there occasionally and apply the updates in hopes that a patch fixes it. This is the hazard when you try to support every computer made not knowing what the hardware is going to be.

I hope someone else has a good idea that helps you out- sorry I couldnt be more help :(

---

### Post by Blinc on 2010-05-01
Hi 

I had this problem on my Toshiba U400 installing 9.10 - also worked fine on other computers, but not on the Tosh! I burnt the ISO again, setting drive speed to 4x - solved the problem.

Maybe a [slightly] related issue: just installed 10.04 on the same Tosh U400 - X server keeps crashing, and there doesn't seem to be a workaround / fix that works! 

My advice is stay away from 10.04 for a while on the Tosh until more help is available...

---

### Post by not1 on 2010-05-01
I am much less technologically savvy than either of you however:

HistoryMac, considering that we both have Toshiba Portege's and both have similar problems I'd imagine going into recovery mode (pressing esc at GRUB loading) and then using the failsafe graphical environment will work for you - albeit not fully. I think it may all come down to a driver bug or something.

Hey we also both live in Victoria! That's one heck of a coincidence.

---

### Post by HistoryMac on 2010-05-01
> **GSF1200S said:**
> Man.. im out of ideas.. at this point, im not sure that 10.04 would work even if you managed to chroot into the partition and do the changes I suggested. I had a similar problem to you, and I fixed it as I mentioned on the first page, and its worked for others. I know that 9.10 will likely boot. All I can say is to wipe the partition you installed and put 9.10 back on. I can suggest installing a separate /home so that when you update releases as such, you dont lose anything if you have to revert. If youre really brave, you can install 9.10 on a seperate partition, along with a separate /home and then chroot into 10.04 from there occasionally and apply the updates in hopes that a patch fixes it. This is the hazard when you try to support every computer made not knowing what the hardware is going to be.

I hope someone else has a good idea that helps you out- sorry I couldnt be more help :(

Whoa. Don't give up yet, I just hit a breakthrough.

I followed these steps:

1. When you see the purple box with the little keyboard and person, hit a key to enter options.
2. Choose your language.
3. Verify you have chosen "Try Ubuntu without any changes."
4. Press F6.
5. Press Esc to get out of the menu that pops up.
6. Go to the end of the commandline (with arrow keys if necessary) and type: "i915.modeset=0 xforcevesa" (no quotes; that is a zero, not a capital O; I also was able to boot without "xforcevesa" at the end).
7. Hit Enter and pray hard.

And the LiveCD booted, I got to the desktop no worries. I'm just not sure exactly how to apply this to the final installation. Ideas? I'm keen to hear them :) Thanks so much for everything so far, by the way. This is why I love Ubuntu, the community.

---

### Post by HistoryMac on 2010-05-01
> **not1 said:**
> I am much less technologically savvy than either of you however:

HistoryMac, considering that we both have Toshiba Portege's and both have similar problems I'd imagine going into recovery mode (pressing esc at GRUB loading) and then using the failsafe graphical environment will work for you - albeit not fully. I think it may all come down to a driver bug or something.

Hey we also both live in Victoria! That's one heck of a coincidence.

Gee, those are a nice bunch of coincidences. Unfortunately the failsafe environment was one of the first things I tried. Still, we can keep trying. I suggest you check out my last post, try following the steps there - they worked for my LiveCD, they may work for your installation. Good luck! :)

---

### Post by elnur on 2010-05-01
I got a similar problem on my system which is far away from Toshiba.

LiveCD boots and installation runs, but after installation is complete, I restart my system and see a flashing underscore. Nothing more. I don't even see GRUB or anything else.

Tried GSF1200S's solution, but that didn't help.

---

### Post by HistoryMac on 2010-05-01
> **elnur said:**
> I got a similar problem on my system which is far away from Toshiba.

LiveCD boots and installation runs, but after installation is complete, I restart my system and see a flashing underscore. Nothing more. I don't even see GRUB or anything else.

Tried GSF1200S's solution, but that didn't help.

Sorry I can't help more, but just so you know GRUB is now hidden from the boot process. You can, however, get it to show by holding SHIFT as the machine turns on. From there maybe you can find a solution that works for you.

---

### Post by GSF1200S on 2010-05-01
> **HistoryMac said:**
> Whoa. Don't give up yet, I just hit a breakthrough.

I followed these steps:

1. When you see the purple box with the little keyboard and person, hit a key to enter options.
2. Choose your language.
3. Verify you have chosen "Try Ubuntu without any changes."
4. Press F6.
5. Press Esc to get out of the menu that pops up.
6. Go to the end of the commandline (with arrow keys if necessary) and type: "i915.modeset=0 xforcevesa" (no quotes; that is a zero, not a capital O; I also was able to boot without "xforcevesa" at the end).
7. Hit Enter and pray hard.

And the LiveCD booted, I got to the desktop no worries. I'm just not sure exactly how to apply this to the final installation. Ideas? I'm keen to hear them :) Thanks so much for everything so far, by the way. This is why I love Ubuntu, the community.

**EDIT** Ignore my prior post here. Just hold down left shift on your harddrive install and add that i915.modeset=0 xforcevesa to the end of the boot line (remove splash and quiet for good measure), that will get you into the desktop without all the chroot stuff most likely..

---

### Post by Havokdan on 2010-05-01
> **elnur said:**
> I got a similar problem on my system which is far away from Toshiba.

LiveCD boots and installation runs, but after installation is complete, I restart my system and see a flashing underscore. Nothing more. I don't even see GRUB or anything else.

Tried GSF1200S's solution, but that didn't help.

My problem is exactly the same as yours.But my computer is not a notebook or netbook, a PC is the same.

*Sorry, I did not speak English, despite having reasonable ability to read. I use the Google translator to speak here.

---

### Post by not1 on 2010-05-01
unfortunately using F6 during the booting of the LiveCD just gives

```
GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

```

There was a recent thread about it [here]("http://ubuntuforums.org/showthread.php?p=9205447"). Although it seems that has nothing to do with anything.

It seems pressing  F6, or any function key for that matter, simply results in alternating from the prompt and the Ubuntu splash and adding this to the prompt:

```

stdin: error 0
```

All hope is lost I guess.

---

### Post by Hellbike on 2010-05-01
got exactly same problem on my old hp laptop (9020).

---

### Post by elnur on 2010-05-01
> **Havokdan said:**
> My problem is exactly the same as yours.But my computer is not a notebook or netbook, a PC is the same.


I'm on PC, too. ASUS P7P55D, Intel Core i7, NVIDIA GeForce GTX275. Can't find a solution after more than 5 hours of searching.

---

### Post by not1 on 2010-05-01
> **GSF1200S said:**
> Just hold down left shift on your harddrive install and add that i915.modeset=0 xforcevesa to the end of the boot line

Forgive my ignorance, but where is this bootline you are talking about?

The GRUB loading stage? Or does HistoryMac's machine have a bootline when he got the splash working?

---

### Post by elnur on 2010-05-01
> **HistoryMac said:**
> Sorry I can't help more, but just so you know GRUB is now hidden from the boot process. You can, however, get it to show by holding SHIFT as the machine turns on. From there maybe you can find a solution that works for you.

I have already tried that for several times and still get the same result.

---

### Post by Havokdan on 2010-05-01
When I try booting the live, can not boot the pc is locked in a message (sorry, but I do not remember exactly the message, besides my English as I mention be limited):

"Bug founded...Cpu stuck for 61s...Plymouth problem"

> I'm on PC, too. ASUS P7P55D, Intel Core i7, NVIDIA GeForce GTX275. Can't find a solution after more than 5 hours of searching.

Mine is: AMM Sempron +3000 1.8 Ghz, 1 Giga ram, 2 hds(160+40), Ati Radeon 9250.

---

### Post by GSF1200S on 2010-05-01
> **not1 said:**
> Forgive my ignorance, but where is this bootline you are talking about?

The GRUB loading stage? Or does HistoryMac's machine have a bootline when he got the splash working?

You hold down left shift to get the grub loading screen to show, then you move over the linux install you would normally boot (normally the one that is highlighted), and then hit 'e'

After that, the boot line usually contains ro quiet splash- thats where you make these changes.

---

### Post by GSF1200S on 2010-05-01
> **Havokdan said:**
> When I try booting the live, can not boot the pc is locked in a message (sorry, but I do not remember exactly the message, besides my English as I mention be limited):

"Bug founded...Cpu stuck for 61s...Plymouth problem"



Mine is: AMM Sempron +3000 1.8 Ghz, 1 Giga ram, 2 hds(160+40), Ati Radeon 9250.

If you edit the bootline as I said above, and REMOVE splash, I think plymouth will not be loaded. Try that and see if it helps..

---

### Post by elnur on 2010-05-01
> **Havokdan said:**
> When I try booting the live, can not boot the pc is locked in a message:

"Bug founded...Cpu stuck for 61s...Plymouth problem"

At least you get some message. My installation runs as it should, but then all I get is this flashing cursor and nothing more to tell me what is the problem.

---

### Post by GSF1200S on 2010-05-01
> **elnur said:**
> I'm on PC, too. ASUS P7P55D, Intel Core i7, NVIDIA GeForce GTX275. Can't find a solution after more than 5 hours of searching.

Youve got an nvidia card- my solution SHOULD work, but im not guaranteeing it. Have you tried what I suggested on the first page? If you cant get the livecd to load, try appending nomodeset to and removing quiet splash from the bootline.

**EDIT** I had the exact same problem with an nvidia card and my first post fixed it, but I had the luxury of having a 9.10 install working great to chroot in from.

Can everyone else who is in this thread tell me what cards you are using so I can keep it straight. HistoryMac, any updates?

**EDIT2** Upon reread of this thread, I can see that you were able to boot without the xforcevesa historymac- thats the ticket. If you just leave that off your bootline, you should have functioning intel drivers and 3d acceleration.

---

### Post by HistoryMac on 2010-05-01
> **GSF1200S said:**
> HistoryMac, any updates?
Yep - It aint' working. Tried changing the boot command through grub, still results in black screen. Not sure why this works with the LiveCD but not with the final installation...

---

### Post by Hellbike on 2010-05-01
there is solution:

edit /etc/X11/xorg.conf
add "Driver "vesa""

> Section "Device"
	Identifier	"Configured Video Device"

Driver "vesa"
EndSection

---

### Post by Elie-M on 2010-05-01
ur black screen would be probably from an xserver-xorg fail.

try to boot in recovery mode, use the netroot mode (the one with  networking enabled)

use sudo apt-get purge xserver-xorg && sudo apt-get install  xserver-xorg


this will remove it completly then reinstall it again. that worked for  me

---

### Post by elnur on 2010-05-01
> **GSF1200S said:**
> Youve got an nvidia card- my solution SHOULD work, but im not guaranteeing it. Have you tried what I suggested on the first page?

Yea, the first thing I did was to try your solution from the first page. It didn't help.

> **GSF1200S said:**
> 
If you cant get the livecd to load, try appending nomodeset to and removing quiet splash from the bootline.


I can load it and it works fine. Can't get why it works and the installed system doesn't.

> **GSF1200S said:**
> 
**EDIT** I had the exact same problem with an nvidia card and my first post fixed it, but I had the luxury of having a 9.10 install working great to chroot in from.


If I can boot LiveCD, I don't need that luxury, need I?

---

### Post by elnur on 2010-05-01
I just have tried rebooting my system for several times and noticed one interesting thing. After BIOS messages (I think they are called POST, but I'm not sure about that), I saw a flashing cursor on the **first** line of the screen for several milliseconds, then the screen went black, and then the cursor came back. But this time the cursor was on the **2nd or 3rd** line.

Maybe this makes some sense to somebody.

---

### Post by not1 on 2010-05-01
> **GSF1200S said:**
> You hold down left shift to get the grub loading screen to show, then you move over the linux install you would normally boot (normally the one that is highlighted), and then hit 'e'

After that, the boot line usually contains ro quiet splash- thats where you make these changes.

Sorry about my lack of intelligence with these questions and statements of confusion - I hope they dont frustrate you too much:

I already have the GRUB loading screen appearing... at least on trying to boot the HDD install. The HDD install flashes the splash and then hangs.

If you are talking about Live there is no mention of GRUB, after "trying w/out installing" I get a flashing underscore followed by the Ubuntu splash which works. Pressing F6 here just gives me: 

```
GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
```

I am probably talking nonsense. I am really confused.
You are awesome by the way.

> **GSF1200S said:**
> Can everyone else who is in this thread tell me what cards you are using so I can keep it straight.

Intel 855GM

---

### Post by HistoryMac on 2010-05-01
> **Elie-M said:**
> ur black screen would be probably from an xserver-xorg fail.

try to boot in recovery mode, use the netroot mode (the one with  networking enabled)

use sudo apt-get purge xserver-xorg && sudo apt-get install  xserver-xorg


this will remove it completly then reinstall it again. that worked for  me

Sorry, who's black screen? We all seem to have slightly different forms of the same problem.

---

### Post by elnur on 2010-05-01
> **Hellbike said:**
> there is solution:

edit /etc/X11/xorg.conf
add "Driver "vesa""

Erm. I don't have /etc/X11/xorg.conf file. Is that OK?

---

### Post by rbala on 2010-05-01
OK,

I had this issue...Not anywhere after following GFS's instructions. Only thing did it in a different way.

My Original Problem:
1. I turn on my PC
2. Grub appears, i select ubuntu, ubuntu tries to boot up
3. i get this splash..then a black screen appears with "underscore" on left top corner, and a hanged mouse cursor. Nothing works after that...no HDD activity no keyboard/mouse nothing...complete freeze.

Work Around:
1. I turn on PC
2. Grub appears, i select ubuntu, ubuntu tries to boot up
3. i get this splash screen...immediately i pressed Ctrl+Alt+F1 several times. i get to tty console
4. The followed GFS's insttructions ...navigated to /etc/default/grub, editted grub's quite splash to nomodeset
5. updated initramfs
6. updated grub2 (all these instructions are in page 1)
7. reboot, and bingo!!! my screen comes up.


Thanks GFS et all

---

### Post by Elie-M on 2010-05-01
> **HistoryMac said:**
> Sorry, who's black screen? We all seem to have slightly different forms of the same problem.


I'm talking abt a boot of 10.04 directly into a black screen followed by ubuntu booting u into a tty1 terminal console. and I solved it the way I did put my instructions

---

### Post by GSF1200S on 2010-05-01
> **HistoryMac said:**
> Yep - It aint' working. Tried changing the boot command through grub, still results in black screen. Not sure why this works with the LiveCD but not with the final installation...

nomodeset appended to grub did not work for me when I did it via grub- when I chrooted, it fixed it (multiple times). I was trying to fix plymouth at the time..

Try using the liveCD, chroot in as on the first page and add both lines to the GRUB_CMDLINE_LINUX_DEFAULT="" part while removing quiet and splash. Then update initramfs and grub, and see what happens. We are forcing vesa, dealing with modeset, and eliminating splash. I dont suppose any of you removed pulseaudio? That caused my kernel to freeze as well, until I reinstalled pulseaudio from the chroot.

Beyond this, im out of ideas.. im trying to think of something, and Ill let you know if I do- let me know how it goes..

---

### Post by GSF1200S on 2010-05-01
> **not1 said:**
> Sorry about my lack of intelligence with these questions and statements of confusion - I hope they dont frustrate you too much:

I already have the GRUB loading screen appearing... at least on trying to boot the HDD install. The HDD install flashes the splash and then hangs.

If you are talking about Live there is no mention of GRUB, after "trying w/out installing" I get a flashing underscore followed by the Ubuntu splash which works. Pressing F6 here just gives me: 

```
GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
```

I am probably talking nonsense. I am really confused.
You are awesome by the way.



Intel 855GM

Someone said this and I didnt correct it because I figured they knew something I didnt. You select your language and BEFORE selecting try Ubuntu, you hit F6 and escape, then you edit the bootline from there. Im about to burn a livecd and try it on my desktop while helping you guys from my netbook.

---

### Post by dino99 on 2010-05-01
Some commands to check errors and repair them:

need to open a terminal:
- if you fail to boot completly but can use the keyboard, press ALT+F2 to call a terminal, then:

1) sudo dpkg --configure -a
2) sudo dpkg-reconfigure gdm
3) sudo dpkg-reconfigure plymouth
4) sudo apt-get update
5) sudo apt-get install -f

validate these commands one by one, if errors appear with 5): read and note what is missing or wrong:
a) if missing: sudo apt-get install "the missing package name"
b) if wrong: sudo dpkg-reconfigure "the wrong package name"

Hope that can help some of you :)

- if you can boot but have errors:
look at system --> admin -- log viewer for errors
and .Xsession-errors into /home/your user/.Xsession-errors ( . stand for hidden file, so into menu check "show hidden file"

---

### Post by GSF1200S on 2010-05-01
> **dino99 said:**
> Some commands to check errors and repair them:

need to open a terminal:
- if you fail to boot completly but can use the keyboard, press ALT+F2 to call a terminal, then:

1) sudo dpkg --configure -a
2) sudo dpkg-reconfigure gdm
3) sudo dpkg-reconfigure plymouth
4) sudo apt-get update
5) sudo apt-get install -f

validate these commands one by one, if errors appear with 5): read and note what is missing or wrong:
a) if missing: sudo apt-get install "the missing package name"
b) if wrong: sudo dpkg-reconfigure "the wrong package name"

Hope that can help some of you :)

- if you can boot but have errors:
look at system --> admin -- log viewer for errors
and .Xsession-errors into /home/your user/.Xsession-errors ( . stand for hidden file, so into menu check "show hidden file"

Very good suggestion- thanks for adding. For those of you running Ubuntu (as opposed to Xubuntu/Kubuntu) I might also suggest
```
sudo apt-get install ubuntu-desktop
```

If the liveCD is loading for you, please do the mount and chroot portion as listed on the first page of this thread, then run one additional command:
```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```

This will allow your chrooted partition to have DNS resolution, or plainly, internet access. That way, you can run all the commands Dino99 suggested as well as the one I suggested.

Thanks again for that suggestion- bravo :)

---

### Post by not1 on 2010-05-01
> **GSF1200S said:**
> Someone said this and I didnt correct it because I figured they knew something I didnt. You select your language and BEFORE selecting try Ubuntu, you hit F6 and escape, then you edit the bootline from there. Im about to burn a livecd and try it on my desktop while helping you guys from my netbook.

Ok awesome. I have the boot edit line.

Now before I go and do something stupid do I type "i915.modeset=0 xforcevesa" like HistoryMac? Or do I need a different driver name with my chipset?

And to the other solutions that have recently been posted, I am not ignoring you - I just want to try this first.

---

### Post by GSF1200S on 2010-05-01
> **not1 said:**
> Ok awesome. I have the boot edit line.

Now before I go and do something stupid do I type "i915.modeset=0 xforcevesa" like HistoryMac? Or do I need a different driver name with my chipset?

And to the other solutions that have recently been posted, I am not ignoring you - I just want to try this first.

What vid card do you have (sorry, its hard to keep them all straight- this thread has gotten crazy)? If you have an nvidia card, add:
```
nomodeset
```
and remove:
```
quiet splash
```

If you have an intel card, add:
```
i915.modeset=0 xforcevesa
```
and remove:
```
quiet splash
```

---

### Post by GSF1200S on 2010-05-01
> **rbala said:**
> OK,

I had this issue...Not anywhere after following GFS's instructions. Only thing did it in a different way.

My Original Problem:
1. I turn on my PC
2. Grub appears, i select ubuntu, ubuntu tries to boot up
3. i get this splash..then a black screen appears with "underscore" on left top corner, and a hanged mouse cursor. Nothing works after that...no HDD activity no keyboard/mouse nothing...complete freeze.

Work Around:
1. I turn on PC
2. Grub appears, i select ubuntu, ubuntu tries to boot up
3. i get this splash screen...immediately i pressed Ctrl+Alt+F1 several times. i get to tty console
4. The followed GFS's insttructions ...navigated to /etc/default/grub, editted grub's quite splash to nomodeset
5. updated initramfs
6. updated grub2 (all these instructions are in page 1)
7. reboot, and bingo!!! my screen comes up.


Thanks GFS et all

Glad it helped :)

---

### Post by Dave M G on 2010-05-01
Hello,

I had a laptop that was running 9.10 without problems.

I tried running the update, and it got almost to the end, and then failed, citing a MySQL package as having some kind of problem. It said the system might be unstable.

I attempted to reboot, but nothing would happen.

So I downloaded the install CD for 10.04, and tried to install. However, the live CD will only boot to a blank screen. Alt+Ctrl+F1 does nothing. Pressing shift, or escape, does nothing.

I downloaded the alternate install CD, and attempted to install with that. It went through the whole process (I formatted root partition, kept my home partition).

And then at the very end, when it rebooted, a blank screen.

This time, when I reboot and hold down the shift key, I can get a GRUB menu from where I can boot to a command prompt.

However, there is no network support even if I select "with networking", so I can't download or change any packages.

I have handled similar issues before, and I think my laptop uses an Nvidia graphics driver which is probably failing.

However, I am restraining myself greatly from ranting about the difficulty of upgrading.

All I want is for my laptop to work like it did with 9.10. Do I have to download a 9.10 CD and go back? Or is there any way of getting 10.04 to get past this blank screen.

---

### Post by dino99 on 2010-05-01
> **not1 said:**
> Ok awesome. I have the boot edit line.

Now before I go and do something stupid do I type "i915.modeset=0 xforcevesa" like HistoryMac? Or do I need a different driver name with my chipset?

And to the other solutions that have recently been posted, I am not ignoring you - I just want to try this first.

you use i915 if your chipset is i915, if its an other, replace by that other, if you dont know exactly use nomodeset, anyway if it fail dont worry that break nothing, you only have to find what works for you

---

### Post by not1 on 2010-05-01
> **GSF1200S said:**
> What vid card do you have (sorry, its hard to keep them all straight- this thread has gotten crazy)? If you have an nvidia card, add:
```
nomodeset
```
and remove:
```
quiet splash
```

If you have an intel card, add:
```
i915.modeset=0 xforcevesa
```
and remove:
```
quiet splash
```

Ok. I have an Intel 855GM, Ill see what happens and get back to you :)

---

### Post by GSF1200S on 2010-05-01
> **not1 said:**
> Ok. I have an Intel 855GM, Ill see what happens and get back to you :)

Crap... See dino99's suggestion above- as Ive said I use an nvidia card so Im shooting in the dark trying to help you guys with intel cards. It looks like 915 should be replaced with 855 or 855GM (im not sure which).

---

### Post by elnur on 2010-05-01
When I install grub, I get the following output:
```

root@ubuntu:/# grub-install /dev/sda
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb

```

I don't understand what is this fd0 device. If it somehow relates to floppy drive, I don't have any.

May it be the reason I can't get to GRUB?

---

### Post by not1 on 2010-05-01
> **GSF1200S said:**
> Crap... See dino99's suggestion above- as Ive said I use an nvidia card so Im shooting in the dark trying to help you guys with intel cards. It looks like 915 should be replaced with 855 or 855GM (im not sure which).

Well whatever happened it did something. Unlike the previous one line error I have outlined elsewhere it spat out a huge amount of booting code.

then went to a weird huge messup of lines and stuff.

The screen went blank for like 3 minutes. Then I heard the Ubuntu startup tune, the default background a cursor and the "Install Ubuntu 10.04" icon, then a toolbar, etc, etc

SUCCESS!

But this is mighty slow - then again I have never used Ubuntu Live.

Now how does this work in the scope of things? How do I get it to work on my HDD?

---

### Post by GSF1200S on 2010-05-01
> **not1 said:**
> Well whatever happened it did something. Unlike the previous one line error I have outlined elsewhere it spat out a huge amount of booting code.

then went to a weird huge messup of lines and stuff.

The screen went blank for like 3 minutes. Then I heard the Ubuntu startup tune, the default background a cursor and the "Install Ubuntu 10.04" icon, then a toolbar, etc, etc

SUCCESS!

But this is mighty slow - then again I have never used Ubuntu Live.

Now how does this work in the scope of things? How do I get it to work on my HDD?
**EDIT** This is a culmination of the information in this thread that has helped people boot. I compiled it together to make things easier (how bout that- compiling makes things easier for once, eh? ;) )

Load a liveCD. Open a terminal and run:
Code:
> 
sudo fdisk -l
and determine what partition 10.04 is installed on. Then, mount that partition. Assuming your / (root) partition is /dev/sda1:

> sudo mount /dev/sda1 /mnt

Then open nautilus as root:

> gksudo nautilus /

Then, navigate to /etc/default/grub and open it. Look for the line that says:
Code:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

(or whatever it says inside the " ") and change it to:
Code:
(For nvidia)
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
(for intel)
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=0"
Save and close.

Then, chroot into the system as follows:
> sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
Then, check out dino99's suggestions (you will be able to do them assuming the liveCD is connected to the internet):
> Some commands to check errors and repair them:

need to open a terminal:
- if you fail to boot completly (GSF1200S Edit: Or if you make it into the liveCD) but can use the keyboard, (GSF1200S Edit: you dont need to press alt f2 in the live environment, just open a terminal) press ALT+F2 to call a terminal, then:

1) sudo dpkg --configure -a
2) sudo dpkg-reconfigure gdm
3) sudo dpkg-reconfigure plymouth
4) sudo apt-get update
5) sudo apt-get install -f
6) sudo apt-get install ubuntu-desktop (added by GSF1200S)

validate these commands one by one, if errors appear with 5): read and note what is missing or wrong:
a) if missing: sudo apt-get install "the missing package name"
b) if wrong: sudo dpkg-reconfigure "the wrong package name"

Hope that can help some of you (GSF1200S Edit: Make sure you are looking in the directory where you mounted the 10.04 install, NOT the ubuntu live CD location)

- if you can boot but have errors:
look at system --> admin -- log viewer for errors
and .Xsession-errors into /home/your user/.Xsession-errors ( . stand for hidden file, so into menu check "show hidden file"

Then run:
> sudo update-initramfs -u
sudo update-grub2
and then close that terminal. Open another and put in:
> sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /dev/sda1
and then restart and hopefully it will boot.

---

### Post by HistoryMac on 2010-05-01
> **GSF1200S said:**
> Crap... See dino99's suggestion above- as Ive said I use an nvidia card so Im shooting in the dark trying to help you guys with intel cards. It looks like 915 should be replaced with 855 or 855GM (im not sure which).

Hmm... Really? Cause I'm fairly sure the Tosh I have here uses an 855GM chip, but the i915 command is what's gotten me this far.

---

### Post by dino99 on 2010-05-01
[COLOR="Red"][SIZE="4"]General Notes:[/SIZE][/COLOR]

- Lucid dont need xorg.conf by default, its the kernel job now (so built-in). Of course kernel cant deal yet with all the different cards and chipsets, so sometimes we need to tweak a custom xorg.conf (/etc/X11/xorg.conf)

There are lot of troubles with old xorg.conf (those having dist-upgrading), so first thing is to remove it:

sudo rm -f /etc/X11/xorg.conf

dont worry on next reboot Lucid will take care of that smootly  :)

- If ubuntu devs work hardly to fine tune drivers, its not for nothing, there is to much troubles with proprio drivers. So you might use the distro driver in priority, but if you have no luck with them (mostly with the too recent cards or chipsets, better to use driver from ppa if already built ([https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)) , at least use proprio drivers.

- into synaptic, you find lot of: xserver-xorg-video-something
where "something" is the chipset name. If its yours, it might be installed, no need the others filed by the meta-package xserver-xorg-video-all.
In case of trouble with your video driver, reconfigure it:
sudo dpkg-reconfigure xserver-xorg-video-"your chipset driver"

About Grub2:

to those having dist-upgrading and was using previously grub1 (=grub-legacy), you have to remove/purge everything about it as there are troubles with grub2. First into synaptic, remove/purge all the grub installed packages, then install grub-pc and grub-common, when asked install grub on the Lucid mbr partition ( /dev/sda or so, if you dont remember where it is, check it first).
Then into console: sudo grub-mkconfig && update-grub ( if you have multi distro)

---

### Post by GSF1200S on 2010-05-01
> **HistoryMac said:**
> Hmm... Really? Cause I'm fairly sure the Tosh I have here uses an 855GM chip, but the i915 command is what's gotten me this far.

Ok, I did the above post doing as you suggested. If anyone very knowledgeable with intel knows better, please inform us. Where are you stuck at HistoryMac? Im having a hard time keeping up with everyones issues.. :(

---

### Post by dino99 on 2010-05-01
> **GSF1200S said:**
> Ok, I did the above post doing as you suggested. If anyone very knowledgeable with intel knows better, please inform us. Where are you stuck at HistoryMac? Im having a hard time keeping up with everyones issues.. :(

i know a good friend of mine and i'm sharing with you its name because you are desperate ubuntu's users: GOOGLE

Note that you are not alone having the same troubles with the same hardware, and there are good chances that somewhere somebody has already had your problems and found a solution  :P

---

### Post by HistoryMac on 2010-05-01
> **GSF1200S said:**
> Ok, I did the above post doing as you suggested. If anyone very knowledgeable with intel knows better, please inform us. Where are you stuck at HistoryMac? Im having a hard time keeping up with everyones issues.. :(

Hey, no worries! I just finished doing a clean install of 10.04 (from the LiveCD, which now works with the i915 workaround) because the install I was working with before was getting kinda messed up because of all the fixes I had attempted. Now I am going to follow the last post you made and see what happens. Will report back shortly! :)

---

### Post by elnur on 2010-05-01
I have finally solved my problem. The reason of it is really stupid. Here it goes.

I got two HDDs, /dev/sda and /dev/sdb. I've installed Ubuntu on /dev/sda, but in BIOS it was set to boot from /dev/sdb. (The reason is that previously I had Ubuntu on /dev/sdb and Windows on /dev/sda, and had been booting from /dev/sdb because GRUB was there. This time I got rid of Windows and installed Ubuntu on /dev/sda, leaving /dev/sdb unformatted for now.) That's why I saw nothing except a flashing cursor.

The mistake was mine, but at least something could tell me that it can't find anything bootable...

---

### Post by elnur on 2010-05-01
And thank you all for your attempts to solve the problem.

---

### Post by HistoryMac on 2010-05-01
Okay, following the instructions everything goes fine until I get to 
```

sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

```

Apparently, 
```

cp: cannot stat `/etc/resolv.conf': No such file or directory

```

Ideas?

---

### Post by GSF1200S on 2010-05-01
> **HistoryMac said:**
> Okay, following the instructions everything goes fine until I get to 
```

sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

```

Apparently, 
```

cp: cannot stat `/etc/resolv.conf': No such file or directory

```

Ideas?

Are you connected to the internet on the livecd? Let me boot a liveCD and ill monitor this thread from my netbook..

---

### Post by HistoryMac on 2010-05-01
> **GSF1200S said:**
> Are you connected to the internet on the livecd? Let me boot a liveCD and ill monitor this thread from my netbook..

Ah, connected to my WiFi and the prompt ran without a glitch. Will continue to follow your instructions and report back accordingly.

---

### Post by HistoryMac on 2010-05-01
Okay, quick question - After I run
```

sudo chroot /mnt

```
Do I close Terminal and open a new one, just continue, or open a new tab in Terminal before continuing on?

---

### Post by GSF1200S on 2010-05-01
> **HistoryMac said:**
> Okay, quick question - After I run
```

sudo chroot /mnt

```
Do I close Terminal and open a new one, just continue, or open a new tab in Terminal before continuing on?

No, you WANT to keep using that terminal. That terminal is the one you are chrooted into your install with. No new tab, no new terminal ;)

---

### Post by HistoryMac on 2010-05-01
> **GSF1200S said:**
> No, you WANT to keep using that terminal. That terminal is the one you are chrooted into your install with. No new tab, no new terminal ;)

Okay, so now do I run through each of Dino99's suggestions one by one? (Incidentally, after running the first one I received "sudo: unable to resolve host ubuntu")

---

### Post by not1 on 2010-05-01
unfortunately it didnt boot

BUT

I believe I did something wrong along the way, because my none of dino's commands were responding with anything in the terminal.

this fight isnt over yet.

And I should take this moment to thank GSF1200S for his ENORMOUS help and my apologies to HistoryMac for kind of hijacking the thread.

---

### Post by HistoryMac on 2010-05-01
> **not1 said:**
> unfortunately it didnt boot

BUT

I believe I did something wrong along the way, because my none of dino's commands were responding with anything in the terminal.

this fight isnt over yet.

And I should take this moment to thank GSF1200S for his ENORMOUS help and my apologies to HistoryMac for kind of hijacking the thread.

No apologies necessary! The more people benefiting from the thread, the better. Happy computing! :)

---

### Post by GSF1200S on 2010-05-01
> **HistoryMac said:**
> Okay, so now do I run through each of Dino99's suggestions one by one? (Incidentally, after running the first one I received "sudo: unable to resolve host ubuntu")

If it says unable to resolve host, then you wont be able to run his commands. Unable to resolve host means you dont have internet in the chroot jail. I dont understand how this could possibly be the case considering you have an internet connection via the liveCD and you ran:
```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```
Incidentally, you can try to do the bits that I mentioned and attempt to do dino99's commands ignoring the errors (hopefully the dpkg commands will fix it), and then do the initramfs and grub update- that should get you booting. Ill double check myself with the resolv.conf in the meantime (chroot into my 9.10 install).

---

### Post by not1 on 2010-05-01
I went back to /etc/default/grub and it had reverted back to quiet splash. I dont know why.

Extra newbie question: why dont we add "xforcevesa" as with the livecd?

---

### Post by not1 on 2010-05-01
OH MY...

Could someone please post a screenshot of their grub file and/or tell me the line under GRUB_CMDLINE_LINUX_DEFAULT?

I think i did something very very silly

---

### Post by GSF1200S on 2010-05-01
> **not1 said:**
> unfortunately it didnt boot

BUT

I believe I did something wrong along the way, because my none of dino's commands were responding with anything in the terminal.

this fight isnt over yet.

And I should take this moment to thank GSF1200S for his ENORMOUS help and my apologies to HistoryMac for kind of hijacking the thread.

Effort, not help.. I havent managed to get you guys up and running, and im getting very tired. Most of his commands shouldnt spit out anything if everything is going well. apt-get update, apt-get install commands SHOULD spit out some output though.. Did it do the same thing as before? Where does it freeze? This may be over my head :(

---

### Post by HistoryMac on 2010-05-01
> **GSF1200S said:**
> If it says unable to resolve host, then you wont be able to run his commands. Unable to resolve host means you dont have internet in the chroot jail. I dont understand how this could possibly be the case considering you have an internet connection via the liveCD and you ran:
```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```
Incidentally, you can try to do the bits that I mentioned and attempt to do dino99's commands ignoring the errors (hopefully the dpkg commands will fix it), and then do the initramfs and grub update- that should get you booting. Ill double check myself with the resolv.conf in the meantime (chroot into my 9.10 install).

Yep, not sure why but the "unable to resolve host ubuntu" are appearing but the commands are running properly anyway, I know because I can see their progress (delays, downloading files, etc.) I went through everything without a single hiccup until I get to
```

sudo umount /dev/sda1

```

Terminal returns:
```

umount: /mnt: device is busy.

```

So close! What to do?

---

### Post by GSF1200S on 2010-05-01
> **HistoryMac said:**
> Yep, not sure why but the "unable to resolve host ubuntu" are appearing but the commands are running properly anyway, I know because I can see their progress (delays, downloading files, etc.) I went through everything without a single hiccup until I get to
```

sudo umount /dev/sda1

```

Terminal returns:
```

umount: /mnt: device is busy.

```

So close! What to do?

type exit in the chroot terminal. If nothing else, the liveCD will unmount it when you hit restart- I do that in case the liveCD messes up and because its always a good idea to unmount a drive rather than turn it off in the middle of writes. A reboot on the LiveCD should go okay though..

---

### Post by HistoryMac on 2010-05-01
[SIZE="6"]IT LIVES![/SIZE]

:popcorn:

Thank you so much for everything, it's been along day and I definitely couldn't have done this on my own. Hopefully everyone else with this issue will be able to benefit from this thread too.

---

### Post by GSF1200S on 2010-05-01
> **HistoryMac said:**
> [SIZE="6"]IT LIVES![/SIZE]

:popcorn:

Thank you so much for everything, it's been along day and I definitely couldn't have done this on my own. Hopefully everyone else with this issue will be able to benefit from this thread too.

Really??! Man.. Im really glad its going man.. Have fun with 10.04 ;)

(Note: Hopefully its smooth from here on out :?)

---

### Post by not1 on 2010-05-01
> **GSF1200S said:**
> type exit in the chroot terminal. If nothing else, the liveCD will unmount it when you hit restart- I do that in case the liveCD messes up and because its always a good idea to unmount a drive rather than turn it off in the middle of writes. A reboot on the LiveCD should go okay though..

congrats buddy.

To GSF1200S it seems a reason my terminal wasn't working was when I did gksudo nautilus - it gave me some sort of networking error or something that froze the processing.

There is hope yet.

Im not giving up after a whole day of this crap.

---

### Post by not1 on 2010-05-01
And can someone please upload their grub file

[size="7"]please[/size]:(

---

### Post by elnur on 2010-05-01
I'm glad your problem is solved, but I would like to answer to some of your problems, so that others may benefit.

> **HistoryMac said:**
> 
```

sudo umount /dev/sda1

```

Terminal returns:
```

umount: /mnt: device is busy.

```

So close! What to do?

I solved it this way:

```

sudo umount /mnt/dev
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt

```

By the way. I had Internet connection in my chroot jail without doing anything special like this:
```

sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

```
Maybe you don't need it, too.

---

### Post by elnur on 2010-05-01
> **not1 said:**
> And can someone please upload their grub file

[size="7"]please[/size]:(

Here is my /etc/default/grub in initial state after the fresh installation:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by not1 on 2010-05-01
> **elnur said:**
> Here is my /etc/default/grub in initial state after the fresh installation:


Thankyou.

I have one more question to ask. When I type
```
sudo update-grub2
```
I get command not found, why?

Is  it the reason the file reverts back to quiet splash?

---

### Post by GSF1200S on 2010-05-01
> **elnur said:**
> I'm glad your problem is solved, but I would like to answer to some of your problems, so that others may benefit.



I solved it this way:

```

sudo umount /mnt/dev
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt

```

By the way. I had Internet connection in my chroot jail without doing anything special like this:
```

sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

```
Maybe you don't need it, too.

Hmmm.. really? I needed it to chroot into 10.04 from 9.10- without it I could not download any packages. Ill do some research on this later today and make sure.

**EDIT** Seems theres more to this than I know.. I need to do more research, but you can see the /etc/resolv.conf mentioned over in the Arch forums, as well as the OP stating it worked fine without such modifications. Ill need to boot up Arch and see whats up:
[http://bbs.archlinux.org/viewtopic.php?id=54201](http://bbs.archlinux.org/viewtopic.php?id=54201)

---

### Post by GSF1200S on 2010-05-01
> **not1 said:**
> Thankyou.

I have one more question to ask. When I type
```
sudo update-grub2
```
I get command not found, why?

Is  it the reason the file reverts back to quiet splash?

Yes it is. This is a hard drive install of fresh 10.04 allowing it to do grub and all right? My question is, how were you booting it in the first place? Did you upgrade? If so, youre probably using Grub 1, which you would update using:
```
sudo update-grub
```
(actually, that command may work for whatever one is installed, so perhaps I should check and then change it).

**EDIT** I just need to know, if the above does not work, how you were booting Ubuntu. If you arent using grub, I honestly dont know what to do. I dont use Lilo and Im not familiar with any other loaders. If it is a variant of grub, the sudo update-grub or sudo update-grub2 in chroot should work to append those options and remove splash/quiet to/from the boot line.

---

### Post by GSF1200S on 2010-05-01
> **elnur said:**
> I'm glad your problem is solved, but I would like to answer to some of your problems, so that others may benefit.



I solved it this way:

```

sudo umount /mnt/dev
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt

```

By the way. I had Internet connection in my chroot jail without doing anything special like this:
```

sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

```
Maybe you don't need it, too.

Makes sense- didnt think to try considering I had appended --bind, but its logical and works. Im fairly new to chroot, but at least its helping some people (and it helped me for sure). Thanks alot for the information :)

**EDIT** I have to get some sleep. Dying over here ;) Ill check the thread when I wake up before I start tuning the bike and see if anything further has developed. Good luck..

---

### Post by GuitarG on 2010-05-01
> **GSF1200S said:**
> 
```
i915.modeset=0 xforcevesa
```
This worked for me. Live CD boot, entered code, system booted and I was able to use the update 10.04 icon on the desktop for the install.
Thanks for all of your help.

---

### Post by not1 on 2010-05-01
> **GSF1200S said:**
> Yes it is. This is a hard drive install of fresh 10.04 allowing it to do grub and all right? My question is, how were you booting it in the first place? Did you upgrade? If so, youre probably using Grub 1, which you would update using:
```
sudo update-grub
```
(actually, that command may work for whatever one is installed, so perhaps I should check and then change it).

I am so confused.

Do I need grub 2? what do you mean by upgrade? Booting what? What is going on?

Why is my terminal hanging on this screen:
[IMG]http://imgur.com/hmkik.png[/IMG]


Why cant this work :C

---

### Post by GSF1200S on 2010-05-01
> **not1 said:**
> I am so confused.

Do I need grub 2? what do you mean by upgrade? Booting what? What is going on?

Why is my terminal hanging on this screen:
[IMG]http://imgur.com/hmkik.png[/IMG]


Why cant this work :C

Haha, common thing to get stuck on. This is complicated man, and hopefully the devs will work out the bugs. Im going to reference this thread in a bug report tomorrow so hopefully they can fix it. 

Hit 'tab' to select ok in that terminal, then hit enter. Go ahead and select ok and let it do its thing. Then, run the commands above in that compiled command post a page or two back and try to boot. Id love to stay up, but I need to get some sleep. Good luck, and ill check this thread tomorrow.. Glad it helped some of you :)

---

### Post by dino99 on 2010-05-01
READ what i've post previously, that answer your question

---

### Post by dino99 on 2010-05-01
> **not1 said:**
> And can someone please upload their grub file

[size="7"]please[/size]:(

Never do that, its stupid :lolflag:

each system is different of the others. Every time you have to:

remove grub-legacy if you have, then

sudo grub-mkconfig && update-grub

---

### Post by Dave M G on 2010-05-01
Note to developers:

Do not release a version of Ubuntu that has graphics drivers that do not work.

This situation is just stupid.

Pretty much a day of my life wasted trying to get around a black screen, and in the end I'm having to re-install 9.10.

Ubuntu 10.04 = Fail.

---

### Post by not1 on 2010-05-01
I'm tired, stressed and have no motivation to try new ideas.

Im done for today.

I intalled grub 2 i think
Then I updated it without checking the grub file because nautilus wasnt running.
I got the infinite underscore that someone else was talking about several pages back.

Thanks everyone for the support. Please respond upon seeing this.

---

### Post by GSF1200S on 2010-05-01
> **dino99 said:**
> READ what i've post previously, that answer your question

**EDIT** never mind...

---

### Post by not1 on 2010-05-01
> **GSF1200S said:**
> **EDIT** never mind...

hey now, that was a quality post.

---

### Post by not1 on 2010-05-01
[http://ubuntuforums.org/showthread.php?t=1467154](http://ubuntuforums.org/showthread.php?t=1467154)

d99's workaround looks very appealing but I have completely stuffed myself with this gnome-pc stuff.

How can I get back to the situation I was in at the start of the last page?

remove gnome-pc
install gnome?

Will such a thing work?
I feel close to the finish!

---

### Post by foxy123 on 2010-05-01
booting in failsafe mode worked for me. I also have an old 2.6.32-20 kernel which also works fine. However it is all on my test drive. Cannot still upgrade my main partition from Koala. Hopefully a fix will be released shortly. Still I find it unacceptable to have such bug in the final release of LTS.

---

### Post by jiex on 2010-05-01
Hi I posted this elsewhere, but realised that was the wrong section. So, i post it here again.
Hi there. 
I tried to upgrade through the manager and after it was finished (it took hours) my computer booted to the log in screen. I entered my name and P/W - then the screen went black. I could not get to the recovering page or anything, apart from the terminal.

I lot of searching revealed that it was likely a problem with my ATI display (its a 4200 onboard the motherboard). I read somewhere that the drivers that come with Ubuntu do not like the ATI / Radeon / Catalyst drivers AND then I recalled some advice I saw in my frenzy of searching: totally remove the ATI / Radeon/ Catalyst drivers and package. 

This I then tried. Easier said than done. 

Most removal approaches leave artefacts and the system finds those, becomes confused and chucks a wobbly. This was happening. I did a listing of software in yhr terminal - I think the command was:
<<dpkg -l '*fglrx*'>> and secondly <<locate fglrx>> - without the << and >>
Yup - fglrx was still there.
Finally, I found this page:
[https://wiki.ubuntu.com/X/Troublesho...thRadeonDriver](https://wiki.ubuntu.com/X/Troublesho...thRadeonDriver)
It recommended an "aggressive" complete removal and this is achieved by:
sudo /usr/share/ati/fglrx-uninstall.sh # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon

I also found this page, which has similar advice. 

[http://swiss.ubuntuforums.org/showthread.php?p=9202028](http://swiss.ubuntuforums.org/showthread.php?p=9202028)

However, remember: a standard uninstall won't remove enough of the ATI/Radeon/Catalyst drivers and you really have to go the whole hog - the "aggressive uninstall. When I did that, the machine booted OK and seems to work. The display is a bit odd - a little distorted, like 4:3 TV on 16:9. 

Were I doing the upgrade again (and when I have recovered my composure, I will do this I would cut Lucid to CD, back up all data then reformat disk and do a complete clean install. It would have been quicker. 

I have not tried reinstalling the latest ATI drvers, but will do that with the new install to see what happens.

On that, last time (for Karmic) they would not install properly through synaptic but I had to download the packege and install through the command line. I think for the most recent drivers they install via the ATI site somehow.

Given that the ATI drivers are known to cause problems, I do think that the Lucid installer should containn a sub-routine that removes totally the ATI drivers before installation upgrade commences and then it could give you the option to reinstall the latest ATI drivers. 

Tags for this post might be: ATI drivers black screen boot failure complete remove

---

### Post by HistoryMac on 2010-05-01
> **GSF1200S said:**
> Really??! Man.. Im really glad its going man.. Have fun with 10.04 ;)

(Note: Hopefully its smooth from here on out :?)

Things are pretty good (I <3 the Me Menu!) but there are a few little things that could be improved upon. I started a new thread for them [here]("http://ubuntuforums.org/showthread.php?p=9213849#post9213849"), seeing as this one is confusing enough already :P

---

### Post by not1 on 2010-05-02
> **not1 said:**
> [http://ubuntuforums.org/showthread.php?t=1467154](http://ubuntuforums.org/showthread.php?t=1467154)

d99's workaround looks very appealing but I have completely stuffed myself with this gnome-pc stuff.

How can I get back to the situation I was in at the start of the last page?

remove gnome-pc
install gnome?

Will such a thing work?
I feel close to the finish!


Does anyone know how to get gnome 1 back? Am I making sense?

---

### Post by not1 on 2010-05-02
I fixed up GRUB and used GSF1200S's solution. Everything now works perfectly. The only set back is I get bootline text instead of a pretty splash screen, but that is fine.

Thankyou so much.

---

### Post by HistoryMac on 2010-05-02
> **not1 said:**
> I fixed up GRUB and used GSF1200S's solution. Everything now works perfectly. The only set back is I get bootline text instead of a pretty splash screen, but that is fine.

Thankyou so much.

Same for me, small sacrifice I reckon. Congratulations on getting it working! :)

---

### Post by GSF1200S on 2010-05-02
Well, I prefer the text to Plymouth or a splash screen, but just for the sake of trying it out, I managed to get Plymouth working using this article:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")
Note: For you intel guys, do NOT USE nomodeset, because as this thread has shown, it will not work for you. I would use the i915.modeset=0 ALREADY added to the bootline, and then try to add the rest. If you do this, print out the first page of this thread so you have all the chroot commands handy (just in case it doesnt work for you and you need to revert back; I updated the first page to be like it is on page 8 where I compiled it all).

Works for me though on an Nvidia 9800GTX+. Glad you got up and running not1 :)

**EDIT** Also make sure that lucid's grub is grub-installed to the MBR, otherwise the kernel line parameters wont be added. So, for instance, if Lucid is on /dev/sda2, you would do (to make sure its installed right):
> sudo grub-install /dev/sda
Note that I DID NOT include the 2 at the end- we are installing to the mbr, so it needs to be this way. Then, run:
> sudo update-grub
(which you will do throughout the course of the article linked above)
Good luck!

---

### Post by ubfu on 2010-05-02
can the grub problem be done if we don't install grub 2 but install EasyBCD ?

---

### Post by cshannon1077 on 2010-05-02
hope somebody fixes it soon!!

---

### Post by Loshmi on 2010-05-13
I got Ho compaq 615, with ati mobility card inside, and AMD processor, and i am also having black screen issue...
i've tried radeon.modeset=0, and it didn't help...

---

### Post by thebigbug on 2010-05-23
> **Loshmi said:**
> I got Ho compaq 615, with ati mobility card inside, and AMD processor, and i am also having black screen issue...
i've tried radeon.modeset=0, and it didn't help...

Hi,
meme compaq. I use LinuxMint 9 (with ubu 10.04)
1 - At the boot press ESC
2 - Select mode secure
3 - When request select use low resolution
4 - to the term of the installation you still make boot from the CD live 
5 - and modification the /etc/default/grub rows.
    It changes the line:
    GRUB_CMDLINE_LINUX_DEFAULT=&#8221; quiet splash&#8221;
    in
    GRUB_CMDLINE_LINUX_DEFAULT= &#8220;acpi=off radeon.modeset=0 &#8243;
6 - then reboot
7 - You execute the updates and installs all driver the proposals
    (Driver hardware -> proposals 3 driver (2 wireless and 1 video)

LinuxMint (is good) = Ubuntu + software restricted

P.S. I have not tried this procedure on lucid lynx

---

### Post by narunas on 2010-06-04
Lenovo T500 - upgrade to Lucid Lynx - install "recommended" ATI drivers-
screen black after restart - this is terrible!

solution - 
Live CD boot into the laptop - mount and bind sys folders - like recommended in this thread.
run updates and re-installs on the gdm, etc...
boot again
warning about "low graphics mode" - select default - now it works

How do you get Lucid Lynx to give me a choice of graphics modes on start-up?

this black screen problem stumped a pretty good IT guy here who is all for Linux - I am just a mobile dev using to build android stuff. This glitch cost me a few hours of grief - not good for Ubuntu at all.

---

