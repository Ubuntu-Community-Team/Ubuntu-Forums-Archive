---
title: "Ubuntu 11.10 installer won't start"
date: 2012-03-22
forum: General Help
---

### Post by Hariharakadan on 2012-03-22
After burning the iso to a disc and restarting the computer with the disc in the dvd tray I get this message. " error: "prefix" is not set " then it flashes to a crude menu where none of the menu items work. Verify disc / Install Ubuntu

Things I have tested to verify the integrity of the burn:

Software - Burned the image with two different programs. UltraISO and imgburn.

Hardware - My own dvdrw and a external dvd both resulted in the above message. But when I inserted the same disc that didn't work on my pc into another dvd drive on a totally different pc it worked.

The drive was tested inside of another pc completely different from the one I have and it works flawlessly. (installer not erroring out)

ISO: Md5 hash check came back correct. The image works correctly in Virtual Box on this machine. The i386 version works as expected on this machine but not x64.

Media : Verbatim / Memorex
Passed the built in integrity test for the copies I did make. Within Virtual Box and on a PC that can run the installer without any problems.

Motherboard: Biostar TA75M+
Ram : Gskill 4 gigabytes
CPU : AMD A8-3850
DVD RW drive: Asus DRW-24B1ST
ISO: I am trying to use: ubuntu-11.10-desktop-amd64

Here is a detailed list of everything on this pc:
[http://pastebin.com/0aeEDzqc](http://pastebin.com/0aeEDzqc)

---

### Post by holytree on 2012-03-22
hmm...are u sure ur comp is 64bit ?? 

By the way why dont u try the i386 it works with almost all  pcs...

,
holytree

---

### Post by DS McGuire on 2012-03-22
> **holytree said:**
> hmm...are u sure ur comp is 64bit ?? 

By the way why dont u try the i386 it works with almost all  pcs...

,
holytree

Yeah his CPU is 64 bit. 

Make sure all the files are on there, or try booting from a USB stick.

---

### Post by Hariharakadan on 2012-03-22
The AMD A8-3850 does have support for 64 bit. [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103994](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103994)

---

### Post by Hariharakadan on 2012-03-22
Yep they are all on there to. I even tried a completely different machine to burn the ubuntu 11.10 discs, but they all had the same outcome.(black screen with grub at the top and error: "prefix" is not set) I even burned FreeBSD on both machines and the installer for FreeBSD worked fine for those. 

-Probably worth noting to that the other machine that I used in this process is 64 bit enabled as well.

---

### Post by DS McGuire on 2012-03-22
Why don't you try a USB stick? You seem to have a lot of problems with the discs...

---

### Post by Hariharakadan on 2012-03-22
Not a bad suggestion DS McGuire. I may give that shot and if it works I guess I will be RMA'ng a dvd drive later today.

---

### Post by Hariharakadan on 2012-03-22
I tested the asus dvdrw in another pc using the same disc and everything and it worked.

-I just downloaded the i386 version last night and burned it this morning. It worked out of the box. So something about the x64 version and my hardware is causing the problem. But for now the i386 version will work.

---

### Post by Hariharakadan on 2012-05-07
I just found the solution to why none of the linux installers would work on the TA75M+ biostar motherboard. So in case anyone runs into a familiar problem here it is. Check the boot priority: Mine was defaulted like this #1 UEFI (bios) #2 DVD/CD rom #3 HDD. I moved UEFI to #3 and it all works flawlessly.

---

