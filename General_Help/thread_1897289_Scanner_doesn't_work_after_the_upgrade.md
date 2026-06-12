---
title: "Scanner doesn't work after the upgrade"
date: 2011-12-18
forum: General Help
---

### Post by huntkey on 2011-12-18
Hi experts,

After the upgrade from 11.04 to 11.10 my scanner doesn't work any more...

It is Samsung SCX-4521F. It is multi-purpose printer. The printing part works fine so the USB connection should be good.

When I run Xsane image scanning software it says "no device available".

Help please!

Thanks!

---

### Post by huntkey on 2011-12-19
sane-find-scanner tool can see the scanner:

found USB scanner (vendor=0x04e8 [Samsung], product=0x3419 [SCX-4x21 Series]) at libusb:007:007

But not by scanimage tool...

I have had numerous problems after the upgrade. I hope I didn't upgrade to 11.10.

Thanks,

---

### Post by huntkey on 2011-12-19
I have tried something else but it still doesn't work... I really need my scanner... It is actually more important than the printing function of it. Help please...

---

### Post by huntkey on 2011-12-19
Nobody knows about it? Or am I at wrong place? Is there any other place I can get help from?

---

### Post by Synoc on 2011-12-19
I know precious little but if you can't get any help at all, someone with a passing familiarity is better than nothing. 

First question:
when you do an ```
lsusb
``` in terminal. do you see your scanner?

second:
sssuming Simple scan does come with 11.x, can you use your scanner with that?

I do know porting from one version to another CAN mess with a few things. so you might want to try a reinstall if the answer to both of those is yes

```
sudo apt-get purge xsane
sudo apt-get install xsane
```

---

### Post by huntkey on 2011-12-20
Hey [Synoc]("http://ubuntuforums.org/member.php?u=975233") thank you so much for the reply!

Yes I can see the printer.

```
$ lsusb
...
Bus 007 Device 008: ID 04e8:3419 Samsung Electronics Co., Ltd Composite Device
...
```

sane-find-scanner tool can see the printer as well.

```
$ sane-find-scanner 
...
found USB scanner (vendor=0x04e8 [Samsung], product=0x3419 [SCX-4x21 Series]) at libusb:007:008
...
```

I also tried to reinstall the xsane but still doesn't work. It is good try though! I should have tried it. My unity was broken after the upgrade but was fixed after reinstalling it. Simple scan can't find the scanner either... Anything else I can try?

Thanks!

---

### Post by inkrypted on 2011-12-20
I have noticed that Unity does not install all packages necessary for scanning. Check and see if "sane-utils" are installed. If not install them.

---

### Post by inkrypted on 2011-12-20
A little Googling brought me to this and it looks promising. 
[http://www.howtoforge.com/sane_xsane_scanner](http://www.howtoforge.com/sane_xsane_scanner)
Best of luck.:D

---

### Post by huntkey on 2011-12-20
Hey [inkrypted]("http://ubuntuforums.org/member.php?u=536170") thank you for the reply. None of them worked... I do have sane-utils installed. I can't find the scanner even as root... But thanks anyway

---

### Post by yahs on 2011-12-20
The thread you need is on this page.
**HOWTO Install Samsung Unified Printer Driver** which deals with everything to do with Samsung printing.
If you read the opening paragraph you will see that this issue is common.  There is a link to a fix which is on page 85 of the thread

---

### Post by huntkey on 2011-12-20
Thank you so much Yahs! Finally it works now!

---

