---
title: "How to turn off system beeps"
date: 2010-06-04
forum: General Help
---

### Post by DJonsson2008 on 2010-06-04
My pc speaker is unplugged, so this question is about system beeps
making their way to my soundcard speakers/headphone output.

Using Gnome Mixer I can see that PC Speaker is muted and volume 100% down.

I've a file in /etc/modprobe.b/blacklist that contains the line blacklist pcspkr.

Still though I get these annoying system beeps.

This is on my production machine I'm using Hardy 8.4 LTS, 
my MB is of Intel 946 flavor.

---

### Post by mike555 on 2010-06-04
to disable the beeps you can try these two commands (one after the other):

Code:

sudo rmmod pcspkr

and then this:

Code:

echo 'blacklist pcspkr' | sudo tee -a /etc/modprobe.d/blacklist

Hopefully you will now be beep-free! If your system fails to shutdown, another way to shut down is to run this command:

Code:

sudo shutdown -h now

---

### Post by Jakiejake on 2010-06-04
> **djonsson2008 said:**
> my pc speaker is unplugged, so this question is about system beeps
making their way to my soundcard speakers/headphone output.

Using gnome mixer i can see that pc speaker is muted and volume 100% down.

I've a file in /etc/modprobe.b/blacklist that contains the line blacklist pcspkr.

Still though i get these annoying system beeps.

This is on my production machine i'm using hardy 8.4 lts, 
my mb is of intel 946 flavor.

bios?

---

### Post by DJonsson2008 on 2010-06-04
Thanks for your answers.

I've applied the suggestions above.
$ sudo rmmod pcspkr
returns ERROR: Module pcspkr does not exist in /proc/modules

but  echo 'blacklist pcspkr' | sudo tee -a /etc/modprobe.d/blacklist
does verify -- blacklist pcspkr

I also rebooted the machine to find actually on this box the PC Speaker
is plugged in. 

But the beeps in fact do not go through the PC speaker but go through my speakers and headphones.  

Its an intermitent 7 beep thing seems to sound sporatically about every hour.

The source may be as suggested the bios, trying to tell me something. 

Deal is though this machine runs cool and beeps or no beeps is stable as a rock and has been for 2 years during which time Ubuntu has also been beeping nearly every hour. On Windows it did not beep, although that alone won't drive me back to Windows.

I am as mystified by these beeps origin as I am in finding a Gnome, Ubuntu or Linux way of controlling them.

---

### Post by llawwehttam on 2010-06-04
Do what I do ( but at your own risk)

open the computer and rip the speaker out!

---

### Post by mike555 on 2010-06-04
Sounds like your computer trying to tell you something , you might do a memory check and/or Hard drive check (before it's to late)

although it might be something simple like your computer battery needs replacing (the little wafer one on the motherboard)

---

### Post by HiImTye on 2010-06-04
or you need to clean your system/video fans as they may be overheating and it might be a warning

---

### Post by DJonsson2008 on 2010-06-10
Thanks for all your suggestions. According to the Intel beep count for this machine - beeps which I believe to be start up
beeps, the 7 beeps emitted by this machine indicate faulty motherboard or processor.

The machine just beeped again running with CPU temp of a very
acceptable and well within the margins of 44 Celsius. 

I've cracked the case several times pushed cards down, lightly vacuumed the fans, checked for obstructions, loose screws bits
of metal and so on. 

Towards this beep mystery...

* These beeps come through the Alsa/Mixer Linux system
  and do not occur when windows is being run. 

* These beeps do not come through the PC speaker, and do
  not occur at startup but sporatically during daily use.

* I want to turn these sporatic alerts off, even if they
  indicate a valid alert 
  _Because 
   
   These beeps have been happening for 18 months now and the 
   machine remains stable as a rock under Ubuntu.

   I'm not interested in replacing the MB or CPU on this 
   machine until they have a complete meltdown.
 
I've tried the previous suggestions with no results.

Any further insights into how to turn these headphone/speaker beeps routed by Ubuntu greatly appreciated.

---

