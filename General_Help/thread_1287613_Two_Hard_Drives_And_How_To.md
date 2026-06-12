---
title: "Two Hard Drives And How To"
date: 2009-10-10
forum: General Help
---

### Post by Gliderfm on 2009-10-10
I am a totally newborn baby in the Linux world. Please don't dislike me because I've been in the Windows world for over 20 years. I've been wanting to learn this O.S. for a long time but untill recently I've never had the time. I've slowly been trying out Jaunty on my old 386 machine just to famillarize myself with it!
 
Here's the Rub. I have a i7 machine with of course Vista on it and I am getting ready for Win 7. That's not going to help me much with what I want to do here. I had a corrupted hard drive on my old XP machine and this gave me the oppertunity to replace the H.D. so I thought why not have two and put Ubuntu on one. No problem there using the Grub boot loader.
 
But here's the new problem. I want to do the same thing with the i7 machine and the thought of messing it up terrifies me. Much too big an investment. I will be waiting on Karmic to be available at the end of the month. Right along with Win 7.
 
So the simple guestion is how can I keep the Win 7 bootloader and have Ubuntu run on my 2nd hard drive. This link explains what I want to do but on the new platform.
[http://www.linux.com/archive/articles/113945?tid=49&theme=print](http://www.linux.com/archive/articles/113945?tid=49&theme=print) :confused:

---

### Post by delcypher on 2009-10-10
It probably best if you install Ubuntu after installing windows7.

What you want to do is setup GRUB (boot loader) on the hard drive you boot off and then have entries in your /boot/grub/menu.lst for your two operating systems.

Problem (I think) is if you ever remove your ubuntu hard drive, you won't be able boot into windows because the grub files are on the ubuntu hard drive (I think).

A possible way out of this might be to have two MBRs (Not sure if this would work - would need bios that supports choosing the boot hard drive)

1. Install windows 7 on your first hard drive (the one you boot off).
2. Set your 2nd hard drive as the one you want to boot off in your BIOS and then install Ubuntu telling it (the menu option isn't that obvious) to install the GRUB bootloader to your 2nd hard drive (if your BIOS doesn't support it you could physically swap your drives round)
3. Add an entry to /boot/grub/menu.lst for Windows7 on the other drive (Chain load) -- I'M NOT SURE IF CHAINLOADING to another MBR would work!
4. Try it out... Hopefully your ubuntu install will be completely on the 2nd drive (including the bootloader) 


Have a read of this and see if it helps
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

Although things might get a little complicated as Ubuntu 9.10 (Karmic) uses GRUB2 which I know nothing about.

Can someone else comment on this because I'm not sure if my suggestions would work.

---

### Post by nikhilbhardwaj on 2009-10-10
just before installing ubuntu
unplug your first hard drive
after installation plug it back in


it will be even easier
if you install grub to (hd1) while installing ubuntu
in the expert mode

---

### Post by Gliderfm on 2009-10-10
Thanx Nik,
 
Sounds too easy. Sure it'll work? I think that's what I tried on my old box and it didn't work out that way.
although like I said this is a new platform on the new box. This is why I need all the help I can get. Will I
have to use the bios to boot each hard drive?

---

### Post by delcypher on 2009-10-10
I'm not 100% sure it'll work but Nik is right, you won't screw up your Windows install if you unplug the hard drive it's on before you start the ubuntu install (do make sure your pc if off before you unplug your hard drive ;-) ).

You don't have to remove the drive but the problem is most people miss the "advanced menu" whilst installing ubuntu (see picture below). The default is to write the MBR to the first drive (which will be your windows one).
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=112243&d=1241334255[/IMG]

So far looks like the consensus is.

1. Install windows7 onto hard drive 1, reboot make sure your machine can boot into windows7
2. Unplug hard drive 1 and make sure hard drive 2 is plugged in
3. Install ubuntu, reboot make sure you can boot into ubuntu
4. Plug both hard drives in, your machine will most likely now boot into windows7 as it is installed on your first hard drive and that is usually the first drive. If it boots straight to ubuntu then skip to step 6.
5. Either change BIOS setting to boot off other drive (ubuntu drive) or swap data cables round.
6. Boot into ubuntu and check you can see your windows hard drive from ubuntu.
7. Add a "Window" entry to /boot/grub/menu.lst (for older versions of ubuntu)

With this setup you will be booting off your ubuntu drive but GRUB will present you with an option to start windows instead if you add a menu option for it. Doing everything this way has the advantage that it will preserve the MBR on your windows drive so if something goes wrong with ubuntu you can still boot into windows by changing the bios settings or by unplugging your ubuntu drive.

Unfortunately ubuntu 9.10 switches to GRUB 2 which works differently ( I know you need to modify grub.cfg instead, but that's all I KNOW! So I don't know how easy stage 7 will be for you.

You will need to look into configuring GRUB2

---

### Post by DJonsson2008 on 2009-10-10
What Motherboard / Bios do you have?


Some bios have a boot selector, on mine machines
here its simply press F12 when booting. 

From there I can select USB, CD or whatever
HD I want to boot on. No need to mess with
Grub w/ 2 drives. Check your bio for this
feature.

Whatever the case if you have 2 drives, be
sure to unplug the other drive when installing
the other OS.

---

### Post by Gliderfm on 2009-10-11
Thanx everyone but as I've read numerous times everyone says to use Grub as my bootloader. This I understand since this is what I did to my old machine. XP HD1 and
Jaunty on HD 2. Please take a couple minutes to read the link on my thread start at the top of the page. It's curious since xp is on the master and JJ is on the slave.
But SATA doesn't have the master/slave config. I'm trying to use windows BCD on HD 1 with a win 7 boot promp for ubuntu on HD 2.

---

### Post by oldfred on 2009-10-11
I think you want to reverse that as the final result.

Install windows and make sure it works on hard drive. Then in BIOS switch hard drives. Install Ubuntu normally, it will add a menu entry for Windows and not overwrite the MBR on the windows drive as Ubuntu is not the second drive. 

If you want to only boot windows you can change the order in BIOS or using f12 (or whatever key in post) to boot windows Hard drive since the windows boot is still in that hard drive's MBR.

---

