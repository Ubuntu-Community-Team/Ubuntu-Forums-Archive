---
title: "Is my system supported?"
date: 2009-11-30
forum: General Help
---

### Post by Caathrok on 2009-11-30
So, I used to have Red Hat in college. Hated the look, feel, and hassle...

Well, Windows installer requires third party drivers, which don't work. And it seems like everytime I get it online I mysteriously get hit by virut & crypto (did you know anti-virus programs are helpless before them?).  So, I'm switching to Linux. Ubuntu seemed like a good place to start since it's free. What I can't seem to determine is how hard it's gonna be to get my computer up and working. That wiki link for wireless devices doesn't say whether mine will work, and nothing I've seen yet mentions SATA/II HDDs, 64bit dual-core processors, physics cards...

It's about half downloaded but if it's not gonna even install (like windows)... I might be throwing away a $2k machine because I beat it to pieces.

Computer Specs:
ECS KA3-MVP AM2 Crossfire
AMD Athlon 64 FX 62 AM2 (2.8Ghz Dualcore 64bit)
250GB SATA II (WDC2500JS)
NEC 18x +/- DVD-RW
2x1GB Corsair DDR2 6400 RAM (been meaning to upgrade to 4x1gb)
ATI x1950 XTX 512MB PCI-E
ATI x1950 XTX 512MB Crossfire PCI-E
Asus PhysX P1 128mb
Linksys WUSB54GS

---

### Post by dcstar on 2009-12-01
> **Caathrok said:**
> So, I used to have Red Hat in college. Hated the look, feel, and hassle...

Well, Windows installer requires third party drivers, which don't work. And it seems like everytime I get it online I mysteriously get hit by virut & crypto (did you know anti-virus programs are helpless before them?).  So, I'm switching to Linux. Ubuntu seemed like a good place to start since it's free. What I can't seem to determine is how hard it's gonna be to get my computer up and working. That wiki link for wireless devices doesn't say whether mine will work, and nothing I've seen yet mentions SATA/II HDDs, 64bit dual-core processors, physics cards...
.........

Ubuntu is a Live CD that you boot up to see if you hardware works, it might take you 10 minutes to find out for sure.

---

### Post by fluffman86 on 2009-12-01
All of your hardware will work great, with the possible exception of your USB Wireless Dongle.  I've never seen one of those work easily, though they usually can be made to work.  You'll need a wired internet connection, at least temporarily.  

When downloading, I recommend that you get the amd64 version.  Some people say there are problems with it and all of the software doesn't work.  I disagree.  It's faster, and everything seems to work just fine with the 64bit version.

When installing, take a look at this guide:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

and more specifically:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

With a few exceptions:
1.  Make / 10 - 20 GB instead of 4 as posted in the link.
2.  Make swap 1 GB
3.  Select Ext4 as the partition type instead of Ext3.  

Let me know if you have any questions!

---

### Post by Caathrok on 2009-12-01
ya, and now I know that, no. it doesn't. only an hour and a half to download and burn it.

> /init: line 1: can't open /dev/sdb : no medium found
/init: line 1: can't open /dev/sdb : no medium found
/init: line 1: can't open /dev/sdc : no medium found
/init: line 1: can't open /dev/sdc : no medium found
/init: line 1: can't open /dev/sdd : no medium found
/init: line 1: can't open /dev/sdd : no medium found
/init: line 1: can't open /dev/sde : no medium found
/init: line 1: can't open /dev/sde : no medium found
stdin: error 0
stdin: error 0


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash
Enter 'help' for a list of built-in commands.
(initramfs) Unable to find a medium containing a live file systemit does that whether I do the live thing or try to install...

I found a thread where the guy had to remove his video card... acted like he never got them to work, and was stuck with his onboard video.
Obviously that's not an option. Though I am about to try it, figure maybe if it'll install without the vidya cards I can fix it so they work later.

---

### Post by fluffman86 on 2009-12-01
Your CD didn't burn properly.  Be sure to burn on a slow setting (like 24x for a 48x CD, or less), and then when you boot from the CD select "Check CD for Defects"

---

### Post by Caathrok on 2009-12-01
ugh. OK...

I only have DVDs here. Am I gonna have to buy CDs?

Might as well try again with the 64bit version or whatever.

---

### Post by Spectre5 on 2009-12-01
> **fluffman86 said:**
> Your CD didn't burn properly.  Be sure to burn on a slow setting (like 24x for a 48x CD, or less), and then when you boot from the CD select "Check CD for Defects"

Definitely follow this advice...I usually burn iso's on the slowest settings I can.  Many people will suggest you just use 4X.  Also, be sure to check the md5sum of the iso file you downloaded.

---

### Post by fluffman86 on 2009-12-01
DVDs *SHOULD* work fine, but be SURE to burn at an ultra low speed, like 1x or 2x for DVDs.

---

### Post by Caathrok on 2009-12-01
ok, worth a try.


hmmm, well, here's hoping. it'll be interesting to have an operating system that supports 64bit for once.

---

### Post by fluffman86 on 2009-12-01
Also, if you're in Windows now, you can download and install unetbootin from [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and it will turn your ISO into a bootable USB drive.  It's neat and faster than burning a DVD, and installs *MUCH* faster.

Also also, check your download for errors before burning or installing to USB:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Primefalcon on 2009-12-01
> **fluffman86 said:**
> Also, if you're in Windows now, you can download and install unetbootin from [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and it will turn your ISO into a bootable USB drive.  It's neat and faster than burning a DVD, and installs *MUCH* faster.

Also also, check your download for errors before burning or installing to USB:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Not to mention doesn't waste a disk or anything, since you can wipe the usb stick after, this is the way standard way to install to netbooks as well, they typically don't have a cd/dvd drive unless you buy an external one

---

### Post by Caathrok on 2009-12-01
nah, windows won't install on the system for a bunch of stupid microsoft reasons.

been on a laptop for about 3 months trying to turn my paperweight back into a computer.


you know what? my motherboard supports booting from USB-flash drives.

I think I'll try that before wasting another disc. thnx!

---

### Post by Primefalcon on 2009-12-01
> **Caathrok said:**
> nah, windows won't install on the system for a bunch of stupid microsoft reasons.

been on a laptop for about 3 months trying to turn my paperweight back into a computer.


you know what? my motherboard supports booting from USB-flash drives.

I think I'll try that before wasting another disc. thnx!
there's always rw's as well

---

### Post by Caathrok on 2009-12-01
. . .

well, my computer won't boot from usb, so I burned a disc.

this time, instead of giving me the error message after I hit "install" it turned off the monitor

---

### Post by fluffman86 on 2009-12-01
Did you run the MD5SUM and the "Check Disc for Errors" before trying to install?

And you don't want to run the "Install" option, you want the "Try Ubuntu without changing my computer" option, which will let you install after you try it out without rebooting.

It's probably not recognizing your ATI cards immediately.  Plug your monitor into your onboard card to start with, and once you're installed we'll get your ATI cards working.

---

### Post by Caathrok on 2009-12-01
ok I got it to boot.

no onboard but I removed the cable going between the cards.

it said something about "one of you harddrives may be failing"
and "one of your discs reports errors"
and "click the icon for more information"



there isn't an icon...

---

### Post by Caathrok on 2009-12-01
installing anyway.

---

### Post by fluffman86 on 2009-12-01
> **Caathrok said:**
> ok I got it to boot.

no onboard but I removed the cable going between the cards.

it said something about "one of you harddrives may be failing"
and "one of your discs reports errors"
and "click the icon for more information"



there isn't an icon...

Once you install, you'll still get that error.  It's probably a bug.  I got that error a couple of years ago...still no problems with my drive.

To disable it once you've installed, there should be a HDD icon near the clock, or you can go to System > Administration > Disk Utility, click the drive that's failing on the left panel, then "More Information" on the right side, and the check the box that says "Don't warn me if the disk is failing" about mid way down the page that opens.

Just be sure to keep a backup of your important files.

Edit: reformatting the drive during install may help it and you may not have any more problems with it after that.  Only disable the failure warning if you keep getting the error and you're relatively sure your drive is OK.

---

### Post by Caathrok on 2009-12-01
it automatically installed my wireless USB

all I had to do was open the network connections and make a wireless one with my SSID and it just worked.
now I'm off to figure out how to install flash and stuffs

---

### Post by Caathrok on 2009-12-02
Why doesn't flash work right?

---

### Post by Spectre5 on 2009-12-02
Did u install it?  How?

---

### Post by fluffman86 on 2009-12-02
1.  Go to System > Administration > Software Sources.  Check the top 4 boxes.

2.  Applications > Ubuntu Software Center > View > All Applications > Search for "flash" > Double click on Ubuntu Restricted Extras (should be the first result) > Install.

---

