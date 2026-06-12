---
title: "Should I use 64 bit or 32 bit?"
date: 2011-03-24
forum: General Help
---

### Post by usagiakumu on 2011-03-24
Building a new system:
AMD Athalon X2 220
2gig DDR3 ram
Nvidia GeForce 8400GS 1G GDDR3
500Gig 7200 RPM Sata3
DVD Burner
220 Watt Smart 80 powersupply

It will replace my aging Pentium 4 HT with 2Gig DDR

I have come to use a lot of 32 bit stuff:
Wine
-World of Warcraft
-Rosetta Stone
Flash
Video Game Emulators with no 64 bit counterpart

I do some light video editing mostly desktop usage and some Urban Terror. I get along great with what I have, but the machine is quite old and I am retiring it as a file server. I need to know if I need seperate 32 Bit stuff installed to run 32 bit applications. If so then I will just use the 32 bit counterpart. Can I run 32 bit Flash in 64 bit Firefox? The OS will be 10.10 until 11.04 is like a month or so old and updates have come out to fix issues I will let others complain about :). Thanks in advance.

---

### Post by pqwoerituytrueiwoq on 2011-03-24
there is a 64bit flash (google flash square) for firefox the 32bit is a bit of a pain to get working but you can do it
you can use 32bit wine on 64bit
*is doing so on lucid laptop*
your processor is 64bit so go for it and see if everything you want works

---

### Post by Hakunka-Matata on 2011-03-24
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

getlibs

---

### Post by usagiakumu on 2011-03-24
64 Bit flash is extrememly buggy according to some of my research which is why I asked if it were possible to just run 32 bit apps using the 64 bit kernel. I am not above tinkering, I just want to know if it is worth the trouble or just roll 32.

---

### Post by jerome1232 on 2011-03-24
A) When you install flash through apt-get, you get a 32-bit version of flash that uses a wrapper to let it run in a 64-bit browser

B) The 64bit version of flash is much better in my experence than using the 32-bit version with the wrapper, I really am not a heavy flash user but it hasn't failed me yet.


My suggestion is to try 64 bit for a week for yourself to determine whether it will work for you or not.

---

### Post by oldfred on 2011-03-24
I have been running the 64 bit for about 2 years and do not have any issues. I also run it on my laptop that has only 1.5GB and it works well there also. (I want same version on both machines.) Somewhere around 2GB is probably the break even between more memory use offsetting advantages of 64bit processing.

Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Essentially says if you can use the 64bit kernel you should.

Have you checked that your 220 watt power supply is large enough? Most systems now have larger power supplies, if just for future upgrades (usually video card). Only the brand name systems have little power supplies to save a few pennies.

---

### Post by Hakunka-Matata on 2011-03-24
I've installed both 32 & 64 bit 11.04 Alpha3, zero problems with either installation.

@oldfred:  can you point me to the separate /Data partition guide please sir?

---

### Post by Paddy Landau on 2011-03-24
Having used 8.04 32-bit for two years, I installed 10.04 64-bit. I did nothing special to cater for 64-bit, and everything has worked. The only hiccough has been the recent mistake that Adobe made with its (beta) 64-bit Flash; I have reverted to the default Ubuntu installation of Flash and it works fine.

I can't comment on your games, though, as I don't use the computer to play games.

EDIT: I have only 1Gb RAM.

---

