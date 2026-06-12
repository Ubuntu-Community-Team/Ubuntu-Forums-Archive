---
title: "Help: New to Linux and Ubuntu fresh 9.10 install locks up after desktop loads"
date: 2010-03-27
forum: General Help
---

### Post by guybryant on 2010-03-27
Hi I am new to Linux and have started with Ubuntu 9.10.
I currently  have a valid Windows XP Professional installation on my computer and I  now have Ubuntu 9.10 as well.

I downloaded Ubuntu 9.10 from  [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and I used unetbootin to create  a bootable usb flash drive from which to install Ubuntu 9.10.

I  installed it on my friends computer last night and we had no problems  getting everything to work, it was awesome.

After my wife saw  that Ubuntu wasn't difficult, she said that it was ok to install it on  our home computer.

The installation went very smooth, but now I  have a problem.

A few seconds after Ubuntu boots up (this is  after I log in [I set it up so that I don't need to type my password to  log in]) my mouse and keyboard die, and the entire system locks up.

This  is without me trying to run any applications.
I know that with  Windows, installing updates can fix many problems so I thought I would  try that.

The furthest I have come to installing updates before  the system freezes, is the password box after I click on update manager.

I  have no idea why this is happening and after about an hour of quality  time with Google I find myself being introduced to a world that is most  unfamiliar.

I have read about something called Jaunty, and  Karmic, and the only that has made any sense to me at all is the  possibility of an incompatible graphics driver for which the solution  looked like a foreign language. 

I did a hard reset 4 times now,  after the most recent of which I have left the system in it's frozen  state for the past hour and fifteen minutes.

I tried to use the  "Try Ubuntu without making changes to your system" option of the Live CD  (which is a usb stick for me...) and it too freezes shortly after the  desktop loads.

I will list all the hardware in my computer,  submit this plea for help and then wait for help. I can just go back to  XP but I really like the concept of Linux in general and Ubuntu  specificaly, so it is worth my time to try and make it work.

I am  willing to do whatever might work, I can format the entire hard drive  and then only have an Ubuntu installation if that will help, or if I  need to use a different version of Ubuntu or maybe I need to downgrade  my kernel what ever that means.
I have already back up everything  that I want off my computer.


Hardware:
-Computer: Compaq  Presario PC SR501NX
-Processor: Intel Celeron D Processor 360
-Memory:  2gb (2 1gb sticks)
-Hard drive: 120gb (xp partition is 20gb and I am  using about 17gb, Ubuntu 9.10 is        100gb)
-Graphics: Intel  Graphics Media Accelerator 950

That is all the information that  is listed on the front of my computer, if you need to know something  else, I can log in to XP and find it for you.

I am usually pretty  good at diagnosing computer issues, but being unfamiliar with Linux and  Ubuntu, and not being able to even use my keyboard/mouse to do  anything, I am just stuck.

p.s. I can enter into the recovery  mode without any problems and the keyboard works just fine in there

Thanks  for your time and effort and I hope to be a knowledgeable, contributing member of  this forum in the near future...assuming I can get Ubuntu working.

---

### Post by krismatth3 on 2010-03-27
When the computer is booting, at the grub prompt there's an option to press Escape - press it and boot into recovery mode.

You should get a text only console. You can try these command

```
# apt-get update 
# apt-get upgrade
```

with any luck, that will update your system. If that solves your problem is another story.. :)

---

### Post by stratus75 on 2010-03-27
if it is happening with both the installed version and the live version maybe you could try verifying the downloaded iso with the md5sum( if you haven't already that is?) heres a link for doing that on a XP box
[http://www.cyberciti.biz/faq/linux-verify-md5-checksum-of-iso-file-using-windows-xp/](http://www.cyberciti.biz/faq/linux-verify-md5-checksum-of-iso-file-using-windows-xp/)

Also would be worth checking the usb drive itself isn't damaged scan-disk or some other prog ?? by the way did you use the same usb drive to install the Ubuntu on your friends computer ??
If so that may rule out all of the above?

---

### Post by guybryant on 2010-03-28
I did both the update and the upgrade and as you suspected, it isn't fixed.

Yes, I used the usb stick to install Ubuntu 9.10 on my friends computer.
I also used it to install ubuntu on another computer today and neither my other computer nor my friends computer have any issues.

I decided to reinstall and then update and upgrade Ubuntu 9.10 on my computer again.

But the it is still locking up just after the desktop loads.

Can somebody tell me how to change my graphics settings so that I can rule that variable out?

Thank you

---

### Post by snowpine on 2010-03-28
Try disabling your Compiz desktop effects.

Right click on the desktop, select "Change Desktop Background". Click "Visual Effects", select the "none" option.

---

### Post by guybryant on 2010-03-28
I will try that just as soon as my memory check completes.

But I don't think I have enough time to do that before the computer freezes.

Is there a way to permanently disable that from the recovery console?

---

### Post by guybryant on 2010-03-28
Well I did a check for defects on my hard drive and a memory test.

Now I can't get the desktop to even load...

---

### Post by 4manifold on 2010-04-01
I don't have any help to offer, but I am experiencing the exact same problem.  I am running (or trying to run) Ubuntu 9.10 in a dual-boot situation with Windows 7.  Hardware:

Intel Core i3 540
Gigabyte h55m-ud2h motherboard
4gb ddr3 ram
1tb hitachi deskstar hard drive

---

### Post by guybryant on 2010-04-04
Success!

I have no idea what compiz is, but it must have been my problem.

This is how I made my Ubuntu work on my computer:

First I had to boot into recovery mode.

Then I used cd (stands for change directory) to get to here:
 /.gconf/desktop/gnome/applications/window_manager/

So I did:
cd .gconf
cd desktop
cd gnome
cd applications
cd window_manager

You don't have to do one cd at a time, cd .gconf/desktop/gnome/applications/winow_manager should work.

Then I typed dir (it shows you the contents of your current file.
I saw a file called %gconf.xml

I typed sudo nano %gconf.xml

sudo lets you do stuff as the root user, root is similar to Administrator in Windows
nano lets you edit the contents of a file 
%gconf.xml is a file that affects display settings, but I don't know why or how..

So basically that code means that you want to edit %gconf.xml as the root user.

This took me to another text only screen which was the contents of %gconf.xml.
On this screen the word compiz appeared twice.
I deleted both of those words and replaced them with the word metacity.

Again I don't know what compiz (or metacity) is.

Then you have to hold ctrl (control) and press x to leave that screen.
Be sure to save your changes when it asks.
When you are able to type again type sudo reboot to restart your computer.

I booted up in the normal desktop environment and I haven't had any problems since.


To give credit where it's due, I found this solution here:
[http://ubuntuforums.org/showthread.php?t=681048](http://ubuntuforums.org/showthread.php?t=681048)

I only typed this out to make it easier for other Linux newbs like me.

I would like for someone with power to make either my post or Bruce M.'s pose, (or even ebash whoever that is if s/he wants to write something out) available as a solution to some freezing issues.

I would even be ok with someone typing a more professional guide and that being available in some kind of help section.

I have seen many complaints that are similar to mine and I think this would help.

Thanks and I hope you get the help you need soon.

---

