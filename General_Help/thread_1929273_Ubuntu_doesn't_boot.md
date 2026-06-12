---
title: "Ubuntu doesn't boot"
date: 2012-02-21
forum: General Help
---

### Post by Fenoxo on 2012-02-21
Hello everyone,

Finally I've decided to install Ubuntu in my laptop, but it doesn't boot from the hard disk (However, it works from the CD). So I read some threads on this forum and I've used the boot info script and this is the results


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  


I understand nothing, I don't know if it's due to the grub or something else. It would be a big help if someone could tell me what it's wrong. Thank you very much in advance.

Best regards.

---

### Post by Fenoxo on 2012-02-22
I have news. After reinstall and search some information, it shows the grub menu and after select generic mode, it turns everything black with a blinking cursor and nothing more. No matter what I do, I don't get entering ubuntu.

---

### Post by imachavel on 2012-02-22
grub 2? Strange, I would have thought ubuntu currently uses a legacy grub. That boot info script doesn't seem to be very detailed, please do the following, go to terminal:

ctrl+alt+t

and then type in

sudo apt-get install boot repair disk

if that doesn't work type 

sudo apt-get install boot repair

That should work, then go to search, find boot repair disk and open it, and then choose to create a grub script instead of repairing boot. now that you've done this, upload the entire grub script as an attachment please.

if none of those work, you can download boot repair disk from the internet, google it, download it, burn the .iso to a cd by right clicking on the file and try brasero burner. then put the disk in and create a grub script.


OR BETTER YET

you seem to have no problem creating a grub script, however you did so, please create another one, but upload the ENTIRE THING as an attachment. Or just go to the terminal and type

fdisk -l

then copy and paste into this thread

notice dev/ seems to be the bios read? I'm not sure but dev seems to remain as dev/. /sda1 or /sda2 would be partitions on your primary master boot device.  /sdb/ seems to be a partition on another secondary device, a slave device I believe but then it's not necessarily internal, could be a pen or external hard drive.

What exactly is the boot problem anyway? Have you tried using boot repair disk and using repair boot? This will fix mbr and grub of any file system whether it be windows ntfs or linux ext2/ext3/ext4 etc. With windows boot problem can be a bad drive that could be virus related or a bad disk. chkdsk and safe mode using virus scans would fix this.

with linux I believe fsck(chkdsk equivalent) runs automatically at boot. If it's not a bad sector with linux hardly a chance it's   a virus. Probably a corrupted file, my advice would be to use boot repair disk, or boot repair. Could be a driver issue, could be a memory issue, try running a memory test from the bios.

some more info would be helpful please. what model of computer is it? How many OSes installed? How many partitions? How did you install linux? Through an image written from an .iso to a cd? Anything you could explain will be helpful MORE INFO!

---

### Post by Fenoxo on 2012-02-25
First of all, I want to thank you for answering me.
 
And yes, I try it with a boot repair disk and follow this instructions:
 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 
When I type in the terminal this: sudo apt-get install boot repair disk, it shows me this message:
 
Reading package lists..... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package boot
E: Unable to locate package repair
E: Unable to locate package disk
 
When I type in the terminal this: sudo apt-get install boot repair, it shows me this message:
 
Reading package lists..... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package boot
E: Unable to locate package repair
 
When I type in the terminal this: fdisk -l, it doesn´t show me anything and a new line appears.
I try to type in the terminal "boot-repair" and nothing "boot-repair: command not found".
 
I only have one OS in the laptop (Ubuntu)
no windows,
no partitions,
nothing in the hd except Ubuntu (I formated before installing),
I tested the memory and everything is fine,
I install this version: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) and follow the instructions,
My laptop is Packard Bell Easy Note
and in the system info displays Ubuntu 11.10, Memory: 874.1 MiB, Processor: Intel Celeron(R) M CPU 520 @ 160 GHz, Graphics: Unknown, OS type: 32-bit, Disk: 916.6 MB.
 
I don't know what happens.

---

### Post by jefelex on 2012-02-25
it looks as if you either don't have enough memory or enough hard disk space to install 11.10 - maybe try an older version that requires less memory (can't remember offhand which version) or try lubuntu - it takes significantly less resources

---

### Post by Fenoxo on 2012-02-25
I think you are right, jefelex. But Ubuntu only requeries 256 MB of RAM and 4 GB of disk space, and I have 896 MB of RAM and 119 GB. When I try it from the CD it works, but it freezes after the grub menu.
 
At least, I've done the boot repair. This is the result: [http://paste.ubuntu.com/856579/](http://paste.ubuntu.com/856579/)

---

### Post by jefelex on 2012-02-25
Is your installation working now?  I hope it is - I looked at your paste.ubuntu.com, and everything looked ok at a glance.  I know that once you have it installed and start using it, you'll really like it for sure!

John

---

### Post by Fenoxo on 2012-02-26
Hi again,
 
After the boot repair, it doesn't work yet. So I try to install Xubuntu and Debian, and the result is the same. After selecting generic mode in the grub menu, the screen gets freezed with the blinking cursor on the left top. However, in Debian it freezes when in the screen appears "waiting for dev to be fully populated". I've read many forums and I think the problem is the kernel, because don't recognice my ATI.
 
Thank you very much for your replies, all help is appreciated.

---

### Post by jefelex on 2012-02-26
if you are getting the grub menu, this is a good thing! if it runs with the cd, then there should be no reason that it doesn't run Ubu with it on the hdd!  I think you are right with the ATI card - does it boot into maintenance mode?  if it boots into maintenance mode, then the problem is definitly with the graphics system.  you are right about the older ATI cards but all is not lost - the install that is on the hdd is thinking that the graphics card is capable of more than it actually is (as you have determined)  there are options that you can give to the grub boot that can disable graphics options at boot time, although I can't remember what they are since I don't install UBU frequently - try the grub maintenance mode first just to see if the UBU will set up a command line, and I'll see if I can find the boot options I was mentioning.  I have had in the past, where there were errors on the installation CD where the CD operating system sets up fine, but the install portion of the CD has errors on it.

Also, just so you know - I don't use 11.10 - I use 11.04, I'd try installing that instead - I looked up boot options, but couldn't find what I was looking for.  If you are new to Ubuntu, I'm sure you are finding there is a lot to learn! :-)

---

### Post by Carterclan on 2012-02-26
I had a problem with the kernel when my son upgraded from 11.04 to 11.10.
He had the same result as you have. I was able to get round it by booting into an older kernel that was available to me in grub.

So I disabled the kernel that didn't work and carried on using the older kernel until there was a kernel update.

Now there is no problem

---

### Post by Fenoxo on 2012-03-11
Hi everyone,

I was very busy, and I haven't run it yet. Jefelex, when you said maintenance mode do you refer to recovery mode? If it's so, it doesn't run. However, I've been reading some forums and I must edit the grub list (or something) with the command sudo gedit.

Thank you very much for your answers.

Best regards.

---

### Post by Fenoxo on 2012-03-31
Hi again,

I'm trying to edit the menu.lst but It doesn't exist, when I type in the terminal "sudo gedit /boot/grub/menu.lst" a new pop-up window appears completely empty. What can I do?

Thank you very much.

Best regards.

---

### Post by bobman321123 on 2012-03-31
> **Fenoxo said:**
> Hi again,

I'm trying to edit the menu.lst but It doesn't exist, when I type in the terminal "sudo gedit /boot/grub/menu.lst" a new pop-up window appears completely empty. What can I do?

Thank you very much.

Best regards.

You might have GRUB2, which has been used since 9.10. 
To get to it, use: 
```
sudo gedit /etc/default/grub
```

---

### Post by Fenoxo on 2012-04-01
Thank you bobman,

This is what it's written:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

And I don't know what I have to change for the kernel options or the graphic card.

---

### Post by Fenoxo on 2012-04-05
At least, I know what I have to do. I must add the next lines: apci = off, noapic, nolapic, edd=on, nodmraid, and some more but I don't know where I have to type them.

Thank you very much.

Best regards.

---

