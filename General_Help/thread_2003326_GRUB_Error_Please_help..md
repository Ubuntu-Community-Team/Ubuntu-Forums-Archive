---
title: "***GRUB Error*** Please help."
date: 2012-06-13
forum: General Help
---

### Post by colomob on 2012-06-13
I've wasted 2 days trying to fix this issue i have. I deleted the partition that had Ubuntu on it there for i lost my GRUB? Well anyhow i inserted the llive CD to help me fix this issue but when i boot it it gives me another error.

Verifying DMI Pool Data.............
Boot from CD :
error: no such partition.


What do i do?? LEt me know if i need to tell you guys anything else.

---

### Post by colomob on 2012-06-13
Im having the same issue but it does not let me boot the live CD. it gives me an Error: no such partition. what do i do in this case??

---

### Post by wilee-nilee on 2012-06-13
> **colomob said:**
> Im having the same issue but it does not let me boot the live CD. it gives me an Error: no such partition. what do i do in this case??

Use this tool to get the bootinfo summary only, and start a thread and post the HTTP address to the bootinfo.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

We don't mix individual problems together it gets to confusing, and we want you to have the best help possible. ;)

---

### Post by colomob on 2012-06-13
I already created the ISO with Boot-repair but it does not boot. it gives me the same error as before. No such partition. 


> **wilee-nilee said:**
> Use this tool to get the bootinfo summary only, and start a thread and post the HTTP address to the bootinfo.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

We don't mix individual problems together it gets to confusing, and we want you to have the best help possible. ;)

---

### Post by wilee-nilee on 2012-06-13
> **colomob said:**
> I already created the ISO with Boot-repair but it does not boot. it gives me the same error as before. No such partition.

You need to address this in your own thread.

---

### Post by wilee-nilee on 2012-06-13
> **colomob said:**
> I've wasted 2 days trying to fix this issue i have. I deleted the partition that had Ubuntu on it there for i lost my GRUB? Well anyhow i inserted the llive CD to help me fix this issue but when i boot it it gives me another error.

Verifying DMI Pool Data.............
Boot from CD :
error: no such partition.


What do i do?? LEt me know if i need to tell you guys anything else.

What is left on the hard drive?

Are you familiar with a per session boot?

Have you set the bios to read the disc first?

The live cd is a Ubuntu cd?

What is the ultimate goal here?

---

### Post by oldfred on 2012-06-14
It seems like you do not have a bootable CD. Did you burn it correctly, not copy the ISO to it? The boot process seems to be looking at CD, not working then going to hard drive and finding the hard drive error.

---

### Post by colomob on 2012-06-14
I have 3 partition. 1st, Windows Rec. 2nd, Widows 7 and third it was Ubuntu that now is empty.

I'm not Familiar with a per session boot.

yes. i have set the BIOS to read the disk first and i have tried to boot it manually. 

Yes, the live CD is a Ubuntu CD. i also have the Boot-recovery CD and Windows 7 CD. noon of them Boot.

I need to be able to use the computer on windows 7 or Ubuntu so i can run Windows 8 Beta.

> **wilee-nilee said:**
> What is left on the hard drive?

Are you familiar with a per session boot?

Have you set the bios to read the disc first?

The live cd is a Ubuntu cd?

What is the ultimate goal here?

---

### Post by colomob on 2012-06-14
YEs it burned correctly. i tried it with an old Laptop and it worked perfectly. It just seem to not work in this case. 

> **oldfred said:**
> It seems like you do not have a bootable CD. Did you burn it correctly, not copy the ISO to it? The boot process seems to be looking at CD, not working then going to hard drive and finding the hard drive error.

---

### Post by wilee-nilee on 2012-06-14
A per-session boot is a key prompt like you were going to the bios, but it is a out of the bios boot from menu.

Mine prompt is f12, yours may be different. If you find the manual on the web it will probably tell you what key or keys, or using the computer model and session boot it will be on there as well.

---

### Post by efflandt on 2012-06-14
Even if you change boot device order in CMOS setup, some computers (like my Dell laptop) still boot from hard drive first unless you press a certain key during BIOS splash screen.  On some computers that key is **F12** and others might be **Esc** (based on computers I have).

Maybe that is to avoid booting from CD or DVD that possibly has something malicious on it.  The only virus I ever caught was a boot sector virus spread by floppy disks a long time ago (Stoned Empire Monk or Monkey virus).

So see if your BIOS splash screen shows a key to press to select boot device on the fly.  For my tablet PC I actually had to enable it to even list the F12 device selection in the BIOS splash screen. If no disks boot from your CD or DVD drive, you are probably not booting the drive you think you are.

---

### Post by colomob on 2012-06-14
Mine is the same F12 to choose where to boot from and ESC to change the Order of the booting process. I've tried both ways but it keeps giving me the error or no such partition.


> **efflandt said:**
> Even if you change boot device order in CMOS setup, some computers (like my Dell laptop) still boot from hard drive first unless you press a certain key during BIOS splash screen.  On some computers that key is **F12** and others might be **Esc** (based on computers I have).

Maybe that is to avoid booting from CD or DVD that possibly has something malicious on it.  The only virus I ever caught was a boot sector virus spread by floppy disks a long time ago (Stoned Empire Monk or Monkey virus).

So see if your BIOS splash screen shows a key to press to select boot device on the fly.  For my tablet PC I actually had to enable it to even list the F12 device selection in the BIOS splash screen. If no disks boot from your CD or DVD drive, you are probably not booting the drive you think you are.

---

### Post by CharlesA on 2012-06-14
Threads merged. Please do not hijack another person's thread.

Thank you.
Charles

---

### Post by colomob on 2012-06-14
I dont know if this might help,

when i enter ls in the grub rescue it returns
(hd0) (hd0,msdos2) (hd0,msdos1)

but when i type in set, it returns as

prefix=(hd0,msdos5)/boot/grub

---

