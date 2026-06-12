---
title: "I know I will get sniped for asking..."
date: 2009-07-09
forum: General Help
---

### Post by Vagas Lupus on 2009-07-09
My girlfriends new (used) PC has unbuntu linux as its OS and she wants Vista installed. I can not seem to get the cd to install. Being new to the "Unbuntu" world, what am I doing wrong?

---

### Post by philcamlin on 2009-07-09
is it an error or is it just the the cd wont boot

---

### Post by nacho32 on 2009-07-09
make sure you boot off the cd first not the hard drive , the settings are in the bios choose cd first

---

### Post by milton1 on 2009-07-09
Can you give us more detqailed description of what is going wrong? Will the cd boot? Do you get any error messages? Need more info in order to help.

---

### Post by philcamlin on 2009-07-09
if its cd go into bios and click boot from cd but if its it wont install format the hdd with gparted 
on the ubuntu live cd thenn try again :popcorn:

---

### Post by Vagas Lupus on 2009-07-09
OK, I load the cd, and try to boot from Bios, but the keyboard will not activate and register my commands until the startup bar in in progress.

I tried loading from the terminal but can't seem to get the commands right.

Does this help?

---

### Post by dhughes on 2009-07-09
Nah we don't snipe, we try our best to act civilized around here or things will go downhill fast, the forums are quite nice and pretty much free of attacks.

 Well usually the way it goes, the easiest way, is Windows is installed first and Linux on second, but as some have stated that's not carved in stone but as a new user you don't really want to begin your Linux journey by messing with GRUB.

 Wipe the drive using the Ubuntu Linux LiveCD choosing Gparted partition editor to wipe and create the partitions; 40GB Vista NTFS partition then for Linux a 1 or 2GB swap partition, maybe a 30GB root (/) ext3 or ext4 partition and the rest of the space an ext3 or ext4 /home partition then I'd say try Windows first, get it set up and then install Linux (if you make the Linux partitions during manual setup choose the partitions you made for Linux).

  Or just wipe the drive and then continue on with the install and let the installer choose what partitions to use and how to set them up.

 Although I have never used Vista I'm not sure how it acts in a dual boot situation.

> OK, I load the cd, and try to boot from Bios, but the keyboard will not activate and register my commands until the startup bar in in progress.

I tried loading from the terminal but can't seem to get the commands right.

Does this help?

 If you put the CD in and reboot it should start on its own and go to the LiveCD desktop you shouldn't have to do anything until you see the Ubuntu Gnome desktop.

---

### Post by philcamlin on 2009-07-09
so you cant even click install wen the cd boots?

---

### Post by John Private on 2009-07-09
I am new to Ubuntu too. From the best I know turn on the Laptop put the CD in and wait for the Laptop to identify it once it is hold the power off button until the screen goes black then turn it on and from there it should boot from the CD automatically. Good Luck

--John

---

### Post by t4thfavor on 2009-07-09
If your using USB keyboard, you may have to enable usb keyboards in the bios, I have a P$ machine that will not work without first going into bios with a regular PS2 kb and enabling USB.
This is especially annoying whn the cmos battery dies.

---

### Post by Vagas Lupus on 2009-07-09
OK, Thax everyone, I'll give these all a try and see what happens, knowing my luck, I will crash her new computer and have to take it to the Geek Squad or something! LOL

---

### Post by Vagas Lupus on 2009-07-09
I Don't know what MOJO you all have but it started loading from the CD this time!! I guess I just needed some encouragement! Thanx Everyone, You just got me some "ALONE" time! LMAO

---

### Post by sXeChris on 2009-07-09
What you're doing wrong is taking off Ubuntu. *snipes*

---

### Post by DeMus on 2009-07-09
It looks to me your USB keyboard does not function during boot. Try to get an old keyboard with cable and ps2 connector. Connect this to your computer and you should be able to enter bios (either with F1, F8, or DEL) to change the boot order. Make boot form CD the primary boot.
Put in your Windows CD/DVD and in Bios save what you have changed and exit. PC will boot now from the CD/DVD.

Even better: convince your girlfriend to keep using Linux, she won't regret it.

---

