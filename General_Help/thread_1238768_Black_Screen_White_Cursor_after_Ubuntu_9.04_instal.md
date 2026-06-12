---
title: "Black Screen White Cursor after Ubuntu 9.04 install."
date: 2009-08-12
forum: General Help
---

### Post by wynncreations on 2009-08-12
Hi,
 
I recently installed the latest Ubuntu 9.04 release. Downloaded from [www.ubuntu.com]("http://www.ubuntu.com").
 
It is installed on a Dell Optiplex 320. 3.0GHz proc, 1.5GB RAM 80GB HDD.
 
I had Windows XP Pro installed and working fine. After I installed Ubuntu(after formatting HDD) I went through the install, and after the screen came up to take the CD out and restart I now get an all back screen with the blinking cursor in the tope left.
 
I tried rebooting a few times, I have tried reinstalling Ubuntu after reformatting with no changes.
 
Any suggestion as to what might cause the problem?
 
Thanks,
Robert
 
P.S. This is my first post, if I should post this elsewhere please let me know.

---

### Post by michy99 on 2009-08-12
Did you run a check on the CD to make sure it did not have any errors?

---

### Post by wynncreations on 2009-08-12
Yes I did, no errors found.

---

### Post by sailthesea on 2009-08-12
Can you type anything at the cursor? If so type xstart if desktop is loaded but not enabled you may have got a server edition by mistake
Welcome by the way:)

---

### Post by wynncreations on 2009-08-12
Ok, so wierd gig.... had the CD in the tray..rebooted chose the CD, then once on the CD menu choose to boot from hardisk...booted without issue. Odd.

---

### Post by sailthesea on 2009-08-12
So you can restart and boot into Ubuntu without the CD now?
Probably the boot file didn't update correctly after the first attempt but recovered when back in RAM with CD 
Things sometimes fix themselves and give thanks for that!

---

### Post by wynncreations on 2009-08-13
No, all it does without the CD is hit the Grub loading screen then head to the black screen with cursor. Also, if I hit exc before it auto loads and choose the Ubuntu install it still does the black screen.

---

### Post by starr0stealer on 2009-08-15
I am running into same thing, its the boot loader, you need to use Grub2 or Lilo

[https://wiki.ubuntu.com/DellOptiplex320](https://wiki.ubuntu.com/DellOptiplex320)


I haven't gotten this working just yet, I'm on the live boot part of the CD. Once I figure it out I'll post to ya.

---

### Post by starr0stealer on 2009-08-15
I have been able to get it to boot, installed Grub2

I am having issues with the network card. Doesn't seem to be giving it a driver.

I installed with these steps.

Boot into live CD (9.04), and Install. DONT REBOOT

go into term. sudo -i

mount /dev/sda /mnt
mount -o bind /dev /mnt/dev
chroot /mnt
apt-get remove --purge grub
aptitude update
aptitude install grub2
grub-install /dev/sda
update-grub


Now I'm back into the live CD, working on the network card.
ubuntu@ubuntu:~$ sudo lspci | grep net
02:09.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)



Lets see if that helps you get it installed though

---

