---
title: "Kubuntu and Win 7 run without a bootloader"
date: 2011-04-29
forum: General Help
---

### Post by TurtleKing on 2011-04-29
Kubuntu and win 7 have their own separate hard drives. The problem showed up when I installed the new Kubuntu 11.04 (disconnected win7 hard drive in hope that it wouldn't affect the win boot loader) . As of now, it's just an annoyance since I can just hit f12 quickly during startup and decide which one I want to boot. I tried doing what other tutorial suggest, but I am a little nervous about their instruction in reference to what number I should jot down since situation may be a little different.

Basically, I want Grub or whatever good working boot-loader to be installed (I heard a rumor that a click-able one was in the making) on my Kubuntu hard drive, and avoid affecting my win 7 hard drive (they research now with the updates to make sure you got their boot-loader running *sigh).

Here is some data I collected from partition editor, hopefully this will assist somebody in understanding my problem better:

**ATA ST** (where linux is installed)
/dev/sda1; type: ext4; size: 461.76 GiB; Used: 20.77 GiB
/dev/sda2 type:  extended; size: 4.00 GIB; Used: 4.00 GiB
/dev/s...; type: linuxswap; size: 4.00GiB; Used: ---;

**ATA WDC** (Win 7 is installed)
/dev/sdb1; type: ntfs; size: 596.17 GiB; Used: 116.61 GiB

---

### Post by TurtleKing on 2011-04-29
bump.

---

### Post by aphatak on 2011-04-29
Does Kubuntu load as the default OS?  If it does, it looks like GRUB was installed correctly.  It will not show a menu because it found only a single operating system, and decided that a menu to choose an OS was irrelevant.

If Kubuntu does load without your doing anything, open a terminal and run the command 'sudo update-grub'.  After you key in the password to sudo, you should see a list of the operating systems GRUB finds.  When you re-boot, the GRUB menu should show up and allow you to choose the OS to boot.  This is not going to write anything to the Windows partition, merely scan it.

Just to make doubly sure, back up the MBR on the Windows hard disk.  So if you find it did get clobbered, you can restore it.

---

### Post by TurtleKing on 2011-04-30
Maybe the win7 master boot loader got deleted (upon selecting win7 hard drive from the motherboard menu it goes to the win7 loading screen), and that is why Grub can't find win 7? I updated grub and it didn't list any other OS. It just look for where and...actually let me post the response:

```
replaced@replaced:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.38-8-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```Gonna restart but I have a feeling it will still boot Kubuntu without a menu.

---

### Post by Wiebelhaus on 2011-04-30
That's where you goofed up , disconnecting the primary drive. Install *buntu with all drives attached , grub will handle it all for you perfectly.

---

### Post by TurtleKing on 2011-04-30
So i have to re-install kubuntu again? I figured there would be an easier method.:confused:

---

### Post by Lateralis on 2011-04-30
Shouldn't need to reinstall, no.  Just have all drives connected and do 

```

sudo update-grub

```

That should then pick up Windows 7 and add a line to your Grub menu.  

As a side note, so long as you don't tell the Ubuntu installer to install Grub on your Windows drive, then nothing will happen to your Windows bootloader.  So it is best to leave all hard drives connected during an installation so Grub can detect which OSs you have and add Grub menu entries as appropriate.

---

### Post by TurtleKing on 2011-04-30
> **Lateralis said:**
> Shouldn't need to reinstall, no.  Just have all drives connected and do 

```

sudo update-grub

```That should then pick up Windows 7 and add a line to your Grub menu.  

As a side note, so long as you don't tell the Ubuntu installer to install Grub on your Windows drive, then nothing will happen to your Windows bootloader.  So it is best to leave all hard drives connected during an installation so Grub can detect which OSs you have and add Grub menu entries as appropriate.
This is the result from trying that command in terminal. 
```

replaced@replaced:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.38-8-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```
I still get the startup without GRUB menu thing.Perhaps should I remove and re-install grub? or sudo update-grub from the live CD?

---

### Post by Lateralis on 2011-04-30
Have you upgraded to Maverick from an earlier distribution, or was Maverick a fresh install?  I'm possibly reading your post wrong, but it looks like it is writing /boot/grub/menu.lst, which is grub legacy, not grub 2.

---

### Post by TurtleKing on 2011-04-30
Fresh install of Kubuntu 11.04 64 bit. I did mess around with the grub installation thinking that maybe the future version might have had problems. Any suggestions?

---

### Post by TurtleKing on 2011-04-30
Can somebody please help me install Grub 2 again on the kubuntu 11.04 64 bit hard drive?:( 
```
ATA ST (where Kubuntu 11.04 is installed)
 /dev/sda1; type: ext4; size: 461.76 GiB; Used: 20.77 GiB
 /dev/sda2 type:  extended; size: 4.00 GIB; Used: 4.00 GiB
 /dev/s...; type: linuxswap; size: 4.00GiB; Used: ---;

```I will be away from my PC for several hours today, so if re-installing Kubuntu 11.04 is the only option, than I rather get it done today and start from scratch all over again tomorrow.

For users reading only this page or post (Problem): Kubuntu is automatically started instead of the grub menu or grub list of Operating Systems. In other words, Grub 2 doesn't see windows 7 OS or hard drive I guess.

---

### Post by aphatak on 2011-05-02
You might get away with not having to re-install Kubuntu.

Once you get into the desktop environment, start a terminal window.
[LIST=1]
[*]Run the command 'df'; that will tell you which disk partitions have been mounted.
[*]Then run the command 'sudo fdisk -l'.  This will ask for your password; when you enter it, it will display which disk partitions are accessible to Linux.  Make sure you know where your Linux partitions are (make sure it says '/dev/sda'), and where your Windows partitions are (make sure it does NOT say '/dev/sda').
[*]Finally, run 'sudo grub-install /dev/sda'.
[/LIST]
Of course, you would do this with the Windows hard disk connected.  And equally of course, you would have backed up all your data before you tinker with the innards of your PC!

---

### Post by TurtleKing on 2011-05-06
I decided to install Ubuntu 11.04 rather than keeping Kubuntu because the desktop would crash sometimes upon powering down or restarting (I had to hit the button). I am gonna miss not being able to run the login window theme (finger print scan theme). Why isn't the simplicity to choose your login-window theme on Ubuntu? :(

Anyways, I will mark the thread solve since I just installed ubuntu 11.04 with the win 7 hard drive connected (grub menu now), and I guessing your instructions would have solved the problem as well.

Thanks for the reply.

---

