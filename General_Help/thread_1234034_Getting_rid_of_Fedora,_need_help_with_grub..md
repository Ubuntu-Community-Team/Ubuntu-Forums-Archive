---
title: "Getting rid of Fedora, need help with grub."
date: 2009-08-07
forum: General Help
---

### Post by running_rabbit07 on 2009-08-07
Last night I installed Fedora. It will not let System Update connect to the network while at the same time I was surfing the net. 

Currently their grub doesn't show Ubuntu and while I want to keep Fedora around to learn more about it, I can't boot Ubuntu. Can anybody help me get Ubuntu back on the list?

SDA 5 is Ubuntu's / 

Thanx for your time and help.

Edit: I apologize for the thread title saying I was getting rid of Fedora, that was my original plan.

---

### Post by running_rabbit07 on 2009-08-07
I am going to try reinstalling Fedora to fix a bunch of problems that I think should have never existed. I have the feeling it just isn't going to work out though. Can anyone tell me how to fix the Ubuntu Grub from the LiveCD so I will not have to do a complete reinstall of Ubuntu just to be able to boot it? 

Thanx!

---

### Post by merlinus on 2009-08-07
Try this, if linux / is on sda5 as you indicated:

```
sudo grub
root (hd0,4)
setup (hd0)
quit
```and restart.

You can also use fdisk to fix the partitions not being in order:

```
sudo fdisk /dev/sda
x
f
w
```

---

### Post by running_rabbit07 on 2009-08-07
[COLOR=White]Cool thanx. [/COLOR]

---

### Post by running_rabbit07 on 2009-08-07
[COLOR=White]Now that I have loaded 2 OSes in one day I am ready for a cold beer and some TV. 

I have installed Fedora via their LiveCD instead of the big DVD I used last night and it is working. My new problem is getting Ubuntu into Fedora's grub so I can have both of my happy systems. 

Can anyone tell me how to do this? 

P.S. I opened an account for fedora's forum hours ago and they haven't got my account to where I can post yet.[/COLOR]

---

### Post by unutbu on 2009-08-07
Here is a guide on how to multi-boot:
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

If you'd like more detailed help on how to set it up, run 
```

sudo fdisk -l
```

and post the output, along with which partitition corresponds to which OS.

---

### Post by running_rabbit07 on 2009-08-07
> **unutbu said:**
> Here is a guide on how to multi-boot:
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

If you'd like more detailed help on how to set it up, run 
```

sudo fdisk -l
```and post the output, along with which partitition corresponds to which OS.

Fedora says I don't have sudoers powers yet, I have to figure out how to get that set up.

Thanx.

---

### Post by unutbu on 2009-08-07
Hm. Fedora may not use sudo as the most common way to gain root powers (like Ubuntu).
Perhaps try
```

su -
fdisk -l

```
When you installed Fedora did it ask you to setup a root password? If so, that is what you want to enter after the "su -" command.

---

### Post by running_rabbit07 on 2009-08-07
Great while trying to get root permisions in Fedora I managed to get it to a point where I can't even sign in. Anyway here's what fdisk -l says,

I am going to reboot now and see if Ubuntu's grub shows up after changing the boot flag.

---

### Post by unutbu on 2009-08-07
Open a terminal (in Fedora). As root, type
```

grub
grub> root (hd0,4)
grub> setup (hd0,4)
grub> exit

```
This will install a GRUB bootloader on /dev/sda5, your Ubuntu installation. 

The in Fedora, edit your /boot/grub/menu.lst
At the bottom of the file, add:
```

title      	Ubuntu
root       	(hd0,4)
chainloader +1

```

Then reboot.

---

### Post by running_rabbit07 on 2009-08-07
When I try to reboot I don't get a Grub error, just the BSOD but the B stands for black this time. Any advice? 

Thanx again and I am sorry I keep changing things before I can get a fix. Once I get grub going I am shutting this thing down for the weekend.

---

### Post by unutbu on 2009-08-07
Boot from the Ubuntu LiveCD.
Type
```

sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> exit
```

(This is also what merlinus wrote in post #2).

Reboot. You should be able to boot Ubuntu.

---

### Post by running_rabbit07 on 2009-08-07
Si! I have Ubuntu! Thanks again. I wasn't sure if after changing all the partitions that the command would work the same. It did. I am taking the rest of the night off. I have been playing with this thing all day. At least now I know how to fix grub when I mess it up.

Thanks both of you.

---

### Post by unutbu on 2009-08-07
Great! Cheers and good night.

---

### Post by merlinus on 2009-08-07
Excellent news!  Have fun...

---

### Post by running_rabbit07 on 2009-08-09
So, I have reinstalled Fedora and of course I could not for the life of me get Ubuntu on their boot loader. Could someone please tell me how to get Fedora on my Ubuntu Grub list? My fdisk -l looks like this,

rabbit@rabbid-rabbit:~$ su
Password: 
su: Authentication failure
rabbit@rabbid-rabbit:~$ sudo fdisk -l
[sudo] password for rabbit: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0defc2af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11693    93923991    7  HPFS/NTFS
/dev/sda2           11694       30401   150272010    f  W95 Ext'd (LBA)
/dev/sda5           11694       13517    14651248+  83  Linux
/dev/sda6           13518       21210    61793991   83  Linux
/dev/sda7           30098       30401     2441848+  82  Linux swap / Solaris
/dev/sda8   *       21211       21236      204799+  83  Linux
/dev/sda9           21236       30097    71180026+  8e  Linux LVM

Partition table entries are not in disk order
rabbit@rabbid-rabbit:~$ 

fedora is on sda8

Thank you for the help.

---

### Post by unutbu on 2009-08-09
Please boot Fedora and post your /boot/grub/menu.lst

---

### Post by running_rabbit07 on 2009-08-09
I can't boot Fedora, only Ubuntu. I reinstalled Ubuntu so that I could have access to my Bookmarks to take care of business. And because Grub seems easier to work with than Fedora's loader.

---

### Post by unutbu on 2009-08-09
Okay, then try this:

Boot Ubuntu, open a terminal and run
```

sudo grub
grub> root (hd0,7)
grub> setup (hd0,7)
grub> exit

```
The add
```

title      	Fedora
root       	(hd0,7)
chainloader +1

```
to the bottom of Ubuntu's /boot/grub/menu.lst
Reboot, and try to boot Fedora.

If you run into any trouble, please run [boot_info_script]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and post the RESULTS.txt file here.

---

### Post by ouker on 2009-08-09
May be what you need to do is edit /boot/grub/menu.lst in Fedora, and add ubuntu to the menu list ! You can find your ubuntu boot command from the partition ubuntu installed or from the Internet

---

### Post by running_rabbit07 on 2009-08-09
> **unutbu said:**
> Okay, then try this:

Boot Ubuntu, open a terminal and run
```

sudo grub
grub> root (hd0,7)
grub> setup (hd0,7)
grub> exit

```The add
```

title          Fedora
root           (hd0,7)
chainloader +1

```to the bottom of Ubuntu's /boot/grub/menu.lst
Reboot, and try to boot Fedora.

If you run into any trouble, please run [boot_info_script]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and post the RESULTS.txt file here.

That worked, Thank you yet again.

---

