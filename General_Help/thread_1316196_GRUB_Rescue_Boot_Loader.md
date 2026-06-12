---
title: "GRUB Rescue Boot Loader"
date: 2009-11-05
forum: General Help
---

### Post by oldtraveler on 2009-11-05
I have previously made a GRUB Rescue Boot Loader on a floppy using StartUp Manager.  It worked perfectly allowing me to boot either to Ubuntu or to the Windows Boot Loader.  Today I installed Ubuntu 9.10 and uninstalled Ubuntu 9.04 and now the old floppy will only boot to the Windows boot loader, while trying to boot to Ubuntu creates an error.  Okay I'll make a new floppy.  Wrong!  Again usuing the option contained in StartUp Manager to create such a floppy it starts the create process and then says "Error". As things now stand I have an emergency way to boot to Windows, but not to Ubuntu by using the old floppy. I even tried formatting the new floppy in Windows first.

How can I create the boot disk?

Oh yes, I have tried Super Grub Disk and that leads nowhere.

---

### Post by ranch hand on 2009-11-05
SUM, if you check, does not work with grub2.  The developer is working on it.  Give the guy a chance.

---

### Post by drs305 on 2009-11-05
I haven't worked with it, but check out the man page for "grub-mkrescue".

I'd be interested in hearing your experiences with it.

---

### Post by fox.esq on 2009-11-05
I've had problems like this with 8.04 9.04 and 9.10.  But I think it is happening more frequently with 9.10 because of the new GRUB.  The problem I believe is related to some issue with GRUB not looking far enough into the hard disk to find the info to load your OS.  

Do you have Linux on a separate hard drive?  If you do, then my sugestion is to download the latest version of Gparted and burn it as an .iso at the slowest speed, then boot up with it.  When you are inside find your linux harddrive.  Now, you'll have to move the ext4 partition over so that the first ~2-10 Gb are unformated.  It will take maybe 3 hours to compile, unless you are willing to just reformat the whole thing (less time, but make sure you have a small partition for booting, a large primary ext4 partition for linux and a ~4 Gb extended partition for linux swap).  Make it so that first unformated section is a primary partition as ext4, this will technically act as a boot partition (don't load linux on it).

Having your linux hard drive partitioned this way will allow grub to quickly see it on the hard drive and be able to call it up for loading.  For some reason motherboards/bios/grub only look so far into a hard drive to find the OS loading info; if they don't find it at the beginning then they just give up.

Hope this make sense and helps!

---

### Post by oldtraveler on 2009-11-05
> **ranch hand said:**
> SUM, if you check, does not work with grub2.  The developer is working on it.  Give the guy a chance.
SUM seemed to work just fine except for the inability to create the rescue disk.

---

### Post by drs305 on 2009-11-05
> **oldtraveler said:**
> SUM seemed to work just fine except for the inability to create the rescue disk.

Parts of it work and parts do not. The main ones, timeout and default OS, do, as does being able to add options to boot instructions.  

The SUM link in my signature line has a little, but not much, more on SUM and GRUB 2.

---

### Post by oldtraveler on 2009-11-05
> **drs305 said:**
> I haven't worked with it, but check out the man page for "grub-mkrescue".

I'd be interested in hearing your experiences with it.
I am too much of a newbie in Ubuntu to really understand what to do with "grub-mkrescue".  Commands and scripts leave me scratching my head.  Isn't there a simple GUI that will do this? I'm willing to try a command if I have some handholding.  I assume this is done in a terminal.

---

### Post by ranch hand on 2009-11-05
Try;
```

man grub-mkrescue

```
Yes this is in terminal.  I can help no more as I am on 9.04 and will not be back on a 9.10 install until tomorrow.

---

### Post by wilee-nilee on 2009-11-05
Have you tried in the terminal sudo update-grub, this should load the MS into grub which is now your boot program. I am assuming that you have MS then Karmic Installed. You dont want the MS boot accessed or part of the MBR you want grub to do the work.

---

### Post by oldtraveler on 2009-11-05
> **wilee-nilee said:**
> Have you tried in the terminal sudo update-grub, this should load the MS into grub which is now your boot program. I am assuming that you have MS then Karmic Installed. You dont want the MS boot accessed or part of the MBR you want grub to do the work.
I don't know that I understand this.  I currently am able to boot into GRUB and from there to select either Ubuntu or Windows loader.
What I want to do is to create a bootable rescue disk for GRUB.

---

### Post by wilee-nilee on 2009-11-06
> **oldtraveler said:**
> I don't know that I understand this.  I currently am able to boot into GRUB and from there to select either Ubuntu or Windows loader.
What I want to do is to create a bootable rescue disk for GRUB.

I guess I was thrown off by you wanting to have the grub or windows boot loader. 
If the rescue disc is what you think you need then you might try super grub it has some interesting options, although I haven't had it work so well with Karmic's ext4 but I think super grub will get caught up, I haven' checked which version I have or tried to use it in a moth or so.
[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by Trog on 2009-11-06
If you want a floppy to boot into grub and no further, use the package manager to download grub-rescue-pc.
This will put the floppy image file at /usr/lib/grub-rescue/grub-rescue-floppy.img

Put in a blank floppy and use:-
**cat /usr/lib/grub-rescue/grub-rescue-floppy.img > /dev/fd0**

That will produce a floppy which will boot into grub

Typical commands to boot from grub:-

[B]set root=(hd0,1)
linux /vmlinuz root=/dev/sda1
initrd /initrd.img
boot[/B]

Those commands assume your linux disk is the first disk. (hd0,1 = disk1, partition 1 in grub but when you use /dev/sda1 the numbering is back to normal).
I'm having fun with this atm as I'm going through the same problem of wanting to use a boot floppy to select between Operating Systems instead of changing the MBR on the main disk. Lack of a floppy or USB boot option is a real pain in 9.10 with the new grub.

---

### Post by oldtraveler on 2009-11-06
> **Trog said:**
> If you want a floppy to boot into grub and no further, use the package manager to download grub-rescue-pc.
This will put the floppy image file at /usr/lib/grub-rescue/grub-rescue-floppy.img

Put in a blank floppy and use:-
**cat /usr/lib/grub-rescue/grub-rescue-floppy.img > /dev/fd0**

That will produce a floppy which will boot into grub

After installing grub-rescue-pc I put in a floppy and using terminal copied cat /usr/lib/grub-rescue/grub-rescue-floppy.img > /dev/fd0
Here is what I got:
phil@phil-desktop:~$ cat /usr/lib/grub-rescue/grub-rescue-floppy.img > /dev/fd0
bash: /dev/fd0: Permission denied
phil@phil-desktop:~$ 

As you can see permission is denied for some reason.

---

### Post by Trog on 2009-11-06
Sorry, I should have said do it as root

Start with:-
**sudo -s**

then do the "**cat**" instruction

---

### Post by oldtraveler on 2009-11-06
> **Trog said:**
> Sorry, I should have said do it as root

Start with:-
**sudo -s**

then do the "**cat**" instruction
OK.  Now it says "No such deivce or address"

phil@phil-desktop:~$ sudo -s
[sudo] password for phil: 
root@phil-desktop:~# cat /usr/lib/grub-rescue/grub-rescue-floppy.img > /dev/fd0
bash: /dev/fd0: No such device or address
root@phil-desktop:~#

---

### Post by Trog on 2009-11-06
Darn,
I really should have read your last post properly. 
Can you post back with the results of the follwing command?

**cat /proc/partitions**

---

### Post by Trog on 2009-11-06
> **oldtraveler said:**
> OK.  Now it says "No such deivce or address"

phil@phil-desktop:~$ sudo -s
[sudo] password for phil: 
root@phil-desktop:~# cat /usr/lib/grub-rescue/grub-rescue-floppy.img > /dev/fd0
bash: /dev/fd0: No such device or address
root@phil-desktop:~#
I can;t see why you can't access the floppy as /dev/fd0. Are you sure it's a good floppy disk?

---

### Post by louieb on 2009-11-06
> **Trog said:**
> ..;
Start with:-
**sudo -s**
then do the "**cat**" instruction

Make that ```
sudo -i
```

The difference being: -s uses the users environment (including home directory and path).  -i uses roots environment. and roots home and changes the path). 

Main reason sudo -i is safer for the user.  [RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 

don't know if it will help with the cat command

---

### Post by oldtraveler on 2009-11-06
> **Trog said:**
> Darn,
I really should have read your last post properly. 
Can you post back with the results of the follwing command?

**cat /proc/partitions**

phil@phil-desktop:~$ sudo -s
[sudo] password for phil: 
root@phil-desktop:~# cat /proc/partitions
major minor  #blocks  name

   8        0   29316672 sda
   8        1      16033 sda1
   8        2   13301820 sda2
   8        3          1 sda3
   8        5   15976611 sda5
   8       16   97906536 sdb
   8       17          1 sdb1
   8       18    6891885 sdb2
   8       19   75786606 sdb3
   8       21   12289693 sdb5
   8       22    2931831 sdb6
root@phil-desktop:~#

---

### Post by oldtraveler on 2009-11-06
> **Trog said:**
> I can;t see why you can't access the floppy as /dev/fd0. Are you sure it's a good floppy disk?
I just tried it with another floppy and soemthing was sritten on it.  I'll try to boot from it and let you know.

---

### Post by oldtraveler on 2009-11-06
Shucks!.  The floppy did boot to a grub menu of sorts, but different from the normal grub menu.  However, none of the options would boot to an OS. I kept getting an error  and asking me to press any key to continue, which I did and was taken back to the previous screen.

---

### Post by Trog on 2009-11-06
I'm off for shuteye (it's my age). If you have no joy, there is another option which is to revert the version of grub you are using to the old one using chroot, this will allow you to make a boot floppy but it's not straightforward. I'll have a go at doing it myself so I can get the steps sorted and make sure there are no pitfalls.

---

### Post by Trog on 2009-11-06
> **oldtraveler said:**
> Shucks!.  The floppy did boot to a grub menu of sorts, but different from the normal grub menu.  However, none of the options would boot to an OS. I kept getting an error  and asking me to press any key to continue, which I did and was taken back to the previous screen.

in the grub window if you press "c" it takes you to the command prompt, from there you can enter the commands I listed earlier
"Typical commands to boot from grub:-

set root=(hd0,1)
linux /vmlinuz root=/dev/sda1
initrd /initrd.img
boot

Those commands assume your linux disk is the first disk. (hd0,1 = disk1, partition 1 in grub but when you use /dev/sda1 the numbering is back to normal)."

If you know the partition number where your /boot/grub folder is then you should be able to get it to boot.

---

### Post by oldtraveler on 2009-11-06
My Ubuntu partition is sdb5 and the Windows partition is sda2.  I'm afraid to try any of this:

set root=(hd0,1)
linux /vmlinuz root=/dev/sda1
initrd /initrd.img
boot

Those commands assume your linux disk is the first disk. (hd0,1 = disk1, partition 1 in grub but when you use /dev/sda1 the numbering is back to normal)."

for fear that it will mess up my existing Grub which works just fine.

---

### Post by drs305 on 2009-11-06
> **oldtraveler said:**
> My Ubuntu partition is sdb5 and the Windows partition is sda2.  I'm afraid to try any of this:

set root=(hd0,1)
linux /vmlinuz root=/dev/sda1
initrd /initrd.img
boot

Those commands assume your linux disk is the first disk. (hd0,1 = disk1, partition 1 in grub but when you use /dev/sda1 the numbering is back to normal)."

for fear that it will mess up my existing Grub which works just fine.

Worry free testing:
Boot to the grub 2 menu. Press "c" to drop to the command line.
Enter the same commands that you want to test, pressing ENTER after each line. Make sure you set the correct root ID.
See if it works.
It won't make any permanent changes. If it works, you can add them to a custom menu.

---

### Post by Trog on 2009-11-06
> **oldtraveler said:**
> My Ubuntu partition is sdb5 and the Windows partition is sda2.  I'm afraid to try any of this:

set root=(hd0,1)
linux /vmlinuz root=/dev/sda1
initrd initrd.img
boot

Those commands assume your linux disk is the first disk. (hd0,1 = disk1, partition 1 in grub but when you use /dev/sda1 the numbering is back to normal)."

for fear that it will mess up my existing Grub which works just fine.


Fair enough, though anything you type in at the grub console is not saved anywhere. You now have a grub boot floppy which will allow you to boot your system.

Your commands would be:
**set root=(hd2,5)** or, possibly **set root=(hd2,4)** or** set root=(hd1,5)** or even **set root=(hd1,4)** :redface: 
(I've been experimenting with mine all evening, trying to work out how the grub disk/partition numbering works and, although I have it working, I'm still not sure how it's numbered, though this oddity may be due to a hardware raid configuration I'm using. I didn't break anything, even when I tried to use my windows XP partition to see what would happen. I'm using the first partition of my second drive and ended up typing in (hd2,0) which doesn't gel with what I've been told :-? )
**linux /boot/vmlinuz root=/dev/sdb5**   
[B]initrd /boot/initrd.img
boot[/B]

Anyway, good luck and if you need more help there's always lots of people here.

---

### Post by oldtraveler on 2009-11-08
I have tried those commands unsuccessfully and also have tried editing the options to the disk and partition on which the Ubuntu OS is located. Also edited to the Windows partition unsuccesfully.  No joy.  No OS booted.

All of this applies to booting from the floppy.  GRUB2 is working fine.

---

### Post by Trog on 2009-11-09
> **oldtraveler said:**
> I have tried those commands unsuccessfully and also have tried editing the options to the disk and partition on which the Ubuntu OS is located. Also edited to the Windows partition unsuccesfully.  No joy.  No OS booted.

All of this applies to booting from the floppy.  GRUB2 is working fine.

Did you also change this line:   *linux /vmlinuz root=/dev/sda1* To match you file location?
It should read like this:
**linux /boot/vmlinuz root=/dev/sdb5**

The original list I gave is for my system which has a separate /boot partition so it doesn't need "/boot" included in the path of the instruction. Yours is all on the same partition which means that the instruction needs the /boot path inserted in the instruction as shown above in bold.
Sorry if I haven't been too clear.

---

### Post by oldtraveler on 2009-11-09
Durn it.  No joy.

Editing the floppy entry for Linux to

**linux /boot/vmlinuz root=/dev/sdb5**

and pressing Ctrl X to boot produces this

**error:  no such partition**

Thought that perhaps sdb5 is not the linux partition so I reverted to Grub2 and looked at editing the linux entry, but it showed root=(hd1,5) which should be sdb5.

---

### Post by Trog on 2009-11-09
At this point I have to say I'm stuck for ideas. I've given you the same steps I've used to get mine working.

The only other option I can think of is to revert to the old grub.

---

