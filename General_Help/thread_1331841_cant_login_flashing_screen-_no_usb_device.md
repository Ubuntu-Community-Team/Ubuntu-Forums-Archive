---
title: "cant login flashing screen- no usb device"
date: 2009-11-19
forum: General Help
---

### Post by rikskelton138 on 2009-11-19
I am using ubuntu 9.10, I don't know what I did but when I try to start ubuntu it says "setting mode 1152 x 864 failed using mode 1024 x 768" the screen continuously flashes and I can't log in. I have a gforce 8600 if that matters. Anyone know whats going on here. I am stumped. I am a newb. I don't have a usb device plugged in.[/quote]

So I have searched more through the forums and help but I still can't resolve this issue. It was working fine when i logged off then the above happened. I won't mind just starting over either I just installed it last week and I don't have anything important on it yet. I have been just playing around with ubuntu. I have ubuntu installed on a partitioned hard drive. Any help?:)

---

### Post by wrgb2 on 2009-11-19
When do you get the flashing screen, when Ubuntu is booting or right after you enter your username and password?

---

### Post by rikskelton138 on 2009-11-19
When it is booting. It asks me for my name and password but the keyboard only works between flashes so its impossible to enter the password. It enters a screen that is just black with white type.

---

### Post by wrgb2 on 2009-11-19
Try ctl-alt-F1 and see if that brings up a text login screen.

---

### Post by wrgb2 on 2009-11-19
If you can do a text login, try:

sudo /etc/init.d/gdm stop

and then

sudo dpkg-reconfigure xserver-xorgv

and restart your pc.

---

### Post by Tiganjero on 2009-11-28
I have the same problem. Everything was working perfectly, but after an update few days ago, I started getting that message and the flashing screen, instead of the login window. It has got to do something with the update, since after i rebooted this problem appeared...

Cheers

---

### Post by Montebest on 2009-11-28
same problem here, i cant press f1 it dosent work

---

### Post by Tiganjero on 2009-11-29
bump

---

### Post by Tiganjero on 2009-11-30
Buuuuump :P

---

### Post by EmlynK on 2009-11-30
I have the exact same problem. I haven't done an upgrade, this is just the first time I've installed it. 

This is what I see, amongst all the blinks/flashes:

[b]usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768

Ubuntu 9.10 hp-laptop tty1

hp-laptop login:[/b]

As stated above, I can't enter the password as the screen is blinking/flashing too fast. 

I am also new to Ubuntu, so do not know how to solve this. Any help will be highly appreciated. Thank you.

---

### Post by bertmanphx on 2009-11-30
Hello,
When you boot, hold the shift key so that the GRUB menu shows.
Read the info at the bottom of the screen.
Modify the boot line to say "nosplash nomodeset"  See if that allows you to boot.
It sounds as if there is a problem with either Usplash, Kernel Mode Setting, or both.  Let me know if you need help.

bertmanphx

---

### Post by EmlynK on 2009-11-30
Ahh right. I shall try that. Thank you for the advice. :)

EDIT:

As I'm new to this, I'm unsure which line to edit. This is what I get when I edit the commands for booting:
[b]recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 31e7fd80-d64a-4a5f-a2b5-629327742\
d8e
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=31e7fd80-d64a-4a5f-a\
2b5-629327742d8e ro  quiet splash
initrd /boot/initrd.img-2.6.31-14-generic[/b]

Where abouts do I make that change? "/

---

### Post by Tiganjero on 2009-11-30
Even if you manage to enter your username and password, it won't solve your problem... I tried it...

Cheers,
George

---

### Post by ArgentStar on 2009-11-30
Just like to add that I've also had this problem with Xubuntu 9.10 on an old PC (500MHz / 256MB RAM).  It's fine after just installing from the CD - downloaded and burned about 2-3 weeks ago - but after updating it says:

usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768

...each time I login.  Once before the login chooser comes up, then it does it again after entering password and clicking Log-In, flickers a bit, then goes back to the login chooser.  Just keeps going in a loop like that so I couldn't login to a desktop. (Not tried the text-login yet.  Thanks for the tip - will give that a try if the problem reoccurs.)

So far it's fine as long as I don't update, but I'm curious as to when/how this'll be fixed.  Thankfully it doesn't seem to have effected this PC (medium-spec / Ubuntu 9.10).

---

### Post by bertmanphx on 2009-11-30
> **EmlynK said:**
> Ahh right. I shall try that. Thank you for the advice. :)

EDIT:

As I'm new to this, I'm unsure which line to edit. This is what I get when I edit the commands for booting:
[b]recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 31e7fd80-d64a-4a5f-a2b5-629327742\
d8e
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=31e7fd80-d64a-4a5f-a\
2b5-629327742d8e ro  quiet nosplash nomodeset
initrd /boot/initrd.img-2.6.31-14-generic[/b]

Where abouts do I make that change? "/

Ok, I modified the line for you.  
it now reads nosplash nomodeset

Let us know if this works for you.

bertmanphx

---

### Post by EmlynK on 2009-12-03
Thank you. Sorry for the late reply, I've been really busy with my A Levels.

Unfortunately it doesn't work. It lists what it's doing, and then when it comes to entering the login name again, it flashes like before. "/

---

### Post by doug-M on 2010-02-05
I managed to get it to stop flashing for a while, not exactly sure how but try switching ttys.

try this a bunch of times
ctrl-alt-F7
ctrl-alt-F1

You might also try a remote ssh into the machine.

Once my flashing stopped I did discovered there was an /etc/X11/xorg.conf file that was not complete. Actually I noticed when this command failed:
startx

So I moved the xorg.conf and did startx to get a desktop.
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.ORIG
startx
After a reboot it went right into MythTv.

I imagine that X should probably be reconfigured properly.

---

