---
title: "Installed Lucid Lynx but it won't boot up. Getting error 2 message?"
date: 2010-06-01
forum: General Help
---

### Post by Macfunky on 2010-06-01
I have just installed Lucid Lynx as, after a live run of it, i thought it was about time to upgrade. Everything ran smoothly in the live version so i backed up my files and installed it. When i went to boot i get this -

Grub loading, please wait ...
Error 2

The strange thing is it seems to be specific to the computer. I have an older, lower speced desktop, computer that i tried the hard drive in and it worked fine. Problem is its too low speced for what i want so it seems the install went ok but its something with the computer? Anyone know what could be happening and be able to help me to be able to boot into the install?

---

### Post by Macfunky on 2010-06-20
Anyone have any idea what could be wrong? Any help at all would be great. Thanks

---

### Post by stoneage on 2010-06-20
Here you go:-
[http://www.uruk.org/orig-grub/errors.html#stage1_5](http://www.uruk.org/orig-grub/errors.html#stage1_5)

> Error 2 - 'Selected disc doesn't exist'
This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

---

### Post by Macfunky on 2010-06-21
> **stoneage said:**
> Here you go:-
[http://www.uruk.org/orig-grub/errors.html#stage1_5](http://www.uruk.org/orig-grub/errors.html#stage1_5)

Do you know how i can fix the problem?

---

### Post by philinux on 2010-06-21
I would reinstall grub2 from the livecd.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Macfunky on 2010-06-23
> **philinux said:**
> I would reinstall grub2 from the livecd.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Will reinstalling GRUB solve the problem when it's only specific to one computer? The hard drive will run on all other computers i have. Any hard drive that boots up on any other computer will run into the same error on the computer in question so i'm wondering how much of a help it would be to reinstall GRUB?

---

### Post by stoneage on 2010-06-24
Did you have any other drives connected when you installed?

I read another post, I think from someone who installed from a usb (maybe)

Anyway, the point was, Grub thought the HDD was the second drive, so when the usb was removed Grub was looking for Ubuntu on /dev/sdb when it was actually on /dev/sda, obviously. Could it be something like that....?

---

### Post by Macfunky on 2010-07-22
> **stoneage said:**
> Did you have any other drives connected when you installed?

I read another post, I think from someone who installed from a usb (maybe)

Anyway, the point was, Grub thought the HDD was the second drive, so when the usb was removed Grub was looking for Ubuntu on /dev/sdb when it was actually on /dev/sda, obviously. Could it be something like that....?

Sorry for taking so long to reply. That's not the problem. I still haven't figured out what's wrong. I am using another tower at the moment with the installation so my install isn't lying idle, however, i would like to figure out why that tower specifically is doing that with any hard drive with any Linux operating system installed on it. It seems to have started out of the blue and for no apparent reason. The tower has had no modifications or peripherals attached since. I would like to get it up and running so it doesn't go to waste. I have not actually tried a windows hard drive which i will have to try to see if that boots up ok. Will report back once i have had the chance to do that. Thanks everyone. Looks like you're as baffled as me though :P

---

### Post by Macfunky on 2010-07-25
Ok i took the notion to try a hard drive with windows xp on it to see how the computer would handle that. The message from that i'm getting is -

Primary hard disk 0 not found

So it appears that the bios can't find the hard drive (bios version A03). I tried tweaking setting in the bios but nothing is making any difference. The primary hard drive is hooked up correctly and i even changed the IDE cable.

So it looks like it is a problem with the computer itself rather than grub, but is it? The thing that confuses me about this is that i was getting a grub error message but how would i be getting a grub error message if it is indeed that my hard drive isn't being recognised? Surely it is being recognised if i am getting a grub error? So where does that leave me? Anyone have any ideas on what could be going on. Computer itself is in perfect working order when i boot from a live disc.

---

