---
title: "GRUB Problem"
date: 2006-03-18
forum: General Help
---

### Post by deboring21 on 2006-03-18
Ok... I have an IBM eServer that uses SCSI drives only. When I try to install Ubuntu onto it with more than 1 HDD, I get a screen full of the word GRUB or just the word GRUB twice... then it does nothing, just sits there. I tried doing both types of install (server and normal). I was wondering if anyone has had this problem and if you found a fix... thanks.
-Ryan

---

### Post by jerrykenny on 2006-03-18
I've had this problem but it was with a debian-businesscard cd, it just would not retreive a kernel, . . . . 

but your problems different.

try booting off your install cd and type "rescue" at the boot prompt . . . . 

You'll then have to tell the rescue system what drive/partition your  root   resides on . . . . 

then try  "ls /boot"    assuming /boot isnt on a separate drive, if it is first do 

mount /dev/?  /mnt/boot

see if theres any kernels actually there . . . . . 

if there type "grub"

this takes you into the grub shell . . . . the following commands are pasted from the gentoo grub instructions . . . 

grub> root (hd0,0)          (Specify where your /boot partition resides)
grub> setup (hd0)           (Install GRUB in the MBR)
grub> quit                  (Exit the GRUB shell)

---

### Post by deboring21 on 2006-03-18
Ok, I got up to the part where I have to type "Grub." I put that in and it look a second or two and said "Error opening terminal: bterm." What should I do? And for future reference, I am using SCSI drive sda I believe its called, but how would I enter those last 3 lines with a SCSI drive?

---

### Post by jerrykenny on 2006-03-18
It looks like you cant get into the grub terminal off the Install CD

so just from the normal command line (without typing grug first)

try 

grub-install /dev/sda


Assuming you want to boot off the first scsi drive (I dont use scsi myself) and see if you get any error messages.


if that doesnt work, try 

ls /boot      and see if there is actually a kernel in there . . . .

---

### Post by deboring21 on 2006-03-18
Ok, I did that grub-install thing and it worked... but when I rebooted, I still get 2 lines of booting from CD, then the next line has the word GRUB twice... any more ideas?

---

### Post by jerrykenny on 2006-03-18
yes, boot into your "rescue" system, and enter the command

nano /boot/grub/menu.lst

this lets you edit the grub menu . . . . 

first of all, put a     #    in front of the       "hiddenmenu"

next, have a look at the actual entries for your kernel, and jot them down on a piece of paper .

Press      <Control> and <X>   together, and press<y> to save the changes to this file . . . . . 

Next, back in the terminal, type

fdisk  /dev/sda

make sure the entries here correlate with the entries in your menu.lst . . . . . and make sure that your ubuntu   /boot   partition is marked "bootable"

If you dont have a separate /boot partition, the just the ubuntu main partition.

---

### Post by deboring21 on 2006-03-18
I tried doing the nano command and I get the message "sh: nano: command not found"

---

### Post by jerrykenny on 2006-03-18
Sorry, I guess the rescue envorinment doesnt have the nano editor . . . 

try 

vi /boot/grub/menu.lst

---

### Post by deboring21 on 2006-03-18
Thanks anyways, but I have just given up on having more than one hard drive....

---

### Post by jerrykenny on 2006-03-18
Lol, no problem, its probably something annoyingly minor 'though, like the ubuntu /boot partition not being marked as "bootable" . . . . try to install on one hard -drive only (primary master) then you can add the other drive later, and make entries to your /etc/fstab file.

---

