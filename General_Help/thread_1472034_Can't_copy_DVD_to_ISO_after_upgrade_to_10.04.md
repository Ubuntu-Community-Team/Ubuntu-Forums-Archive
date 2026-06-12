---
title: "Can't copy DVD to ISO after upgrade to 10.04"
date: 2010-05-04
forum: General Help
---

### Post by mb_webguy on 2010-05-04
I've been backing up some of my older DVDs to my hard drive, as they were starting to get a bit scratched.  Using 9.10, I had no problems.  After updating to 10.04 yesterday, however, every method I try to use fails after copying about 80 to 120 MB.

I'm running the amd64 version of 10.04, my optical drive is a TSSTcorp DVD+-RW TS-L632H, and I have installed libdvdcss2 from the Medibuntu repository.  I can play the DVDs just fine, but I can't copy them.

Brasero craps out with "Error while burning.  Data could not be written (Input/output error)", which based on some things I've read also pops up if data can't be *read*.  I've tried the "Save Log" button, but the log is always empty.  

dd exits with "dd: reading `/dev/cdrom': Input/output error".

dd_rescue starts showing nothing but bad blocks roughly at the same point where dd throws the I/O error, and if I run it in reverse, it starts showing bad blocks immediately.

k3b *seems* to work...  but it took nearly half an hour (which is a bit longer than it should have taken), it threw a "Problem while reading.  Retrying from sector *n*" error three times, and VLC won't play the resulting ISO, either directly or mounted.

I *would* say that it seems like a problem with copy protection, except that I have libdvdcss2 installed and I can play the DVDs just fine.  I just can't copy them to an ISO.  And it's not a matter of the discs being too scratched or a problem with the drive, since as I said I can play them just fine, and I can copy them in Windows using MagicISO.

Some of the DVDs I'm trying to copy aren't available anymore, but I'd hate to have to boot into Windows just to copy some discs since I do pretty much everything else in Linux.  So any help would be greatly appreciated.

---

### Post by jbrown96 on 2010-05-04
They are encrypted DVDs. You will need to install libdvdcss2 (or maybe 3). Not sure of the exact package name.

---

### Post by mb_webguy on 2010-05-04
As I said, libdvdcss2 is already installed.```
matt@the-tardis:~$ sudo apt-get install libdvdcss2 libdvdnav4 libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
libdvdnav4 is already the newest version.
libdvdread4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```The problem may well be due to the encryption, but if so it would be because of a problem with the associated packages, and not because I don't have them installed.

---

### Post by mb_webguy on 2010-05-05
*bump*

---

### Post by StuartN on 2010-05-05
> **mb_webguy said:**
> *bump*

Did you **sudo /usr/share/doc/libdvdread4/install-css.sh** after installing css?

---

### Post by mb_webguy on 2010-05-05
> **StuartN said:**
> Did you **sudo /usr/share/doc/libdvdread4/install-css.sh** after installing css?Yep.

---

### Post by anonymous user on 2010-06-12
I'm having the same problem but with Linux Mint 9 64bit on a Dell XPS9000/i7. Also on the computer I'm also having problems with k9copy  taking forever like 3+ hours to copy a dvd and at times the iso image when played, plays all black and no video. I'm using a 32bit version of Mint 9 on two other Del laptops with no problems.

Any suggestions would be appreciated. Brasero give no log errors when I create the log file.

---

### Post by wilee-nilee on 2010-06-12
> **anonymous user said:**
> I'm having the same problem but with Linux Mint 9 64bit on a Dell XPS9000/i7. Also on the computer I'm also having problems with k9copy  taking forever like 3+ hours to copy a dvd and at times the iso image when played, plays all black and no video. I'm using a 32bit version of Mint 9 on two other Del laptops with no problems.

Any suggestions would be appreciated. Brasero give no log errors when I create the log file.

First you posting in a old thread, start your own thread so it is easier to help.;)

---

### Post by dgeist on 2010-06-14
> **mb_webguy said:**
> Yep.

I'm in the same boat as you. With the following command:
dd if=/dev/dvd of=/root/test.iso

I get the following the the system logs:
Jun 14 16:31:05 xbmc kernel: [ 2574.674578] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 14 16:31:05 xbmc kernel: [ 2574.674591] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
Jun 14 16:31:05 xbmc kernel: [ 2574.674602] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Jun 14 16:31:05 xbmc kernel: [ 2574.674617] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 02 b8 00 00 40 00
Jun 14 16:31:05 xbmc kernel: [ 2574.674648] __ratelimit: 54 callbacks suppressed
Jun 14 16:31:05 xbmc kernel: [ 2574.707297] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 14 16:31:05 xbmc kernel: [ 2574.707310] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
Jun 14 16:31:05 xbmc kernel: [ 2574.707320] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Jun 14 16:31:05 xbmc kernel: [ 2574.707335] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 02 f8 00 00 40 00

Not sure what to think.... as little of it makes sense to me. I AM using a bluray player for the first time, but like the author, it's 10.04 on 64-bit. Would server vs. desktop install make any difference (i.e. packages left out for the server install?

Dan

---

