---
title: "Brother MFC-7340 Scanner on Ubuntu 12.04"
date: 2012-03-19
forum: General Help
---

### Post by bladernr on 2012-03-19
Ok, so up until I installed 12.04, my Brother MFC-7340 was working fairly well.  Printing was a breeze and scanning worked.  Now that I've installed 12.04 from scratch rather than upgrading in place, I can not get the scanner working at all.

I've installed the brscan drivers, brscan-skey tool, tried both the 64bit and 32bit brscan3 drivers, among other things.

Unfortunately, no matter what I've tried, I can't actually get any software to see the scanner.

sane-find-scanner locates the scanner:


bladernr@klaatu:~$ sudo sane-find-scanner
<Unnecessary output snipped>
found USB scanner (vendor=0x04f9, product=0x01e7) at libusb:002:006

And that's confirmed by lsusb:
Bus 002 Device 006: ID 04f9:01e7 Brother Industries, Ltd MFC-7340

But nothing else can find the scanner.

bladernr@klaatu:~$ sudo scanimage -L

No scanners were identified. If you were expecting something different, check that the scanner is plugged in, turned on and detected by the sane-find-scanner tool (if appropriate). Please read the documentation which came with this software (README, FAQ, manpages).

So, any ideas on how to get the scanner portion working in Precise?  It's been so long since I got this all-in-one working with Ubuntu that I've long since forgotten exactly what I had to do to make it work :(

FWIW, the printing function works great... it's just the scanner part.

---

### Post by wojox on 2012-03-19
Did you

1. Open "/lib/udev/rules.d/40-libsane.rules" file.

 ```
gksudo gedit /lib/udev/rules.d/40-libsane.rules
```

2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
```

3. Restart the OS.

---

### Post by bladernr on 2012-03-19
I did, but that is beside the point as I can't even get things like xsane or gscan2pdf or simple-scan to see the scanner when run as root :(  The udev rules changes, IIRC, only apply to making the device available to non-root users.

In any cause, yes, I did do that and it made no difference.

---

### Post by wallaroo on 2012-03-19
For Ubuntu version 11.10 up, you also have to do this ....

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

---

### Post by bladernr on 2012-03-22
Yep... did that too. After that failed to work, I also removed the 64bit driver and installed the 32bit one, that too failed to work.

And to make matters worse, I also had installed brscan-skey and that caused the printer to crash during print jobs, making it spit out every piece of paper in the tray :(  

So skey had to go as well...

---

### Post by Mphill102 on 2012-04-06
I seem to be having the same issue with my Brother MFC-8480DN. Printer works fine but the scanner does not. Simple scan will start. When I push the scan button it just sits there and spins. Xsane will not even start. The printer is networked with 2 Windows machines. The ubuntu machine is running 12.04 32bit  bata 2 with all updates.

---

### Post by ierotheo on 2012-04-25
I am having the same issue with the Brother MFC-8860DN. Printer spits out every single paper in the tray and scanner is not recognized by any scanning programs (XSane, Simple Scan or ScanLite).

---

### Post by techsupport on 2012-04-25
> **ierotheo said:**
> I am having the same issue with the Brother MFC-8860DN. Printer spits out every single paper in the tray and scanner is not recognized by any scanning programs (XSane, Simple Scan or ScanLite).

I had this problem in 11.04, and it do this. 

I needed to go into the configuration and use the drop down to select each of the alternative drivers that were listed. Eventually I found one that fixed it. It is really hit and miss.

I don't have this problem in 12.04 LTS so it seems to have been patched.

---

### Post by kurt18947 on 2012-04-25
For scanning on 12.04, try adding every scanner user to "lp" group.  I was having trouble on 12.04 and that seemed to do the trick.  This was in addition to wojox' fix and wallaroo's fix.  I've sent a couple emails to Brother's linux support people and got acknowledgements  so they should know there are issues with 12.04.  I don't expect any official fixes until after 12.04 is released, 'they don't support Beta software'.

---

### Post by compdave7681 on 2012-05-01
Ok I just did a fresh install of 12.04 and was having the same issue (MFC-7340). I found this a while ago and I got it to print with 11.04/10 and now 12.04. Next I am going to try the scanner options and post back. :D

[http://raywoodcockslatest.blogspot.com/2010/05/installing-brother-mfc-7340-printer-in.html]("http://raywoodcockslatest.blogspot.com/2010/05/installing-brother-mfc-7340-printer-in.html")


Edit: Ok so after trying this out IT WORKS!!!!! :D:D

This is what I did:
**AS ROOT**
dpkg -i brscan3-0.2.11-4.i386.deb(Reading database ... 200822 files and directories currently installed.)
Preparing to replace brscan3 0.2.11-4 (using brscan3-0.2.11-4.i386.deb) ...
Unpacking replacement brscan3 ...
Setting up brscan3 (0.2.11-4) ...
root@Linux-Office:/home/brown/Downloads# dpkg -l | grep Brother
ii  brmfc7340lpr                           2.0.2-1                                 Brother MFC-7340 LPR driver
ii  brscan3                                0.2.11-4                                Brother Scanner Driver
ii  cupswrappermfc7340                     2.0.2-1                                 Brother MFC7340 CUPS wrapper driver
ii  printer-driver-ptouch                  1.3-3                                   printer driver Brother P-touch label printers
root@Linux-Office:/home/brown/Downloads#
--------------------------------------
Simple scan works with feeder :D
--------------------------------------
Buttons:

In Terminal:
dpkg -i --force-all brscan-skey-0.2.1-3.i386.deb
dpkg -l | grep Brother
**EXIT ROOT**
brscan-skey
brscan-skey -l

Open Dash -> Startup Applications
Follow his instructions
-------------------------
Scan to Image Starts GIMP (same as he had)
Scan to File saves as PNM image (image/x-portable-anymap) in /home/user/brscan

Scripts have moved to /opt/brother/scanner/brscan-skey/script/

MAKE BACKUPS OF OLD SCRIPTS AND CREATE NEW SCRIPT (AS ROOT)

cd /opt/brother/scanner/brscan-skey/script/
mv scantofile-0.2.3-0.sh /opt/brother/scanner/brscan-skey/script/scantofile-0.2.3-0.sh.bak
nano scantofile-0.2.3-0.sh
copy and paste script; change this line: output_file="/media/DATA/Current/Scan_`date +%Y%m%d-%H%M%S`.pdf" to output_file="/somedir/where/you_want/Scan_`date +%Y%m%d-%H%M%S`.pdf"

I changed the resolution to 200 (looks ok for txt)
ctrl+x
chmod +x scantofile-0.2.3-0.sh

mkdir of where you want to save 

Test it out.

Hopefully you all can figure out the rest of it for changing scantoimage and so on.

---

