---
title: "Trying to put my old Windows rip onto USB"
date: 2010-08-08
forum: General Help
---

### Post by MapleAwesome12 on 2010-08-08
I got my USB stick edited for WinXP. Now I'm wondering how I edit my BIOS to boot the USB. I don't want to use WINE to emulate a BIOS editor made on Windows. Is there any BIOS editor made to work on Linux?

OLD POST: So, a long time ago, I made my own ISO of WinXP from my install disc and saved it onto my second hard drive. I installed Ubuntu when my brother eventually threw out my WinXP install disc. I was angered, but after looking around my hard drives recently, I found the ISO. Now, I'm wondering, how do I make a USB thumbdrive act as a bootable one, like for Ubuntu, but instead of making a bootable USB of Ubuntu while under Windows, a bootable USB of Windows under Ubuntu. I really like Ubuntu, but I have certain things that Ubuntu isn't pleasing, and I simply want to get Windows under as dual-boot.

---

### Post by kman269 on 2010-08-08
I'm sure if you want  to but from the usb as if you were booting from the windows installation cd or as if your booting onto windows but if you want to but it as if you are booting from the installation cd, [http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/) should be helpful.
it mentions putting a bootable iso image onto a flash drive by first mounting your usb drive then finding where the drive is using the following command ```
dmesg | tail
```
and then using the following command to copy it over
```
dd if=<location_of_iso> of=/dev/sdb ibs=4b obs=1b conv=notrunc,noerror
```

if you want it the same as if you were booting into windows then I don't really know how to help you there.

---

### Post by MapleAwesome12 on 2010-08-08
kman269, I couldn't exactly understand what you said. But I see you linked to a site where I could run Windows from a disc. I actually want to use it as an actual Install disc. I ripped the install disc in the first place so that if I ever lose the official install disc, I still have it as a backup.

---

### Post by kman269 on 2010-08-08
oh god I looked back over my last post and I have no idea what I was thinking, it was hard for me to even make out what I was trying to say.

I'm not sure why you can't just burn the image to a cd because that is extremely simple and is cheaper than a usb.

Also I don't see what is wrong with the site that I linked to. If you just press ctrl+f and do a search for the term "bootable flash drive" it should take you to what you are looking for. The only difference I see is it is describing how to put a linux distro's cd onto a usb instead of a windows cd but it should work in the same manner.

If still none of this is helpful or comprehensive, I'm sorry I wasn't very helpful but I can't do anything else.

---

### Post by MapleAwesome12 on 2010-08-09
Well, I can't use CD because I have no CD-Rs, as well as the fact that none of these burning programs will work with my CD drive. Yes, it can burn CD-Rs, it just never works..

I think I may have already gotten it worked out. I checked the device in Disk Utility, and it read as ISO9660, the disc format for most install discs, so I think I'm covered on the device part.

My next problem is editing the BIOS to allow booting removable devices, such as this USB. I don't know how to edit the BIOS while in Linux. I don't wanna use WINE to emulate any programs that can edit the BIOS. I want a program that has been open-sourced or was developed for Linux so I can assure myself that I'm editing the BIOS correctly.

---

### Post by Mark Phelps on 2010-08-09
I don't believe that there is a way to set or change BIOS options from inside Linux.

You would have to boot into the BIOS setup page -- and that it done by pressing a key when you first boot.  Typical such keys include Del, Esc, F1 -- but the actual key depends on your machine.

If your BIOS offers no option to boot from USB, there is no way for you to add it -- apart from rewriting the BIOS yourself.  And even then, you'd require a PROM burned to create a new BIOS chip.

---

### Post by MapleAwesome12 on 2010-08-09
> **Mark Phelps said:**
> I don't believe that there is a way to set or change BIOS options from inside Linux.

You would have to boot into the BIOS setup page -- and that it done by pressing a key when you first boot.  Typical such keys include Del, Esc, F1 -- but the actual key depends on your machine.

If your BIOS offers no option to boot from USB, there is no way for you to add it -- apart from rewriting the BIOS yourself.  And even then, you'd require a PROM burned to create a new BIOS chip.
You're slightly wrong there. Windows users can actually edit the BIOS while in Windows, and can add USB support.

Besides, why would I be asking how to edit the BIOS if I hadn't already tried messing with thje BIOS settings at the start of the system?

---

### Post by Mark Phelps on 2010-08-13
> **MapleAwesome12 said:**
> You're slightly wrong there. Windows users can actually edit the BIOS while in Windows ...

Yeah ... I already KNOW that!  There are BIOS edit utilities readily available that can be run from inside MS Windows.  I have a ASUS board and have used their such utility.

What part of my response that said "from inside Linux" was not clear?

---

