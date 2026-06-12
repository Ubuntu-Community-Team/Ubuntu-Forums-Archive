---
title: "Blank screen when booting from usb key"
date: 2010-12-12
forum: General Help
---

### Post by Foxheadz on 2010-12-12
I'm not entirely sure if this is necessarily a problem with ubuntu but. I'm trying to boot ubuntu 11.04 alpha from a usb but every time i try to i get a light grey screen with a white _ at the top and sometimes some symbols like ~ or a weird pyramide like thing repeating on the screen. for a couple seconds nothing happens but then if i click any key it makes a loud beep. I used to be able to because i installed ubuntu from a usb key. So even tho this isn't necessarily a ubuntu problem, anyone know a fix?

---

### Post by Foxheadz on 2010-12-12
Oh yeah I also tried on a different usb key and a different plug on the computer, and its an Acer aspire 1690 laptop

---

### Post by vader95 on 2010-12-12
Perhaps you could try boot options such as nomce.

On the computer I'm using now, you need to Press E at the Grub menu.  Then go to where it says silent splash, right before that, type in nomce.  If ubuntu boots, I can tell you how to make the change permanent.

---

### Post by Quackers on 2010-12-12
nomodeset is a popular one for nvidia cards

---

### Post by Foxheadz on 2010-12-12
No I just can't do anything like i select usb boot option and then blank screen

---

### Post by vader95 on 2010-12-12
if you mean from the initial boot of the flash drive, select F6, then at the beginning of the line that appears type other nomce or nomodeset.

---

### Post by Foxheadz on 2010-12-12
Ok just to make it clear here's a breakdown of what happens
1.boot computer
2.press f12 to go to boot menu
3.select usb device
4.blank screen

Edit: oh yeah right before the blank screen i see some text like syslinux and some numbers but its too fast to read

---

### Post by vader95 on 2010-12-12
ok, after seeing the syslinux, try pressing enter to see if you get to boot options like you did in 10.04 and 10.10.

---

### Post by Foxheadz on 2010-12-12
don't have enough time to its there for like half a second

---

### Post by vader95 on 2010-12-12
did you verify the checksums, maybe a bad download.

---

### Post by Foxheadz on 2010-12-12
yeah i verified the md5 i tried re making the startup disk i tried all the norm

---

### Post by vader95 on 2010-12-12
are you sure the BIOS supports booting from usb flash drive.  Perhaps a flash is in order.

---

### Post by Foxheadz on 2010-12-12
Yes like i said i installed ubuntu from a usb key, what do you mean by flash is in order

---

### Post by vader95 on 2010-12-12
sorry, i meant maybe you should flash bios to a newer version.

---

### Post by Foxheadz on 2010-12-12
Hmm not entirely sure how to do that...

---

### Post by vader95 on 2010-12-12
well, most likely you will need windows or an msdos start-up disk, i would check the pc manufacturer's website for more information.

---

### Post by Foxheadz on 2010-12-12
Hmm from what i can tell i have the newest version and also i don't think that would be the problem because again i used to be able to boot and also i can boot from cds and dvds

---

### Post by vader95 on 2010-12-12
That is just really weird that you cannot access boot options.  You say that you installed it to a flash drive, do you mean the live environment, or the full desktop.

---

### Post by Foxheadz on 2010-12-12
live environment  i used startup disk creator

---

### Post by vader95 on 2010-12-12
they must have taken that function out for 11.04.  I'll see if i can do anything over here, might take me a while though.

---

### Post by Foxheadz on 2010-12-12
Well also this isn't the first time it happened to me. the same thing happened with backtrack 4 r2 and r1

---

### Post by vader95 on 2010-12-12
how about any older forms of ubuntu.  Maybe it is just because it is still in Alpha stage.

---

### Post by Foxheadz on 2010-12-12
Well first i got the link to the iso from a site talking about make a liveusb to test bugs and secondly again it happened with an other operating system

---

### Post by vader95 on 2010-12-13
Well, here is the official Link, [http://cdimage.ubuntu.com/releases/natty/alpha-1/](http://cdimage.ubuntu.com/releases/natty/alpha-1/).

second, i find it really weird that you cannot access boot options.

---

### Post by Foxheadz on 2010-12-13
Yeah thats were i got it from. And i guess i'll just contact the computer manufacturer and see what they think.

---

### Post by vader95 on 2010-12-13
what kind of processor do you have?

---

### Post by Foxheadz on 2010-12-13
From what i can tell a Pentium III

---

### Post by vader95 on 2010-12-13
a pentium III, that seems kind of old for an aspire.  You have the minimum requirements, Right?

---

### Post by Foxheadz on 2010-12-13
Again from what I can tell yes.

---

### Post by vader95 on 2010-12-13
what ubuntu version is that picture from.

and it might be a celeron processor.

---

### Post by vader95 on 2010-12-13
I just downloaded it and put it on a flash drive, I cannot boot to it, it automatically restarts my system.

---

### Post by Foxheadz on 2010-12-13
Ubuntu 10.10 the one im running now

---

### Post by vader95 on 2010-12-13
I'm starting to think it's a bug on 11.04.  I'll see if i can file a bug report.

---

### Post by Foxheadz on 2010-12-13
Well i managed to boot of 11.04 from a dvd and again it has happened to me with backtrack 4 so i doubt it's natty's problem

---

### Post by vader95 on 2010-12-13
were you booting it from flash drive then too?  Maybe it is an image writer issue.

---

### Post by Foxheadz on 2010-12-13
Yup the same two different ones i tried

---

### Post by vader95 on 2010-12-14
Well, it has never happened to me.  It's happened to me after it gets to the boot options menu, but from there, if could fix it.

---

### Post by YongQing on 2012-01-06
hi
i just wanna check. is this ever solved? this happens to me regularly. i think it is an issue with syslinux. i get this when i'm installing crunchbang/archbang as well.

my system is an Acer D257 netbook

---

### Post by serge_o on 2012-01-07
Hi, just to confirm the bug

two possibilities.
either
1. you get a line with "syslinux XXX ... by Peter Anvin ..." and the computer hangs.

or
2. you see this line for a moment (like described in this thread) and then it disappears, blank screen, computer hangs?

if either of these two is your case then it is very likely that this thread will help (the last two posts)

[http://ubuntuforums.org/showthread.php?t=1610031](http://ubuntuforums.org/showthread.php?t=1610031)

I too had the same issue and it helped me. I might be that many current laptops (mine is HP) expect the USB stick to be an FDD/CD like with no partition table, whereas the official ubuntu program make HDD USB sticks (with partition table).



> **YongQing said:**
> hi
i just wanna check. is this ever solved? this happens to me regularly. i think it is an issue with syslinux. i get this when i'm installing crunchbang/archbang as well.

my system is an Acer D257 netbook

---

