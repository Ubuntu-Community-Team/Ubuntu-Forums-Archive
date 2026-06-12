---
title: "Lightscribe, Good Lightscribe Program for 9.04 64bit"
date: 2010-04-23
forum: General Help
---

### Post by daldude on 2010-04-23
What is a Good Lightscribe Labeling Program for Ubuntu 9.04 64-bit? I installed LIGHTSCRIBE SIMPLE LABELER but it's the biggest piece of crap program, you can't even set the Font Size, all it allows you to do is set the Font.

I'm not a Linux Expert so I need a program that is easy to install and does not require compiling  or complex manual installation with multiple command line text commands (unless I can cut and paste).
I'm still confused by the complex Linux directory structure I have no idea where or what my home directory is or how to get to it from a terminal window / command line prompt.

---

### Post by marshmallow1304 on 2010-04-23
First, note that I haven't tried this, but in theory it should work.


I assume that you're using 32-bit Ubuntu.  To make sure, check in the terminal (Applications->Accessories->Terminal).
```
uname -m
```
If you're not, it gets more complicated and I won't get into it unless it's necessary.


Go here
[http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814](http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814)
and download the .deb package to your Desktop.  Double-click to install.

Install some dependencies in the terminal.
```
sudo apt-get update && sudo apt-get install -y alien rpm
```

Download the .rpm release of LaCie from here
[http://www.lacie.com/support/drivers/driver.htm?id=10061](http://www.lacie.com/support/drivers/driver.htm?id=10061)
and save to your Desktop.  Rename the download, replacing all spaces with dashes (-).

Convert the rpm package to deb.
```
cd ~/Desktop
sudo alien --to-deb *.rpm
sudo chown <user>:<user> *.deb
```
where <user> is your user name.

Double-click the produced deb to install.



By the way, your home directory is located at /home/<user>.  You can get to it quickly with ~ , e.g.
```
cd ~
```

---

### Post by 2hot6ft2 on 2010-04-23
I have a lightscribe drive too and I agree the lightscribe application is pitiful.
What it boils down to is the lightscribe for text going around the disc that looks awful and is a pain to read.
And LaCie which will do images which made it look better. There is no package that you can just double click on to install stuff for that drive and you can thank lightscribe for that.
If you do go thru the hassle of setting it up you can make some nice discs like in the pic. below but it will take some effort on your part.

[This guide will help you install the base Lightscribe software and the LaCie 4L Disk Labeling software on a 32-bit or 64-bit Ubuntu install.]("http://ubuntuforums.org/showthread.php?t=809112")

---

### Post by daldude on 2010-04-24
Ok thanks for the link but how do you enter Text into the program or what program did you use to create a the image to print to the DVD Disc that allows you to add Text?
Basically all I want to do is make a simple TEXT Label on my DVD Discs and be able to change te Font Size and make it so the Text is curved so it fits around the Disc.

This program is fine and dandy if one has the means to somehow scan a image of a DVD disc into their computer and the only way I can do that is in Windows because Linux does not support my Visioneer Flatbed Scanner and I don't want to have to boot to XP just to scan an image of the Disc of the Movie I want to backup because then I might as well just use XP to label my Lightscribe DVDs and the whole purpouse of instaaling Lightscribe Support on Linux is to avoid useing XP as much as possible.

> **2hot6ft2 said:**
> I have a lightscribe drive too and I agree the lightscribe application is pitiful.
What it boils down to is the lightscribe for text going around the disc that looks awful and is a pain to read.
And LaCie which will do images which made it look better. There is no package that you can just double click on to install stuff for that drive and you can thank lightscribe for that.
If you do go thru the hassle of setting it up you can make some nice discs like in the pic. below but it will take some effort on your part.

[This guide will help you install the base Lightscribe software and the LaCie 4L Disk Labeling software on a 32-bit or 64-bit Ubuntu install.]("http://ubuntuforums.org/showthread.php?t=809112")

---

### Post by daldude on 2010-12-13
Try this program [SIZE=5]**qlscribe - Qt lisghtScribe**[/SIZE]
 

 

 I think I found this program at [http://qlscribe.sourceforge.net/](http://qlscribe.sourceforge.net/) it  does what I want and allows you to just type in text and choose  the font size and type and even make it circular it also allows you to insert a image but the way you manipulate it's size or shape is a pain but it's a vast improvement over the simple label program but for putting an image on a Disc I guess the [SIZE=2]the 4L Disk Labeling program is better software also qlscribe Qt Lightscribe has a 64-bit version so there is no need to install it from a terminal with the ignore architecture flag.[/SIZE]

---

