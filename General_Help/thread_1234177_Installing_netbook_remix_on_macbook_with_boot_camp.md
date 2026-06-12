---
title: "Installing netbook remix on macbook with boot camp"
date: 2009-08-07
forum: General Help
---

### Post by mk12 on 2009-08-07
Hi, I want to try out ubuntu, by installing safely with bootcamp on my Macbook. So far I downloaded the latest version of the Ubuntu netbook remix. I now have a disk image mounted on my macbook. With netbook remix you have to use a flash drive, right? I have a 2gb usb flash drive, but I'm not sure if macbook supports booting from one. Does it? If not, is there a way to put netbook remix onto a cd instead? Could someone give me some instructions on installing it with bootcamp? How much space will I need to partition for it? If I want to get rid of it later, will I be able to just un-partition the drive again and let the os x 5.7 take it all up again like normal? Thankyou!!

---

### Post by callumacrae on 2009-08-07
As far as I am aware, you cannot run Ubuntu in bootcamp. It is designed for windows only.

If you really want to run Ubuntu on a mac you should use a virtualization software. The best ones are Virtualbox (free, not as fast), Parallels (£50, Apple recommends), VMware (£50).

~Callum

---

### Post by Mighty_Joe on 2009-08-07
The UNR is only for Intel Atom-based netbooks [See Here]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks")
As for Ubuntu on MacBooks, go to [the Mac forum]("http://ubuntuforums.org/forumdisplay.php?f=328") and read the FAQ.  It will save you a lot of trouble.

---

### Post by mk12 on 2009-08-07
@callumacrae: It is designed for windows, but it also works with linux:[linux on mac with bootcamp]("http://www.helium.com/items/421906-how-to-install-linux-on-an-intel-mac-with-boot-camp"). I asked here because I'm not sure of when that was written, and that guide doesn't use a macbook, or UNR, but anyway, @Mighty_Joe, are you saying that I should be using the desktop version?

---

### Post by callumacrae on 2009-08-08
It was written in June 2007. Thanks, I never knew :)

I would assume it still works from what it says at the top.

You would be better with the desktop editing with a Macbook. I would only use the netbook remix on a 10" netbook. The Macbook is certainly powerful enough to run the full version.

I would still recommend virtualbox. You can install both versions of Ubuntu if you really want, then :)

~Callum

---

### Post by Mighty_Joe on 2009-08-09
> **mk12 said:**
>  @Mighty_Joe, are you saying that I should be using the desktop version?

I am not aware of any macbooks using the Intel Atom processor, so one cannot use the UNR.

---

### Post by gurashi on 2010-03-09
> **callumacrae said:**
> As far as I am aware, you cannot run Ubuntu in bootcamp. It is designed for windows only.

If you really want to run Ubuntu on a mac you should use a virtualization software. 

~Callum


you can get NBR on a Macbook.

I have a Macbook 2,1 and am typing from it using NBR as we speak. 

This is how i did it you can try others.

0. download REFIT from here [http://refit.sourceforge.net/](http://refit.sourceforge.net/) and install this is a EFI bootoader

1. set up a boot camp partition

2. Load up your NBR install 

3. when you get to partitioning select manual and convert the Bootcamp partition to ex3 or whatever your preference is. TAKE NOT OF THE PARTITION NAME (MINE WAS DEV/SDA3) for me i did not worry about a swap.

4. at the end of the selections for your install there is "advanced" button click that and install the boot loader on the partition that you are installing.

5. install NBR. 

6. restart and you should be able to now select a boot screen of mac osx and NBR

---

### Post by Mlabus on 2011-02-12
> **gurashi said:**
> you can get NBR on a Macbook.

I have a Macbook 2,1 and am typing from it using NBR as we speak. 

This is how i did it you can try others.

0. download REFIT from here [http://refit.sourceforge.net/](http://refit.sourceforge.net/) and install this is a EFI bootoader

1. set up a boot camp partition

2. Load up your NBR install 

3. when you get to partitioning select manual and convert the Bootcamp partition to ex3 or whatever your preference is. TAKE NOT OF THE PARTITION NAME (MINE WAS DEV/SDA3) for me i did not worry about a swap.

4. at the end of the selections for your install there is "advanced" button click that and install the boot loader on the partition that you are installing.

5. install NBR. 

6. restart and you should be able to now select a boot screen of mac osx and NBR


How does one "Load up" the NBR install?  Can it be an .ISO file?

---

