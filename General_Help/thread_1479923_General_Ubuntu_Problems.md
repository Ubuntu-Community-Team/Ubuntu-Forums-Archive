---
title: "General Ubuntu Problems"
date: 2010-05-11
forum: General Help
---

### Post by ZaM0 on 2010-05-11
Hello!
One year ago I decided to give it a try with Ubuntu. I used the 9.04 Live CD, but it didn't perform as expected - it gave randomly errors on boot up, the interface was disappearing and reappearing, applications closed themselves randomly and in the end it usually froze and I had to do the magic SysRQ or hard restart. I installed it then through Wubi - and it was somewhat more stable. It behaved sometimes excellent all the time until I restart, but sometimes it just crashed with an error when I boot up. When 10.04 came out, I wanted to try it out, so I burned the CD. It was the same as the 9.04 when using the Live CD and when installing it using Wubi it just fails on 25% :( I don't have any problems with Windows 7 and **another distribution like Knoppix (6.2) runs just fine and smooth from the Live CD**. No problems what-so-ever.

I haven't did any clean installation on my hard drive because I don't know if this would persist and leave me with a not working system. I still would like to address the problem from a Wubi installation or the Live CD before going for a full installation.

Here is my machine:
AMD Sempron 3300+ @2.0GHz
NVidia GeForce 7300LE 384MB
1 GB RAM DDR1 (2x512MB)
A31G PCCHIPS Mobo

And the topics I started before for more information:
[http://ubuntuforums.org/showthread.php?t=1224175](http://ubuntuforums.org/showthread.php?t=1224175)
[http://ubuntuforums.org/showthread.php?t=1233010](http://ubuntuforums.org/showthread.php?t=1233010)
[http://ubuntuforums.org/showthread.php?t=1479864](http://ubuntuforums.org/showthread.php?t=1479864)

Any ideas? Thanks in advance.

---

### Post by colorlessprism on 2010-05-11
ive noticed lately people's md5's have  not been matching up, this can cause any number of errors from install to boot failures. i had to download 10.04 three times before the  checksums matched. if your using XP (or any other windows operating  system) you need to use a  special program,[  winMD5Sum]("http://www.nullriver.com/products/winmd5sum") is open source and calculates the MD5  checksum of a file or an ISO image. if  you have verified its integrity you might try booting from the CD and  test its  integrity.

md5 is one of the most common signature  to make sure that a  file that you have downloaded is not corrupt. once  you have downloaded the the ISO, use winMd5Sum to get the checksum of the file on your  computer. hen  make sure that the checksums match. if they do, then your file is  exactly the same on your computer as it was/is on the server. tt is a  very good idea to  run an md5 hash  comparison check when you have a file like an operating  system install  CD that has to be 100% correct.

[http://releases.ubuntu.com/10.04/MD5SUMS:](http://releases.ubuntu.com/10.04/MD5SUMS:)
a54366aa72d6b576ee8fc0215f8a13b9 *ubuntu-10.04-alternate-amd64.iso
5b2dadacfd692b4f2d5c7cf034539262 *ubuntu-10.04-alternate-i386.iso
3e0f72becd63cad79bf784ac2b34b448 *ubuntu-10.04-desktop-amd64.iso
d044a2a0c8103fc3e5b7e18b0f7de1c8 *ubuntu-10.04-desktop-i386.iso
0b0e0d36050d9980ec995262eb9f2e6b *ubuntu-10.04-netbook-armel+dove.img
9e0d6ac7b69bb7912d49369a6807e39d *ubuntu-10.04-netbook-armel+imx51.img
712277c7868ab374c4d3c73cff1d95cb *ubuntu-10.04-netbook-i386.iso
8ee25c78f4c66610b6872a05ee9ad81b *ubuntu-10.04-server-amd64.iso
15342636441181f7a19c65984b44e24c *ubuntu-10.04-server-i386.iso
e81f931b1de017520f6d4aa4f78c5c8b *wubi.exe

---

### Post by cmcanulty on 2010-05-11
Your link to md5 is for windows, will it work in linux also? I am wondering because my Lucid has been very flaky.

---

### Post by colorlessprism on 2010-05-11
if your using linux you should be able to:

open a terminal and go to the correct directory  to check a downloaded iso file: 
cd /your/download/directory

Then  run the following command from within the download directory: 
md5sum <your file name should be here.iso>

it should print something like this:
712277c7868ab374c4d3c73cff1d95cb ubuntu-10.04-netbook-i386.iso

Compare the result your computer made with the corresponding hash on the [HashPage]("http://releases.ubuntu.com/10.04/MD5SUMS")  page.

---

### Post by ZaM0 on 2010-05-11
Thanks!
md5sums are the same. Both the Ubuntu and the Wubi one. I gave it one more try, the installation froze on 27% and the computer locked up. Other ideas? :S

---

### Post by ZaM0 on 2010-05-13
I really don't know what to do :( I tried noapic, nolapic, acpi=off, nomodeset, nothing helped - just random freezes, 'unexpected program closes' and anything... Tried Kubuntu - random freezes at boot up, OpenSUSE - freeze at loading screen... I did the disc integrity check, no problems found. Memtest passed 3 tests with no errors. Knoppix however is extremely stable - I'm writing this topic from its Live CD. No any special boot attributes was needed. Any ideas?

---

### Post by Rubi1200 on 2010-05-13
See my post here:

[http://ubuntuforums.org/showpost.php?p=9239795&postcount=26](http://ubuntuforums.org/showpost.php?p=9239795&postcount=26)

Try this from the LiveCD first of all and let us know what happens.

Second, Wubi has been known to be problematic on some computers. You might want to consider either:
a) a clean install of Ubuntu on its own partition or
b) waiting until some of the bugs are ironed out before moving forward with your Linux experiences.

Hope this helps.

---

### Post by ZaM0 on 2010-05-13
Thank you.
Tried xforcevesa noapic noapci nosplash irqpoll, I got a confirmation dialog about the safe graphics mode, I confirmed. Then it loaded the background and the cursor and the system locked up. I tried adding nomodeset to these attributes, it started up well, but when I opened the applications menu, it froze. So it's still the same thing :(

---

### Post by Rubi1200 on 2010-05-13
Hmm, this usually works.

Try this instead on the boot line (i.e. instead of replacing with the parameters I suggested):

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz **i915.modeset=1** --

---

### Post by ZaM0 on 2010-05-13
Doesn't help either :( Clicking on the Examples folder leaded to lock up ...
Tried Mandriva 2010(KDE), experiencing similar problems there too...

---

### Post by Rubi1200 on 2010-05-13
Sorry to hear this. I am out of ideas for the moment. I can only suggest that this might be a hardware issue (but which one?).

Keep trying different LiveCD's; the choice is huge.

Knoppix is great, but not recommended for installation to the HDD. You might want to consider either Debian or Kanotix (which is a fork of Knoppix designed for installation to a HDD).

Good luck!

---

### Post by ZaM0 on 2010-05-13
I installed the Ubuntu 9.04 which I did before to test it out again. It's the only Ubuntu version not to freeze while installing through Wubi. I got similar problems in the beginning, random errors, crashes, lock ups, etc. But after installing the NVidia drivers everything got ok. It's working nice and smooth, running Compiz too. No single error/crash since I installed them. I still get prompted to update to 9.10, but I'm pretty scared - howsoever I had more problems with the newer versions. Is it worth to try the upgrade or keep exploring Ubuntu 9.04?

EDIT: noope... It appears to happen randomly. Sometimes it could be stable all day long and sometimes it crashes on the 2nd minute. It's depending on that if it 'loads fine in the beginning' and then works perfectly stable till restarted. It looks like a hardware initialization problem, but why don't I experience any problems with Windows 7 for example?

---

### Post by ZaM0 on 2010-05-14
Using Ubuntu 9.04 on Wubi for second day. Behaves just perfectly, just until I restart and it would load 'bad'. It would then freeze, show "unexpected program termination" or any of the above. But it's perfectly stable on few boot ups. Can I track down the logs to get a better explanation of the problem?

---

### Post by ZaM0 on 2010-05-14
I've installed Ubuntu 9.04 on my hard drive. The results are worse :( I keep getting segmentation fault errors, black screens, lock ups, et cetera... This time I can't get it as stable as on Wubi... It can't stay stable more than 3-4 minutes - then the interface blinks and goes to black screen or shows weird colored strips/squares, locks up or shows tons of errors in the terminal. I did the kernel recovery mode partition check, no errors were found. Any ideas? :(

---

### Post by ZaM0 on 2010-05-18
I figured out that the only main difference between Knoppix, Debian and Ubuntu, is that Knoppix uses ReiserFS as a default file system. So I installed the Linux on reiserfs instead of ext3. I don't really know what's the problem with ext3 on my system, but it gets mad with any kind of segmentation faults... Never mind, I'm writing now from my Linux on a ReiserFS partition. I know it's not the best choice, but I'm happy. Cheers!

---

### Post by a-user on 2010-05-18
did i understood you right, that using reiserfs solved your problems?

---

### Post by ZaM0 on 2010-05-18
Yes. Linux runs absolutely stable now...

---

### Post by ZaM0 on 2010-07-18
Yup, I knew it wasn't the FS.

I've tried plenty of distros and I've installed Debian only on a ReiserFS partition. I've fooled myself that this was the problem, but I haven't got any proper explanation since then. The thing is that Debian doesn't have the Cool and Quiet technology support of my Sempron 3300+ included by default. And Ubuntu has integrated Cool'n'Quiet kernel support, which makes use of it.

How I figured it out: These days I've tried recompiling my Debian kernel to include CnQ support, but booting with the new kernel have led to the same symptoms. Switching off Cool'n'Quiet from BIOS made the system to boot and run stable with the freshly compiled core.

I've read that the Linux kernel includes support for CnQ (powernow-k8 ), but I'm not sure why I have had problems with my Sempron. Probably it's only implemented for Athlon and the dual core series, but isn't yet implemented/won't be ever implemented for Sempron? I don't know.

Anyway, problem solved, I could live without CnQ. 
Cheers. I hope this helps.

---

