---
title: "how to remove grub?"
date: 2010-11-23
forum: General Help
---

### Post by sohlinux on 2010-11-23
I need to reinstall both windows and ubuntu as dual boot.

I tried to install windows 7 from the recovery partition but after windows starts the recovery and then does its first reboot it always loads to the grub prompt.

I booted with ubuntu 10.10 live cd and wiped off all the partitions except the windows recovery partition and I tried sudo ms-sys -m /dev/sda3 which is supposed to restore the windows mbr but still when I reboot it just boots to the grub command prompt with windows only partially installed.

if I completely wiped off the old ubuntu partition and the windows partition then how can grub still be loading up? where is grub located?  

any ideas how to completely remove grub. I don't have a windows recovery cd, I only have the recovery partition which is still intact.

I have tried to install ubuntu first and make an ntfs partition but when I try to install windows the recovery partition program says there is not enough space to install windows but there is 260gb.

---

### Post by sohlinux on 2010-11-23
anyone? :(

---

### Post by sohlinux on 2010-11-23
I got hold of a windows recovery cd and used bootrec.exe /fixmbr

still would be interesting to know how to do this from the ubuntu live cd. maybe the ms-sys command is only valid for older versions of windows mbr.

---

### Post by axept on 2010-11-23
There is a program called MBRfix.exe, run it in terminal in Windows. Dont remember the correct command.

---

### Post by techunit on 2010-11-23
It can be done in with a with the windows install disk I am pretty sure. I don't remember the process exactly but I am sure you can find it by searching google for restore mbr from windows recovery cd. You have the restore disk so you should be able to use graphical cues if I remember correctly. I hope this helps. Sincerely Techunit

---

### Post by bonixavier on 2010-11-23
> **sohlinux said:**
> I got hold of a windows recovery cd and used bootrec.exe /fixmbr

still would be interesting to know how to do this from the ubuntu live  cd. maybe the ms-sys command is only valid for older versions of windows  mbr.
You're not seriously asking Ubuntu to repair a Windows install for you, are you? Good riddance.

---

### Post by Quackers on 2010-11-23
> **bonixavier said:**
> You're not seriously asking Ubuntu to repair a Windows install for you, are you? Good riddance.


Like Lilo :-)

---

### Post by sohlinux on 2010-11-23
> **bonixavier said:**
> You're not seriously asking Ubuntu to repair a Windows install for you, are you? Good riddance.

 no, I am asking how to remove grub (read the question before you start being rude) It can be done in linux anyway!

---

### Post by WorMzy on 2010-11-23
Grub is installed in two places. 1) The bulk of grub gets installed to the ubuntu partition. 2) A tiny portion of it goes in the MBR, where the bios can load it.

Deleting your Ubuntu partition and (re)installing the windows bootloader to the MBR will remove all traces of grub. If grub still remains, then you haven't reinstalled the MBR correctly. Consider asking on a Windows forum for details on how to do it properly.

---

### Post by Quackers on 2010-11-23
It's a good question. And the answer is yes, it is possible to remove grub but only by over-writing it with zero's or with another bootloader afaik.
I would have expected the recovery you ran to have done that. I don't know why it didn't.

---

### Post by sohlinux on 2010-11-23
linux command ms-sys is supposed to do it but it didn't for me,  [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

anyway fixed it with bootrec.exe /fixmbr command from windows recovery cd

now I have ubuntu/windows7 dual booting again but it was impossible to install ubuntu then windows, I had to install windows then ububtu because if I installed ubuntu first windows would say there wasn't enough room even though I had created a 260gb ntfs partition. a bit of a mystery..

---

### Post by bonixavier on 2010-11-23
> **sohlinux said:**
> now I have ubuntu/windows7 dual booting again but it was impossible to install ubuntu then windows, I had to install windows then ububtu because if I installed ubuntu first windows would say there wasn't enough room even though I had created a 260gb ntfs partition. a bit of a mystery..
Windows doesn't do logical partitions.

---

### Post by sohlinux on 2010-11-23
> **bonixavier said:**
> Windows doesn't do logical partitions.

I see now, so is it possible to create an ntfs primary partition after ubuntu is installed first? if ubuntu is on /dev/sda1 is that the primary partiton? if so can it be changed..

---

