---
title: "Samsung SCX-3205, unable to scan"
date: 2011-10-10
forum: General Help
---

### Post by uhappo on 2011-10-10
Hi,

I received my Samsung SCX-3205 today. I can print but there's no way to scan, simple print and xsane says there are no scanners available.

Samsung site: [SCX-3205 support]("http://www.samsung.com/uk/consumer/print-solutions/print-solutions/mono-multi-function-products/SCX-3205/SEE-support")

Some appointed me to this site: [SANE SCX-2305]("http://alioth.debian.org/tracker/index.php?func=detail&aid=312902&group_id=30186&atid=410366") but I don't know how to proceed with this problem

EDIT: [Solution from launchpad]("https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/576531/comments/14")

```
ID 04e8:3441 Samsung Electronics Co., Ltd
```

```
sudo /etc/init.d/udev restart
```

---

### Post by elf23 on 2011-10-17
Hi uhappo,

I have the same problem after updating to ubuntu 11.10, and I don't really understand your solution. I tried entering the second command you specified at the command line, but it didn't help.

I've also tried uninstalling and re-installing the drivers from Samsung, but it always says that I don't have SANE installed (which I have, as far as I can tell from looking in synaptic).

Any further help from anyone who's also had this problem would be greatly appreciated! :)

---

### Post by uhappo on 2011-10-17
Sorry, my link to launchpad-solution was dead, I updated it.

To ```
/etc/sane.d/xerox_mfp.conf
``` add
```
#Samsung SCX-3205
usb 0x04e8 0x3441
```

and to ```
/lib/udev/rules.d/40-libsane.rules
``` add
```
# Samsung SCX-3205
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="3441", ENV{libsane_matched}="yes"
```

Then
```
sudo /etc/init.d/udev restart
```

and you should be good!

---

### Post by elf23 on 2011-10-17
Awesome, it worked! Thanks a million uhappo! :)

---

### Post by mariomario on 2012-03-09
first thank you to uhappo and if it can be to any help. I have applied it to my compac laptop and hp mini 110 series. Thank your for your help. It was very very helpful. Greetings from berlin

---

### Post by WinterWeaver on 2012-04-04
This works perfectly thanks, uhappo!

By the way, how do you know what values to add, and where to add it? I suspect that knowing why you did what you did may solve many of my future hardware issues :)

ta,

WW

---

### Post by shiinto23 on 2012-04-11
yeess!!! thank you very much! works A+!!

---

### Post by uhappo on 2012-04-22
By the way, scanning works just fine with 12.04 but printing causes some problems. Usually after powering on the device I'm able to print one time with success. But, after that, if I print something else (a different pdf-document etc) quickly after first printing the printer goes a bit crazy. In Printer-properties I see "Idle - sending data to printer" and it usully prints empty pages or some miscallenaous letters in one line.

Anyone else noticed this? In 11.10 everything was fine but I see this with 12.04 only

---

### Post by 10o on 2012-04-26
I have the **wireless** version of this printer, the [SCX-3205W]("http://www.samsung.com/uk/consumer/print-solutions/print-solutions/mono-multi-function-products/SCX-3205W/SEE-support"). I previously assigned a fixed IP to the printer and on install of 12.04 the printer was recognized immidiately. I did not have to add seperate Samsung drivers to get the printer up and running. It was kind of plug and play this time around.

But the scanner I cannot get to work. It is not recognized. After following #3, nothing changes. Perhaps because that is the wired version of this printer. Can anybody help me out?
Maybe I should go find a cable to connect the printer to my laptop, so lsusb returns the right usb id? Or is this useless?

---

### Post by mastablasta on 2012-04-26
> **uhappo said:**
> By the way, scanning works just fine with 12.04 but printing causes some problems. Usually after powering on the device I'm able to print one time with success. But, after that, if I print something else (a different pdf-document etc) quickly after first printing the printer goes a bit crazy. In Printer-properties I see "Idle - sending data to printer" and it usully prints empty pages or some miscallenaous letters in one line.
 
Anyone else noticed this? In 11.10 everything was fine but I see this with 12.04 only
 
 
interesting. how did you install the drivers?
 
I used this PPA described here:
[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)
 
it seems 12.04 messes it it all up.... don't think it's Samsung fault this time.
since i connect the printer via USB to windowsXP mashcine i just hope the printing works ok on upgrade i have to perform (from 10.10 all the way up to 12.04).

---

### Post by 10o on 2012-04-26
> **mastablasta said:**
> interesting. how did you install the drivers?
I did not install any additional "external" Samsung drivers at all. The printer was already assigned a fixed IP before and on install of 12.04 Beta the Samsung SCX-3205W was recognised as a network printer and Ubuntu found its drivers in the online driver database. So printing worked out of the box this time around...

Scanning is not possible though. No scanner found...

---

### Post by mastablasta on 2012-04-26
that's because your's is a networked printer. it acts like connecting to another network device. and it works a bit different. the SCX-3205 is a USB printer i believe.

---

### Post by adesteele on 2012-04-30
I have just done the 10.10- 12.04 upgrade and the scx-3205 printer prints fine, but the scanner is not recognised at all.  Any ideas please?

---

### Post by adesteele on 2012-05-02
I now have a working solution to get the samsung scx-3205 scanner working when migrating from 10.10 to 12.04.
Sources:
[http://ubuntuforums.org/showthread.php?t=1857478](http://ubuntuforums.org/showthread.php?t=1857478)
[http://www.sane-project.org/cgi-bin/driver.pl?manu=samsung&model=&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=samsung&model=&bus=any&v=&p=)

Code:
command

[PHP]sudo gedit /etc/sane.d/xerox_mfp.conf[/PHP]

add in 

[PHP]#Samsung SCX-3205
usb 0x04e8 0x3441
[/PHP]

command

[PHP]sudo gedit /lib/udev/rules.d/40-libsane.rules[/PHP]

add in

[PHP]# Samsung SCX-3205
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="3441", ENV{libsane_matched}="yes"[/PHP]

command

[PHP]sudo /etc/init.d/udev restart[/PHP]


and it works.

---

### Post by uhappo on 2012-05-02
@adesteele:

Yeah, correct, those instructions are on the third post of this thread.

I haven't done a clean install of final 12.04, this is a development version installed long ago and updated. So, those who have done a clean install: Do you need additonal Samsung-drivers for printing or is ot out of the box working? Scanning can be enabled later as is stated.

---

