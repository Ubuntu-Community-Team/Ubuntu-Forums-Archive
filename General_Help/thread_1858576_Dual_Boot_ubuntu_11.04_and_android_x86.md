---
title: "Dual Boot ubuntu 11.04 and android x86?"
date: 2011-10-12
forum: General Help
---

### Post by rblilly on 2011-10-12
So I decided to try ubuntu 11.04 and I love it.  Much better on my little netbook than microsoft.  However, I decided I wanted android as a dual boot so that I could load some android apps.  When I search the web it appears that I am not the only one that wants to do so.  I found a spot where a guy did this, but I am having no luck.  I have both OS on the HD but when the computer boots ubuntu boot loader doesn't recognize android because the android is grub, and ubuntu is grub2.  Or at least that is what I make of it after reading. So below I will show what the file looks like for android, and what I tried to make it in ubuntu.
[B]
Android grub file looks like this[/B].

 [FONT=&quot]default=0
timeout=6
root (hd0,6)
splashimage=/grub/android-x86.xpm.gz

title Android-x86 2.2 (HDPI)
    kernel /android-2.2/kernel quiet root=/dev/ram0 androidboot_hardware=generic_x86 acpi_sleep=s3_bios,s3_mode video=-16 DPI=240 SRC=/android-2.2
    initrd /android-2.2/initrd.img

title Android-x86 2.2 (MDPI)
    kernel /android-2.2/kernel quiet root=/dev/ram0 androidboot_hardware=generic_x86 acpi_sleep=s3_bios,s3_mode video=-16 DPI=160 SRC=/android-2.2
    initrd /android-2.2/initrd.img

title Android-x86 2.2 (Debug mode)
    kernel /android-2.2/kernel root=/dev/ram0 androidboot_hardware=generic_x86 acpi_sleep=s3_bios,s3_mode video=-16 DEBUG=1 SRC=/android-2.2
    initrd /android-2.2/initrd.img[/FONT]


**[FONT=&quot]So I tried sudo /etc/grub.d/40custom[/FONT]**
**[FONT=&quot]Then I entered this into it[/FONT]**
[B][FONT=&quot]
[/FONT][/B]
  [FONT=&quot]menuentry "Android-x86 2.2 (HDPI)" {
set root=(hd0,6)
linux /android-2.2/kernel quiet root=/dev/ram0 androidboot_hardware=generic_x86 acpi_sleep=s3_bios,s3_mode video=-16 DPI=240 SRC=/android-2.2 [/FONT]
  [FONT=&quot]initrd /android-2.2/initrd.img
}[/FONT]
  [FONT=&quot]
menuentry "Android-x86 2.2 (MDPI)" {
set root=(hd0,6)
linux /android-2.2/kernel quiet root=/dev/ram0 androidboot_hardware=generic_x86 acpi_sleep=s3_bios,s3_mode video=-16 DPI=160 SRC=/android-2.2
initrd /android-2.2/initrd.img
}[/FONT]
  [FONT=&quot]
menuentry "Android-x86 2.2 (Debug mode)" {
set root=(hd0,6)
linux /android-2.2/kernel root=/dev/ram0 androidboot_hardware=generic_x86 acpi_sleep=s3_bios,s3_mode video=-16 DEBUG=1 SRC=/android-2.2
initrd /android-2.2/initrd.img[/FONT] 
  [FONT=&quot]}[/FONT]


[FONT=&quot]I get a couple of errors when I do this, but I am not sure what I am entering wrong, or what I am doing wrong.  I am way new to Linux so I haven't a clue where to begin or how to make this thing dual boot with the OS that I want to have.  
[/FONT]


[FONT=&quot]HELP!
[/FONT]

---

### Post by rblilly on 2011-10-12
bump!

---

### Post by rblilly on 2011-10-12
another bump for the day

---

### Post by rblilly on 2011-10-18
Nobody knows how to do this?

---

### Post by rblilly on 2011-10-18
bump

---

### Post by bornagainpenguin on 2011-12-12
I found this thread after googling around to see if anyone else were trying to do this on a computer already running Ubuntu.  Sad to see how little attention this thread has seen.  Will probably wait until I decide to do a reinstall of Ubuntu or if I move to a different distro before attempting this now.  :(

--bornagainpenguin

PS: Consider this a free bump

---

### Post by 3togo on 2011-12-18
1. use ubuntu livecd boot 
2. locate the android grub menu.lst file

eli@3ToGo-One:~$ cat /media/Android-x86/grub/menu.lst 
default=0
timeout=6
root (hd0,1)
splashimage=/grub/android-x86.xpm.gz

title Android-x86 2011-11-13
	kernel /android-2011-11-13/kernel quiet root=/dev/ram0 androidboot_hardware=eeepc acpi_sleep=s3_bios,s3_mode SRC=/android-2011-11-13 SDCARD=/data/sdcard.img
	initrd /android-2011-11-13/initrd.img

3. chroot to your ubuntu in your hard drive /dev/sdaX
3. modify the above few lines and add it to /etc/grub.d/40_custom

eli@3ToGo-One:~$ cat /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Android-x86 2011-11-13" {
	set root='(hd0,msdos2)'
	linux /android-2011-11-13/kernel quiet root=/dev/ram0 androidboot_hardware=eeepc acpi_sleep=s3_bios,s3_mode SRC=/android-2011-11-13 SDCARD=/data/sdcard.img
	initrd /android-2011-11-13/initrd.img
}

4. sudo update-grub

---

