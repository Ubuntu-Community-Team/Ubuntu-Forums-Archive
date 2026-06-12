---
title: "error: no such partition. grub rescue&gt;"
date: 2010-05-24
forum: General Help
---

### Post by MsEvette on 2010-05-24
I am a newbie to Linux/Ubuntu. Apparently I altered my partitions while trying to make room for Ubuntu 10.04, and now I'm in a mess. For two days I have been searching the forums for a solution only to find instructions I don't understand or partial solutions.

Here's my situation.

I have an Acer AspireOne netbook (no CD).

I am able to access F2 setup, so I can prioritize the boot order. I can position my bootable  (ubuntu-10.04-netbook-i386.iso) usb drive at the top of list, but when my computer reboots via usb, there's just a black screen with a white dash in the upper left corner that flashes. 

When I boot with the hard drive I get:
error: no such partition.
grub rescue>

So far, the only commands I have found that work are:

grub rescue>ls
(hd0) (hd0,3) (hd0,2) (hd0,1)

grub rescue>set
prefix=(hd0,5)/boot/grub
root=hd0,5

Now, like I said, I'm a newbie. But that hd0,5 concerns me; doesn't seem to fit.

I'm not concerned with saving data. I'm willing to start from scratch. I just can't get past that grub rescue prompt and I can't access my usb port.

PLEASE HELP!

---

### Post by earthlogics on 2010-05-24
> **MsEvette said:**
> I am a newbie to Linux/Ubuntu. Apparently I altered my partitions while trying to make room for Ubuntu 10.04, and now I'm in a mess. For two days I have been searching the forums for a solution only to find instructions I don't understand or partial solutions.

Here's my situation.

I have an Acer AspireOne netbook (no CD).

I am able to access F2 setup, so I can prioritize the boot order. I can position my bootable  (ubuntu-10.04-netbook-i386.iso) usb drive at the top of list, but when my computer reboots via usb, there's just a black screen with a white dash in the upper left corner that flashes. 

When I boot with the hard drive I get:
error: no such partition.
grub rescue>

So far, the only commands I have found that work are:

grub rescue>ls
(hd0) (hd0,3) (hd0,2) (hd0,1)

grub rescue>set
prefix=(hd0,5)/boot/grub
root=hd0,5

Now, like I said, I'm a newbie. But that hd0,5 concerns me; doesn't seem to fit.

I'm not concerned with saving data. I'm willing to start from scratch. I just can't get past that grub rescue prompt and I can't access my usb port.

PLEASE HELP!  


HI There !!

I have the same problem since friday morning after I update the ubuntu and reboot,and until now i´ve found no solution :(, but in my case:
When I boot whith the hard drive it shows:
[I]
PXE-E53 : No boot filename received
PXE-MOF: Exiting PXE ROM
error: no such device: 66d8295f-a3f4-4c5a-a3c8-a55fefd74c49.
grub rescue>
grub rescue>ls
(hd0) (hd1) (fd0) (fd1)
grub rescue>set
prefix=(hd0)/boot/grub
root=hd0
[/I]   

Does any one have any Idea?
I'd appreciate!

---

### Post by kartabosh on 2010-05-24
this line 
error: no such device: 66d8295f-a3f4-4c5a-a3c8-a55fefd74c49.
looks like the fstab has the boot partition's uuid wrong which could be easily fixed from the live cd by replacing it
there's a gigantic chance that i might be wrong

---

### Post by earthlogics on 2010-05-24
> **kartabosh said:**
> this line 
error: no such device: 66d8295f-a3f4-4c5a-a3c8-a55fefd74c49.
looks like the fstab has the boot partition's uuid wrong which could be easily fixed from the live cd by replacing it
there's a gigantic chance that i might be wrong

I'll try to create a live cd or usb, then i'll give any feedback...

---

### Post by nana336 on 2010-05-24
I'm also dying with this problem...Trying all, no Luck...

---

### Post by earthlogics on 2010-05-27
I'd tried a live CD and it loads the ubuntu in the Grub perfectly, but it's not loading windows. 

ANY suggestions?

---

### Post by earthlogics on 2010-05-27
I'm trying it all,  I removed grub, ubuntu, and I'm reinstalling all over again...:confused:

---

### Post by searchfgold6789 on 2010-05-27
This is tough. To adequately supply you with a solution, it would help to know exactly what you did with your partitions, and where they are currently at.

You have installed 10.04. GRUB is something called a bootloader, and it is part of Ubuntu. Booting from your hard disk will cause your CMOS (setup program, the thing that looks for boot things on your hard drive and uses them to load the operating system, never breaks) to boot from the first partition on the hard disk, which may be windows, or it maybe ubuntu. GRUB, the bootloader, is probably currently installed on that partition, the first one; it can be installed on either the Windows partition or the Ubuntu one.

If you installed it on your windows partition, which I think you did but you might not have, then it can be deduced using this information that you installed Ubuntu on your second and third partitions (Ubuntu has two partitions, one for swap space which is like virtual memory and shouldn't be touched, google what a pagefile is for more info, and one for the main system).

So, if you messed around with your partitions, GRUB probably is finding the windows partition in the wrong spot.

(Don't try messing around with the prompt that comes up, you can't do very much with it.)

What I would do, is get it to boot from your thumb drive and google a command for reinstalling grub. Reinstall grub from the terminal on your thumb drive onto /dev/hd0 and see what happens. Something tells me you'll get grub back but some things will be missing from the list, from there someone can tell you how to fix grub up so it will find your partitions.

Really hope this works,
 - search

---

### Post by searchfgold6789 on 2010-05-27
Ignore the file i attached.........:-s

---

### Post by MsEvette on 2010-05-29
It appears as though a main point is being ignored here.

In my original post I stated, "when my computer reboots via usb, there's just a black screen with a  white dash in the upper left corner that flashes."

In other words, I am not able to utilize my usb port.  I cannot reload anything!

It seems as though my little netbook is bricked!

---

