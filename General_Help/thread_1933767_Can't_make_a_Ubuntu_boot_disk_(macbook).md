---
title: "Can't make a Ubuntu boot disk (macbook)"
date: 2012-03-01
forum: General Help
---

### Post by saiare on 2012-03-01
I am trying to make a boot disk for my newly built computer and completely failing- desperately, desperately need some help.

Using a macbook to write it. Neither CD or USB will work. On my macbook I am getting an error that says the disk is invalid/computer can't read it. On my new build, when I try to boot via usb I am getting the error 'isolinux.bin missing or corrupt.

I've followed the instructions on the ubuntu site down to a T, as well as googling various videos and help forums and trying all of those suggestions too (none of which have been successful)

I've made about 20 cd's and am trying the USB via terminal for about the 25th time today right now. 


 Out of blank cd's so that's no longer an option. My only chance now is of getting the USB thing going. Am absolutely at my wits end on what to do to make this work =(.

---

### Post by jerome1232 on 2012-03-01
Have you verified that the iso your working with is good? Try torrenting the iso to ensure good data integrity.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

I was going to suggest checking the md5sum but they don't seem to have them up anywhere on ubuntu.com that I can find anymore...

---

### Post by NoBugs! on 2012-03-07
I noticed the same problem, I "uninstalled" refit on mac side with sudo mv efi oldefi, then booted up holding shift, restarted the computer normally, tried booting holding c (didn't work), then booted up with Alt held, and selected to boot EFI CD, and it booted! I "reinstalled" refit by renaming folder, mv oldefi efi, and it works great :)

---

