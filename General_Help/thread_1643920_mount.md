---
title: "mount"
date: 2010-12-12
forum: General Help
---

### Post by jim allAn on 2010-12-12
[RIGHT]:(   I have been trying to mount a USB memory stick in my Ubuntu 10.04 and got as far as having a folder on my desktop called flash.  It should represent the drive but it is locked and I can't unlock it.  It has been suggested I type sudo nautilus in a terminal to get root privileges in a file manager to possibly change privileges which are now locked out.  The trouble with that is when I get to my desktop there is nothing.  Where did that file go to or why isn't it visible.  I don't want to start all over after all I have gone through to get this far.
 
[/RIGHT]

---

### Post by tajiknomi on 2010-12-12
> **jim allAn said:**
> [RIGHT]:(   I have been trying to mount a USB memory stick in my Ubuntu 10.04 and got as far as having a folder on my desktop called flash.  It should represent the drive but it is locked and I can't unlock it.  It has been suggested I type sudo nautilus in a terminal to get root privileges in a file manager to possibly change privileges which are now locked out.  The trouble with that is when I get to my desktop there is nothing.  Where did that file go to or why isn't it visible.  I don't want to start all over after all I have gone through to get this far.
 
[/RIGHT]


[SIZE=2]1st of all open up Gparted and unmount the flash drive if it is mounted,
next step > in terminal type "sudo mount /dev/sd***XY*** /dev/flash"

Replace ***XY*** with your flash drive...., and see, if its mounting then....and so that you can access .....
[/SIZE]

---

### Post by jim allAn on 2010-12-12
> **tajiknomi said:**
> [SIZE=2]1st of all open up Gparted and unmount the flash drive if it is mounted,
next step > in terminal type "sudo mount /dev/sd***XY*** /dev/flash"

Replace ***XY*** with your flash drive...., and see, if its mounting then....and so that you can access .....
[/SIZE]
    I did not expect an answer so quick.  I am doing an experiment with the drive selected as the dld to folder.  It has been suggested I try Mint so I am dlding it now.  It should be going to the usb drive but at over 40 percent dlded nothing shows up, which might be ok.  I would like to let it finish so I can see what happens.
   I have never used gparted and it did nothing when I first tried running it.  I checked synaptic and it appeared I did not have it yet so I went through the procedure and it is installed.  I know nothing about it but upon looking in the gparted menu I found my device listed and clicked it.  From what I see it is mounted.  I don't know yet if I can do anything with the drive or with gparted.  While I am waiting for mint to dld is there any interesting stuff I could see in gparted?

---

### Post by jim allAn on 2010-12-12
> **tajiknomi said:**
> [SIZE=2]1st of all open up Gparted and unmount the flash drive if it is mounted,
next step > in terminal type "sudo mount /dev/sd***XY*** /dev/flash"

Replace ***XY*** with your flash drive...., and see, if its mounting then....and so that you can access .....
[/SIZE]
    Well mint is finished but there is still nothing showing in flash.  Nor is there a big enough file containing the word mint anywhere I can see.  If I want to use it I can just click the file on the dlds manager.  I guess I can go ahead and follow your instructions in the morning when there are fewer cobwebs in my brain.

---

### Post by jim allAn on 2010-12-12
I forgot to mention I know nothing about gparted so anything you could tell me about how to do what you want would be very helpful.  So far I don't see anything.  I have read a lot of the instructions.

---

### Post by Krytarik on 2010-12-13
Most probably you have to make an entry for the drive in the file /etc/fstab, read here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

A good clue about what options you have to include get you the entries of the file /etc/mtab if the drive is mounted.

manual of Gparted: [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

Report back if you have further questions!

---

### Post by jim allAn on 2010-12-13
> **tajiknomi said:**
> [SIZE=2]1st of all open up Gparted and unmount the flash drive if it is mounted,
next step > in terminal type "sudo mount /dev/sd***XY*** /dev/flash"

Replace ***XY*** with your flash drive...., and see, if its mounting then....and so that you can access .....
[/SIZE]
    I am sorry but I can't see that gparted will allow me to unmount the sdc  and or get rid of flash.  Could you go into more detail to unmount it?

---

### Post by tad1073 on 2010-12-13
> **jim allAn said:**
> I am sorry but I can't see that gparted will allow me to unmount the sdc  and or get rid of flash.  Could you go into more detail to unmount it?
open a terminal and type:
```
sudo umount /dev/whatever
replace whatever with you drive letters etc.

```

---

### Post by tad1073 on 2010-12-13
> **jim allAn said:**
> :( The trouble with that is when I get to my desktop there is nothing.  Where did that file go to or why isn't it visible.[RIGHT]
[/RIGHT]
 
After you enter sudo nautilus did you browse to /home/"YourUsername"/Desktop?

---

### Post by jim allAn on 2010-12-13
> **tad1073 said:**
> open a terminal and type:
```
sudo umount /dev/whatever
replace whatever with you drive letters etc.

```
    That's what I thought I would need to do in this case.
   I don't believe it, but unmount says /dev/sdc is not mounted.  No wonder gparted didn't give me any options to unmount.  In the future I will believe it.

---

### Post by jim allAn on 2010-12-13
> **tad1073 said:**
> [RIGHT]
[/RIGHT]
 
After you enter sudo nautilus did you browse to /home/"YourUsername"/Desktop?
    I hadn't, but just did and as expected because I had deleted it, there was nothing.
   Now I can go to the next step.

---

### Post by jim allAn on 2010-12-13
> **tajiknomi said:**
> [SIZE=2]1st of all open up Gparted and unmount the flash drive if it is mounted,
next step > in terminal type "sudo mount /dev/sd***XY*** /dev/flash"

Replace ***XY*** with your flash drive...., and see, if its mounting then....and so that you can access .....
[/SIZE]
    At first the results were "mount: can't find /dev/sdc/dev/flash in /etc/fstab or /etc/mtab."  But then I figured there should be at least a space between /dev/sdc and /dev/flash.  Adding the space got "mount: mount point dev/flash does not exist."  Don't I first have to mkdir flash somewhere?

---

### Post by tad1073 on 2010-12-13
> **jim allAn said:**
> At first the results were "mount: can't find /dev/sdc/dev/flash in /etc/fstab or /etc/mtab."  But then I figured there should be at least a space between /dev/sdc and /dev/flash.  Adding the space got "mount: mount point dev/flash does not exist."  Don't I first have to mkdir flash somewhere?
yup

---

### Post by tad1073 on 2010-12-13
> **jim allAn said:**
> I hadn't, but just did and as expected because I had deleted it, there was nothing.
   Now I can go to the next step.
sudo nautilus opens root's home folder, you can either enter 
```
sudo nautius /home/UserName/Desktop
```
or browse to it from within nautilus.

---

### Post by ajgreeny on 2010-12-14
All this talk of **sudo nautilus** is very worrying, firstly because it should not be needed to do anything with a flash thumb drive, and secondly because you must never use **sudo** for gnome applications such as nautilus, or anything else; it must be **gksu**, or **gksudo**, both of which in effect do the same thing, ie give you root permissions within nautilus.  Suso is fort cli terminal apps only.  See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for the details.

When you plug in a USB flash drive, it should mount straight away, and appear on your desktop by default,  If it does not something must be wrong with your settings, or the drive, or perhaps the usb port.

To settle some of the unanswered questions in my mind, please attach the USB drive and run ```
sudo fdisk -l
``` (lower case L at the end, not 1) in terminal, and report the output back here.

---

