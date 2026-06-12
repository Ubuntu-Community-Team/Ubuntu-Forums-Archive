---
title: "AHHH, grub error 17!"
date: 2009-09-18
forum: General Help
---

### Post by Jago6060 on 2009-09-18
I was trying to partition a USB stick to put pg_live on it.  Typed in a command, then my default netbook interface errored, so I rebooted, and it says
```

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17

```

I would post the command, but I don't remember what it was...and I can't go back and look...I think I made an uh-oh...Any ideas/help would be greatly appreciated.

---

### Post by lindsay7 on 2009-09-18
If you start your computer with the usb stick installed, your bios may be set to look for it before your hard drive.  Either remove the usb stick or look at your bios settings and change them if that is your problem.

---

### Post by Jago6060 on 2009-09-18
> **lindsay7 said:**
> If you start your computer with the usb stick installed, your bios may be set to look for it before your hard drive.  Either remove the usb stick or look at your bios settings and change them if that is your problem.

I get the error when booting from the HDD.

---

### Post by Zeosa on 2009-09-18
But is the USB drive still attached?

I get this on one of my desktops if my external usb HD is attached during bootup.

---

### Post by Jago6060 on 2009-09-18
> **Zeosa said:**
> But is the USB drive still attached?

I get this on one of my desktops if my external usb HD is attached during bootup.

No, nothing attached except the power cord.  Just for the heck of it, I tried booting from a slax USB and that worked fine.  But booting to the HDD without anything attached gives the GRUB Error 17

---

### Post by lindsay7 on 2009-09-18
When you were working with the usb you may have changed your grub setup to expect to see it on a usb. I am guessing this since your usb slax boots up.

Try this it should not hurt anything. Make sure there are no usbs attached, and do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type &#8220;sudo grub&#8221;. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Note:  Do not type in the quotation marks in the commands.

---

### Post by Jago6060 on 2009-09-18
> **lindsay7 said:**
> When you were working with the usb you may have changed your grub setup to expect to see it on a usb. I am guessing this since your usb slax boots up.

Try this it should not hurt anything. Make sure there are no usbs attached, and do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type “sudo grub”. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Note:  Do not type in the parenthesis in the commands.

It sounds like it would work...but I'm on a netbook, so no CD drive.  Would it work if I boot to a live ubuntu USB?

---

### Post by lindsay7 on 2009-09-18
It should.

---

### Post by Jago6060 on 2009-09-18
> **lindsay7 said:**
> It should.

Ok awesome.  I'm leaving work now so I'll try it when I get home.  I'm sure you'll hear from me again if it doesn't work, lol.  (I'll post it as a solution if it does)

---

### Post by Jago6060 on 2009-09-19
Ok, loaded with the live ubuntu USB, but there doesn't seem to be a way for me to get to a commandline.  Any ideas?

---

### Post by Jago6060 on 2009-09-19
Ok I think I figured out the problem.  In my quest with the USB, I think I changed my main partition to a fat16 because my partition setup is

/dev/sda1     fat16           146.21GiB
/dev/sda2     extended     2.84GiB
/devsda5      linux-swap   2.84GiB

How do I go about fixing this?  I'm currently loaded with the netbook remix USB, so I have use of GPart.

---

### Post by lindsay7 on 2009-09-19
If you have Ubuntu open, you should be able to go to the Application menu at the top and click on Accessories then terminal.  What version of Ubuntu are you using?

---

### Post by Jago6060 on 2009-09-19
> **lindsay7 said:**
> If you have Ubuntu open, you should be able to go to the Application menu at the top and click on Accessories then terminal.  What version of Ubuntu are you using?

9.04 netbook remix

I tried the steps you listed and got to "find /boot/grub/stage1" at which point it said file not found

---

### Post by lindsay7 on 2009-09-19
I have never used that, but you should have a way to get to the terminal.

---

### Post by Jago6060 on 2009-09-19
> **lindsay7 said:**
> I have never used that, but you should have a way to get to the terminal.

Yeah, I've got the terminal.  did sudo grub, then tried the command list, but it didnt workout after the find command

---

### Post by lindsay7 on 2009-09-19
Try typing  sudo grub-update,  then try the other commands I gave you.

---

### Post by Jago6060 on 2009-09-19
> **lindsay7 said:**
> Try typing  sudo grub-update,  then try the other commands I gave you.
command not found

---

### Post by lindsay7 on 2009-09-19
OK, lets see that the drive looks like,  type fdisk -l in the terminal and post the results that is a lower case L in fdisk -l.

---

### Post by Jago6060 on 2009-09-19
> **lindsay7 said:**
> OK, lets see that the drive looks like,  type fdisk -l in the terminal and post the results that is a lower case L in fdisk -l.

fdisk -l

Disk /dev/sdb:  16.2 GB, 16234053120 bytes
64 heads, 32 sectors/tracl, 15481 cylinders

This doesn't look like a partition table
Probably you selected the wrong device.

   Device    Boot         Start                      End             Blocks    Id   System
/dev/sdb1    ?          1031512                1987932    (big # here) 66   Unknown
Does not end on a cylinder boundry
/dev/sdb2    ?          (big # here)          (big # here) (big # here) 7    HPFS/NTFS
Does not end on a cylinder boundry  
/dev/sdb3    ?          (big # here)          (big # here)(big # here) 7d  Unknown
Does not end on a cylinder boundry
/dev/sdb4    ?          (big # here)          (big # here)(big # here) 6f  Unknown
Does not end on a cylinder boundry

I hand to type this by hand, hence the improv.  If the Start and End are imparitive, I can type them upon request.

---

### Post by lindsay7 on 2009-09-19
I just reread my post on the updat grub command, I gave you the wrong command you should type  sudo update-grub


See if that works and type in the list of commands and let me know what happens.

---

### Post by Jago6060 on 2009-09-19
> **lindsay7 said:**
> I just reread my post on the updat grub command, I gave you the wrong command you should type  sudo update-grub


See if that works and type in the list of commands and let me know what happens.

It says

No GRUB directory found.  To create a template run 'mkdir /boot/grub' first.  To install grub, install it manually or try th 'grub-install command. ### Warning, grub-install is used to change your MBR. ###

---

### Post by lindsay7 on 2009-09-19
Is sda or sdb you drive installed on you computer.  From what you have said sda is about 160 gigs and sdb is about 16.  Let me know.

---

### Post by Jago6060 on 2009-09-19
> **lindsay7 said:**
> Is sda or sdb you drive installed on you computer.  From what you have said sda is about 160 gigs and sdb is about 16.  Let me know.

sda is the HDD(160GB), sdb is the USB(16GB).

---

### Post by lindsay7 on 2009-09-19
> **Jago6060 said:**
> Ok I think I figured out the problem.  In my quest with the USB, I think I changed my main partition to a fat16 because my partition setup is

/dev/sda1     fat16           146.21GiB
/dev/sda2     extended     2.84GiB
/devsda5      linux-swap   2.84GiB

How do I go about fixing this?  I'm currently loaded with the netbook remix USB, so I have use of GPart.

Since you said that you think your partition was changed to fat16 and we can not find the grub directory, you may have messed up you partiton table.  I would download "Testdisk". It is in the repositories so you can get it there if you have an system that is working. Or you can download it from their web site. Read the documentation and run the program. It can restore partitions and may fix you problem.

---

### Post by Jago6060 on 2009-09-19
> **lindsay7 said:**
> Since you said that you think your partition was changed to fat16 and we can not find the grub directory, you may have messed up you partiton table.  I would download "Testdisk". It is in the repositories so you can get it there if you have an system that is working. Or you can download it from their web site. Read the documentation and run the program. It can restore partitions and may fix you problem.


Do you know how I can find out what the default partition types are for the netbook-remix?

---

### Post by lindsay7 on 2009-09-19
I do not know. You could open a new Thread and ask that question.  Testdisk, should restore what was there if it works.  All that said, if you look at Gparted format options, those are the most common, like fat16,fat31, ext2, ext3, ext4, ntsf, to name a few.

---

### Post by Jago6060 on 2009-09-19
> **lindsay7 said:**
> I do not know. You could open a new Thread and ask that question.  Testdisk, should restore what was there if it works.  All that said, if you look at Gparted format options, those are the most common, like fat16,fat31, ext2, ext3, ext4, ntsf, to name a few.

Yeah I checked to see what GParted would allow.  My thought is that maybe if I knew the default primary partition type, I could change it back, then GRUB would work correctly.  I don't have any internet access on the netbook as the NIC connections do not work by default with this particular netbook model.

---

### Post by lindsay7 on 2009-09-19
I do not think you can just change it back and do not format it if you have a chance to restore it. Testdisk can work miricles sometimes. Give a a try.

---

### Post by Jago6060 on 2009-09-19
> **lindsay7 said:**
> I do not think you can just change it back and do not format it if you have a chance to restore it. Testdisk can work miricles sometimes. Give a a try.

Tried Testdisk, didn't do anything unfortunately.  Is there something specific I need to have it do?

---

### Post by lindsay7 on 2009-09-19
There is a restore partition option. Did it run and give you any results.

---

### Post by lindsay7 on 2009-09-19
Did you do this, with Testdisk"?


Choose "Proceed","Intel","Analyze","Quick Search","Deeper Search".
This may take a while. 
When it is done you should see a list of partitions. 
Use the up/down arrows to select partitions.
Press "p" to see if you can list the files inside the partition.

---

### Post by Jago6060 on 2009-09-19
> **lindsay7 said:**
> There is a restore partition option. Did it run and give you any results.

Ok I tried that, and it said it wrote the partition table to disk, and to restart, so I restarted, but still get grub error 15

---

### Post by lindsay7 on 2009-09-19
Try those grub update commands and the sudo grub commands and see if you get any different results.

If that does not help. You should take a look at your sda1 partition and see if you can see any file.  If you can copy these to a place where you can save them. I am out of ideas if your sda1 shows not files. It may be possible to recover them, so if there is you would be best servered to start a new thread and ask for help doing that.

---

### Post by Jago6060 on 2009-09-21
> **lindsay7 said:**
> Try those grub update commands and the sudo grub commands and see if you get any different results.

If that does not help. You should take a look at your sda1 partition and see if you can see any file.  If you can copy these to a place where you can save them. I am out of ideas if your sda1 shows not files. It may be possible to recover them, so if there is you would be best servered to start a new thread and ask for help doing that.

Thanks for the help, but I've given up, lol.  Just decided to do a clean install.  I lost a few things but nothing vital aside from some homework.

---

