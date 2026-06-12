---
title: "Move grub to root partition on software raid"
date: 2009-09-05
forum: General Help
---

### Post by JohnFante on 2009-09-05
I am running 9.04 alternate. The reason is that I am using software raid and have a dualboot with Windows 7.

At present grub is installed to the MBR and works fine. I would like to move it to the boot partition but I am a bit unsure how to do that safely. The reason for moving GRUB is that I am considering replacing Windows 7 (it is the RC) and I would like to be able to do that without worrying about grub.

I have searched a lot but haven't found the solution for a system with software raid.

The boot entry on my menu.lst looks like this:

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=/dev/mapper/isw_decaaghjda_Volume03 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic

How do I tell grub to install itself on my root partition? 

Thank you in advance.

---

### Post by hal10000 on 2009-09-05
i see your / is on (hd0,2) resp. in linux notation /dev/sda3 , is this correct?
If so, then yo have first to run grub: [COLOR="Red"]sudo grub[/COLOR]
Then, on the grub prompt type in: [COLOR="Red"]setup (hd0,2)[/COLOR] if you want it in the boot record of /dev/sda3. you can exit from grub with [COLOR="Red"]quit[/COLOR]

---

### Post by JohnFante on 2009-09-05
> **hal10000 said:**
> i see your / is on (hd0,2) resp. in linux notation /dev/sda3 , is this correct?
If so, then yo have first to run grub: [COLOR="Red"]sudo grub[/COLOR]
Then, on the grub prompt type in: [COLOR="Red"]setup (hd0,2)[/COLOR] if you want it in the boot record of /dev/sda3. you can exit from grub with [COLOR="Red"]quit[/COLOR]

I am not sure. I have tried to find out with "find /boot/grub/stage 1" in grub (after sudo grub) but I get a error "Error 15 - file not found".

I think this is related to the fact that I am using software raid but I am not sure. In gparted I can see my root partition has the path "/dev/mapper/isw_decaaghjda_Volume03"

"blkid" gives me this:

/dev/mapper/isw_decaaghjda_Volume01: UUID="B0B889F8B889BCFA" TYPE="ntfs" 
/dev/mapper/isw_decaaghjda_Volume02: UUID="00BC0B10BC0AFFC0" TYPE="ntfs" 
/dev/mapper/isw_decaaghjda_Volume03: UUID="65b4d03f-aea5-43eb-a3fc-7dcd37898aaa" TYPE="ext4" 
/dev/mapper/isw_decaaghjda_Volume05: UUID="36f52b79-1615-4a03-84d8-364023b0f52e" TYPE="ext4" 
/dev/mapper/isw_decaaghjda_Volume06: UUID="a2167ceb-ba9b-4ee4-9950-66f10a5a6958" TYPE="ext4" 
/dev/mapper/isw_decaaghjda_Volume07: UUID="7f4e80f4-7cb2-4bde-9189-26ed28f78ccc" TYPE="ext4" 
/dev/mapper/isw_decaaghjda_Volume08: UUID="4482532c-391b-4126-b935-6951eddd58a3" TYPE="swap" 
/dev/mapper/isw_decaaghjda_Volume09: UUID="d768ac00-ec29-4229-90dc-9437a7f510b5" TYPE="ext4" 
/dev/mapper/isw_decaaghjda_Volume010: UUID="13169d93-83ee-4333-a87e-9adf89c84da7" TYPE="ext4" 
/dev/mapper/isw_decaaghjda_Volume011: UUID="3d7f1405-1d3c-4ebf-98ae-a018467c307c" TYPE="ext4"

---

### Post by hal10000 on 2009-09-05
Yes, might be the error is related to the raid configuration. But i'm sorry i don't have much experience with raid

---

### Post by JohnFante on 2009-09-06
Bump! Anybody else?

Thank you in advance!

---

