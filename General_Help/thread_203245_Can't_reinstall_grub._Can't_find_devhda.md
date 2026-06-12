---
title: "Can't reinstall grub. Can't find /dev/hda"
date: 2006-06-24
forum: General Help
---

### Post by Singee15 on 2006-06-24
i installed windows xp and it killed grub as expected.

In the process of installing windows i deleted my swap patition because i was at the limit for the number of partitions, not sure if that is relevant or not.

So, i used the ubuntu alternative disc to boot into the system and I have a shell prompt.

Anyway, i try grub-install /dev/hda and it says "/dev/hda: not found or not a block device" and this is the same for /hdb, hd0, and a whole bunch of other options i tried. I also tried grub-install --recheck /dev/hda and it still says the same thing.

my /boot/grub/device.map file just has "(fdo)    /dev/fd0". I imagine that this is my problem, i need /dev/hda in there because apparently it doesn't see it or something. Any ideas??

Thanks a lot!

---

### Post by adwait on 2006-06-24
Dumb suggestion but are you sure you have an IDE disk? If its a SATA disc, it would e /dev/sda....

What does sudo fdisk -l say?

---

### Post by Singee15 on 2006-06-24
[QUOTE=adwait]Dumb suggestion but are you sure you have an IDE disk? If its a SATA disc, it would e /dev/sda....

What does sudo fdisk -l say?[/QUOTE]

I am using a laptop, it is IDE. and even if it were my deviced only show fd0 so i would have the same problem

Any other ideas??

---

### Post by Chribu on 2006-06-25
I had the same problem trying to reinstall grub
fixed it like this:
[http://www.ubuntuforums.org/showthread.php?t=203097]("http://www.ubuntuforums.org/showthread.php?t=203097")

---

### Post by Singee15 on 2006-06-25
My menu does point to the right place, the problem is that I can't even install grub. Grub isn't there because install-grub /dev/hda doesn't work.

Anyone else please have an idea?

---

### Post by incubus on 2006-06-25
What does
```

$ sudo fdisk -l

```

give you?

incubus

===
Edited to avoid confusion.

---

### Post by mlind on 2006-06-25
You usually install grub on MBR so use device name, not a partition. 
It's grub-install /dev/hda, /dev/sda or similar.

But don't try grub-install blindly on every hdd you have, 
only on device which is first on boot order.

---

### Post by Herman on 2006-06-25
You should be able to [Re-install GRUB ]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub")to your MBR (*be sure to scroll down in htat link to see how to use the 'alternate cd's rescue mode*), if there isn't some kind of MBR protection program in your BIOS that is blocking writing to MBR. Check your BIOS and turn off any antivirus or MBR protection options you may have running in your BIOS. A [boot sector virus ]("http://kb.iu.edu/data/ahll.html")can load in memory on every start-up and substitute its own code to your MBR, so some antivirus programs may adopt the tactic of displaying virus-like activity themselves and load in your memory to beat the bootsector virus and protect the MBR and re-write the MBR. Check what other software you have running and try turning off your antivirus stuff just for now. > But don't try grub-install blindly on every hdd you have, only on device which is first on boot order. Yes, that's right, only install GRUB to either your MBR or the first sector of your Ubuntu partition. I don't know if it's possible to install GRUB to the first sector of Windows or not but I would not want to try that, it would probably 'bork' Windows! So check your partition numbers first!
You can write GRUB to a floppy disk by doing this [Re-install GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub") and typing (fd0) after the prompt and press 'Enter' with a good floppy disk in your floppy drive.
You can install GRUB to the first sector of your Ubuntu partition by typing the correct partion number for Ubuntu (hdax) after the prompt you end up at here, [Re-install GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub") and boot with GAG Boot Manager if you cannot install GRUB to MBR. 
GAG Boot Manager is free and it's only a small download, it runs from floppy or CD, or can be installed to MBR (normally). [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm") for more info.
I hope I'm being helpful, Regards, Herman :D

---

### Post by Singee15 on 2006-06-28
[QUOTE=mlind]You usually install grub on MBR so use device name, not a partition. 
It's grub-install /dev/hda, /dev/sda or similar.

But don't try grub-install blindly on every hdd you have, 
only on device which is first on boot order.[/QUOTE]

I think this is getting a little side tracked. I know how to reintall grub. What i am saying is that it isn't working. My MBR is on hda, I know this because i have done it before. I ran the last 2 versions of ubuntu. It just isn't working this time.

see what i said in my first post:
[QUOTE=Singee15]Anyway, i try grub-install /dev/hda and it says "/dev/hda: not found or not a block device"[/QUOTE]
I am just not sure why is can't find my /dev/hda

---

### Post by Singee15 on 2006-07-02
Any thoughts?

---

