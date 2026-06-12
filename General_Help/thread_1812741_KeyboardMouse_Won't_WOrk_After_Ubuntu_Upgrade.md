---
title: "Keyboard/Mouse Won't WOrk After Ubuntu Upgrade"
date: 2011-07-26
forum: General Help
---

### Post by LonelyAspie on 2011-07-26
The other day, I upgraded my Mom's and My Dad's computers (both identical)  from Ubuntu 10.10 to 11.04. ON my Dad's computer, the keyboard and mouse don't work at all. My Dad uses a different keyboard and mouse then the one my Mom. THey both use Logitech mice (different models).

My Dad's keyboard is Seal Shield USB 2.0 washable and his mouse is a Logitech V220.

---

### Post by enimeizoo on 2011-07-26
Well, that is why people advice to make a fresh install rather than an upgrade. 

Does it work fine with a 11.04 live cd ?

---

### Post by rts on 2011-08-08
I am in the same situation.  enimeizoo's facile response notwithstanding (oh! how stupid of me to click "Upgrade" when it pops up every 24 hours, several months after the release!) I've been unable to find a solution.

Keyboard and mouse worked perfectly in 10.10.  They also work perfectly when using the Live CD.  The keyboard works perfectly in the BIOS settings screen.

However, once Linux gets a hold of the system, nothing works.  Num Lock and Caps Lock do not light up;  SHIFT and/or ESC do not bring up the Grub boot menu; at the login screen, I can't do anything except press the Power button to power down.

Using different USB slots doesn't help.  Using a PS/2 keyboard doesn't help.  The mouse has power (the LEDs come on) so I know the USB is "alive".

In short, a very disappointing Ubuntu upgrade experience.

---

### Post by enimeizoo on 2011-08-08
I was probably in a bad day, there is no need to be mad at me for that. Upgrades do go wrong more often than not in a way or another, but it is not necessarily that disturbing. But there was no information at all, and I did ask some precision, for my defense. Anyway, please forgive that.

We also need to know what you can do. Not much, obviously, but I need to know if you are logged in, if you can switch to a virtual terminal (ctrl+alt+F1), and if so, if keyboard works there. Do the [magic keys]("http://en.wikipedia.org/wiki/Magic_SysRq_key") work? 

Do you happen to have a backup of your file system before upgrade (especially the xorg.conf file, which doesn't exist anymore, or rather has been split in different files in 11.04)?

I guess the liveCD is a 10.10 one, but my question was, implicitly, about a 11.04 one. There is no reason it wouldn't, but having one and making sure it works fine  would allow you to use its configuration files and hopefully solve this quite easily.

But if you have an efficient way to backup your data, and if you didn't tweak your system too much, you might consider to just make a fresh 11.04 install.

Thing is that since it doesn't work in grub, it shouldn't be a linux configuration issue. At least, not only. I don't think any kernel is loaded when grub loads. So regarding that, it should be more of a BIOS issue.
But since it does work with another version, that should exclude the BIOS problem. 

Googling around brought solutions fixing keyboard not working in grub, but working in linux. It is about a usb keyboard legacy option in the BIOS. I don't see how it could help your linux issue, aside from allowing you to boot in text mode to find out if it is a X or a kernel/driver issue.

I hardly think two problems happen at the same time without being somewhat related, so as long I I'm not sure why grub not detecting keyboard makes linux not detecting it, I'm pretty much blind. Well, the upgrade is likely to bring several problems at once, but still.

Well, I guess it is not as helpful as you would like it to be, but it is just weird.

---

### Post by rts on 2011-08-09
> **enimeizoo said:**
> 
We also need to know what you can do. Not much, obviously, but I need to know if you are logged in,


Keyboard doesn't work; I cannot enter any credentials.

> 
 if you can switch to a virtual terminal (ctrl+alt+F1),


Nope.

> Do the [magic keys]("http://en.wikipedia.org/wiki/Magic_SysRq_key") work? 

Nope.

> 
Do you happen to have a backup of your file system before upgrade (especially the xorg.conf file, which doesn't exist anymore, or rather has been split in different files in 11.04)?


Nope.  Disappeared in the update.

> 
I guess the liveCD is a 10.10 one, but my question was, implicitly, about a 11.04 one.


Nope.  Live CD is 11.04 and it works perfectly.

> 
 There is no reason it wouldn't, but having one and making sure it works fine  would allow you to use its configuration files and hopefully solve this quite easily.


After booting the 11.04 live cd and mounting my hard drive's partitions, there is no significant difference between the config files on my hard drive and the ones used in the Live CD environment.

> 
But if you have an efficient way to backup your data, and if you didn't tweak your system too much, you might consider to just make a fresh 11.04 install.


Looks to be my only choice.

> 
Well, I guess it is not as helpful as you would like it to be, but it is just weird.

Weird but not uncommon; I've found a number of threads on these boards with the same symptoms.

---

### Post by rts on 2011-08-10
Here's how I solved this problem:

Boot the Live CD.

Switch to a terminal with Ctrl-Alt-F1.

Follow these instructions to mount your HD and get all the necessary /dev entries in a chroot enviornment:

[http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)

Next, edit /etc/default/grub and comment out the line GRUB_HIDDEN_TIMEOUT=0

Run update-grub

Reboot.  Now the SHIFT key *will* bring up the grub menu; hold SHIFT after your BIOS POST.

Select an older kernel.  For me, 2.6.38-8 worked.

Your keyboard should now work.  Go and do an update with the update manager to get the latest kernel.

Edit /etc/default/grub and put the line GRUB_HIDDEN_TIMEOUT=0 back in.  Run update-grub.  Reboot.

Worked for me.  Your mileage may vary.

---

