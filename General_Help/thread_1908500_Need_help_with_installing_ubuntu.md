---
title: "Need help with installing ubuntu"
date: 2012-01-13
forum: General Help
---

### Post by scarface87 on 2012-01-13
Hey.

My laptop ****** up a few days ago so i downloade and installed SystemRescueCD on a USB stick and after that i remove my ubuntu and windows. So my problem now is a only have SystemResuceCD on my USB stick and i dont know how i can install Ubuntu from that. Can anybody help?

---

### Post by carl4926 on 2012-01-13
Can you use a web browser and download Ubuntu with the rescue cd?
Save it to your HD
Do you have more than One USB pen drive?

---

### Post by scarface87 on 2012-01-13
> **carl4926 said:**
> Can you use a web browser and download Ubuntu with the rescue cd?
Save it to your HD
Do you have more than One USB pen drive?

Yes the rescue has firefox and i have download the ubuntu ISO, but i dont know how i can install it onto my harddrive because i have had tried to download unetbootin but SystemRescue wont let me run it.
Shall i just extract the ISO to my empty harddrive?????
No its the only USB stick i have :(

---

### Post by carl4926 on 2012-01-13
You are in a bit of a fix

By far the simplest solution would be to get/borrow another USB pen drive. (And you can't/dont' have a CD/DVD drive?)

I'm wondering if this SystemRescue CD runs in the RAM? Like Parted Magic can?
Which would mean, if it does. You could format the USB you have
Then 'dd' the ubuntu .iso to the USB

---

### Post by scarface87 on 2012-01-13
> **carl4926 said:**
> You are in a bit of a fix

By far the simplest solution would be to get/borrow another USB pen drive. (And you can't/dont' have a CD/DVD drive?)

I'm wondering if this SystemRescue CD runs in the RAM? Like Parted Magic can?
Which would mean, if it does. You could format the USB you have
Then 'dd' the ubuntu .iso to the USB

Yeah quite a fix hehe.
No i dont have any CDorDVD drive. So i gues a will be looking for a USB stick with Ubuntu on but its gonna be hard. What do you mean when you say download to usb???? Shall i just extract the ISO file onto the USB Stick without unetbootin or any other usb creator and then boot from the USB stick and install it???

---

### Post by carl4926 on 2012-01-13
No
You said you have the .iso save to your HD

I was suggesting, that if this SystemRescue CD thing runs from the RAM (That would mean, once it's up and running it doesn't need the USB any more). You could format the USB and use 'dd' to write the Ubuntu .iso

If you don't understand what I am talking about I suggest you just wait.
Especially because, once you try 'dd' and if it doesn't work. You don't have anything on your USB any more.
Unetbootin has requirement that probably are not met in the SystemRescue CD

Someone else though may have a better idea than me. Hence my suggestion you don't rush in to anything.


I do see this:

** Main boot options**

 Here are the most common boot options: 
 
[LIST]
[*]**docache**: copy the files to RAMfs. permits the SysRescueCD to be ejected and another disc inserted.  Programs load faster.
[/LIST]
That's what I am talking about.
You can do that and then format the USB** (But once you do that, we only have one go to 'dd' the Ubuntu .iso to the USB)**

Gparted will format the USB to FAT
Open a terminal and do:
```
fdisk -l
```Probably sda will be your main HD
and sdb the USB

to dd the iso you need to open a terminal in the directory containing the .iso and then do:

 ```
dd if=image.iso of=/dev/sdb bs=4M;sync

```(Replace image.iso with the name of the ubuntu .iso)
This process takes a while.


If you don't understand anything here. Ask

---

### Post by scarface87 on 2012-01-13
> **carl4926 said:**
> No
You said you have the .iso save to your HD

I was suggesting, that if this SystemRescue CD thing runs from the RAM (That would mean, once it's up and running it doesn't need the USB any more). You could format the USB and use 'dd' to write the Ubuntu .iso

If you don't understand what I am talking about I suggest you just wait.
Especially because, once you try 'dd' and if it doesn't work. You don't have anything on your USB any more.
Unetbootin has requirement that probably are not met in the SystemRescue CD

Someone else though may have a better idea than me. Hence my suggestion you don't rush in to anything.


I do see this:

** Main boot options**

 Here are the most common boot options: 
 
[LIST]
[*]**docache**: copy the files to RAMfs. permits the SysRescueCD to be ejected and another disc inserted.  Programs load faster.
[/LIST]
That's what I am talking about.
You can do that and then format the USB** (But once you do that, we only have one go to 'dd' the Ubuntu .iso to the USB)**

Gparted will format the USB to FAT
Open a terminal and do:
```
fdisk -l
```Probably sda will be your main HD
and sdb the USB

to dd the iso you need to open a terminal in the directory containing the .iso and then do:

 ```
dd if=image.iso of=/dev/sdb bs=4M;sync

```(Replace image.iso with the name of the ubuntu .iso)
This process takes a while.


If you don't understand anything here. Ask

Okay. Yes, i understand. i know dd and im now trying to find out if SystemRescueCD runs in RAM.. Thank you very much for your help. i will write back when i know more.

It does not run in RAM but there is an option when i boot up DOCACHE. so now im downloading ubuntu ISO again and formatting the USB stick and install ubuntu on that.

Thank you very much. :-)

---

### Post by carl4926 on 2012-01-13
> now trying to find out if SystemRescueCD runs in RAM..It does

I quoted it to you from their site
> **Main boot options**

 Here are the most common boot options: 
 
[LIST]
[*]**docache**: copy the files to RAMfs. permits the SysRescueCD to be ejected and another disc inserted.  Programs load faster.
[/LIST]


---

