---
title: "hp laserjet pro m1212nf and maverick 64bit"
date: 2010-12-09
forum: General Help
---

### Post by lviggiani on 2010-12-09
Hi Everybody,
I've just received my hp laserjet pro m1212nf printer / fax /scanner device.

It's installed as a Ethernet printer.

First I had troubles with the printer. I could solve it by running
```
$ sudo hp-plugin
```
and then reinstalling the printer from the HP Device manager utility.

During the installation the tool also told me:
```
Unable to locate the HPLIP Fax PPD file:
HP-Fax3-hpcups.ppd.gz
Fax setup has been disabled.
```
BTW, I then installed the hplip-cups package, then reinstalled the printer and the fax is now available (not tested yet)


The rest of the setup seems to be fine and at the end I can print the test page out.

When then I try to scan, I get an i/o error.
I've tried from the terminal...
```
$ hp-scan
```
...and this is what I get:
```
HP Linux Imaging and Printing System (ver. 3.10.6)
Scan Utility ver. 2.2

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hpaio:/net/HP_LaserJet_Professional_M1212nf_MFP?zc=NPIACDA40

warning: No destinations specified. Adding 'file' destination by default.
warning: File destination enabled with no output file specified.
Setting output format to PNG for greyscale mode.
warning: Defaulting to '/home/lviggiani/hpscan001.png'.
Using device hpaio:/net/HP_LaserJet_Professional_M1212nf_MFP?zc=NPIACDA40
Opening connection to device...
error: SANE: Error during device I/O (code=9)

```

Can someone help me please?
Thanks, Luca.

---

### Post by thomhehl on 2011-01-05
Hi!

I'm looking into this printer for my Dad and Mom who I have on Ubuntu. I was wondering if you figured out the scan problem and if you thought this was a good fit for Ubuntu?

---

### Post by lviggiani on 2011-01-05
> **thomhehl said:**
> Hi!

I'm looking into this printer for my Dad and Mom who I have on Ubuntu. I was wondering if you figured out the scan problem and if you thought this was a good fit for Ubuntu?

Hi, unfortunately I discovered that you can't scan with Ubuntu as the scanner is not supported by SANE API (TWAIN equivalent for Linux).
So I gave up with scanning on Ubuntu... My suggestion is to look for a different model.
You may want to search here ( [http://www.sane-project.org/cgi-bin/driver.pl]("http://www.sane-project.org/cgi-bin/driver.pl") ) before choosing thr printer / scanner.

Cheers.

---

### Post by solorvox on 2011-02-07
Actually, this is a **old** bug (May of 2009) with Ubuntu.    [Bug #380322]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/380322")  If you read /var/log/user.log, you'll notice it can't open a lib.  ```
sudo /bin/ln -s /usr/lib/libhpmud.so.0 /usr/lib/libhpmud.so
```  Fixes the errors and you can scan.  Both hp-scan and xsane work now... However, I can't get color scans.  Only back and white.  I'm still working on that part. :)

---

### Post by lviggiani on 2011-02-08
> **solorvox said:**
> Actually, this is a **old** bug (May of 2009) with Ubuntu.    [Bug #380322]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/380322")  If you read /var/log/user.log, you'll notice it can't open a lib.  ```
sudo /bin/ln -s /usr/lib/libhpmud.so.0 /usr/lib/libhpmud.so
```  Fixes the errors and you can scan.  Both hp-scan and xsane work now... However, I can't get color scans.  Only back and white.  I'm still working on that part. :)

Hey Man, thank' you very much! It worked to me as well!
I only had to remove and re-install the printer throug the hp-gui (qt based) program... don't ask me why...
I can only scan in B&W, confirmed. For the time being it's ok as I need to scan some documents, however if you'll have success with color scan, it would be great if you would post details here...
Thanks again, Luca.

---

### Post by pizzafarmer on 2011-03-11
Did you ever get scanning to work properly? I had trouble installing this printer and found that the version of HPLIP packaged with Lucid didn't support it. I ended up downloading and installing HPLIP 3.11.1 and was then able to install the printer. Scanning works perfectly, black & white and color. Maybe this would help in your situation as well.

---

### Post by lviggiani on 2011-03-15
> **pizzafarmer said:**
> Did you ever get scanning to work properly? I had trouble installing this printer and found that the version of HPLIP packaged with Lucid didn't support it. I ended up downloading and installing HPLIP 3.11.1 and was then able to install the printer. Scanning works perfectly, black & white and color. Maybe this would help in your situation as well.

Hi, thank you for the information!
Actually Maverick come with 3.10.6 from ubuntu repos. I'll try to install latest HPLIP from the site and see if I can get color scanning too.
Thanks, Luca.

---

### Post by lviggiani on 2011-05-02
> **pizzafarmer said:**
> Did you ever get scanning to work properly? I had trouble installing this printer and found that the version of HPLIP packaged with Lucid didn't support it. I ended up downloading and installing HPLIP 3.11.1 and was then able to install the printer. Scanning works perfectly, black & white and color. Maybe this would help in your situation as well.

Hi, just to say that I have recently moved to Natty which by default ships with hplip 3.11 and now I can scanning works perfectly b&w and color.
Thanks, Luca.

---

### Post by UglyDuckling on 2011-05-09
Hi !

I am about to buy a LaserJet Pro m1212nf and I also worry to be able to scan. Why don't you simply setup the scan to file fonction through the network ?

---

### Post by pizzafarmer on 2011-05-09
Duckling, I didn't think of trying the network connection for that, but I think I still would have had to upgrade HPLIP to be able to do it. lviggiani was able to fix his scanning problems that way as well after upgrading to Natty.

---

### Post by collisionystm on 2011-05-09
> **lviggiani said:**
> Hi Everybody,
I've just received my hp laserjet pro m1212nf printer / fax /scanner device.

It's installed as a Ethernet printer.

First I had troubles with the printer. I could solve it by running
```
$ sudo hp-plugin
```
and then reinstalling the printer from the HP Device manager utility.

During the installation the tool also told me:
```
Unable to locate the HPLIP Fax PPD file:
HP-Fax3-hpcups.ppd.gz
Fax setup has been disabled.
```
BTW, I then installed the hplip-cups package, then reinstalled the printer and the fax is now available (not tested yet)


The rest of the setup seems to be fine and at the end I can print the test page out.

When then I try to scan, I get an i/o error.
I've tried from the terminal...
```
$ hp-scan
```
...and this is what I get:
```
HP Linux Imaging and Printing System (ver. 3.10.6)
Scan Utility ver. 2.2

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hpaio:/net/HP_LaserJet_Professional_M1212nf_MFP?zc=NPIACDA40

warning: No destinations specified. Adding 'file' destination by default.
warning: File destination enabled with no output file specified.
Setting output format to PNG for greyscale mode.
warning: Defaulting to '/home/lviggiani/hpscan001.png'.
Using device hpaio:/net/HP_LaserJet_Professional_M1212nf_MFP?zc=NPIACDA40
Opening connection to device...
error: SANE: Error during device I/O (code=9)

```

Can someone help me please?
Thanks, Luca.

Wow talk about dejavu. I just installed the same printer on natty yesterday lmao. I installed hplip from the soft center....only thing I haven't messed with yet is scanning.

---

### Post by martinr on 2011-07-11
> **lviggiani said:**
> Hi Everybody,
I've just received my hp laserjet pro m1212nf printer / fax /scanner device.

It's installed as a Ethernet printer.

When then I try to scan, I get an i/o error.
I've tried from the terminal...
```
$ hp-scan
```
...and this is what I get:
```
HP Linux Imaging and Printing System (ver. 3.10.6)
Scan Utility ver. 2.2
...
Using device hpaio:/net/HP_LaserJet_Professional_M1212nf_MFP?zc=NPIACDA40
Opening connection to device...
error: SANE: Error during device I/O (code=9)

```

Can someone help me please?
Thanks, Luca.

Many people experience problems with repetative scans, that end in "SANE: Error during device I/O (code=9)".

See this [thread]("http://ubuntuforums.org/showthread.php?t=1792538") for details or vote for this [bug report]("https://bugs.launchpad.net/hplip/+bug/806950") in order to get it fixed.

---

### Post by AAzKgr on 2011-08-29
Hi everyone!
First of all, thanks for the tips and hints here. I was trying to make my m1212 hp printer work with all its functions a long ago, and today I got it.
I'm using 11.04 Ubuntu, and realized today that the SysOp comes originally with a hp m1212 driver. I tried to install it, but my printer couldn't work. And thats why I've got here.
First of all, I've downloaded the hplip printer driver, but I really have no idea if that was necessary, 'cause I've ran, on a term, the "sudo hp-setup" command, wich installed a hp specific driver, and "voi-la", the printer, the scanner and (not tested yet) the fax are installed. The printer is doing its job normally, the scanner is scanning in collor. Later on I will test fax utility, so I can tell you if it is working.
I have no idea if this is going to help you all, but I really hope it does!

---

