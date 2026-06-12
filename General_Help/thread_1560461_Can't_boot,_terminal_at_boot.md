---
title: "Can't boot, terminal at boot?"
date: 2010-08-24
forum: General Help
---

### Post by zachHH on 2010-08-24
Hey there,

I just did a fresh install of ubuntu 10.04 on my dual boot Vista/Ubuntu laptop. Everything was going fine, until I tried to boot into Ubuntu. The splash screen stops and a white terminal pops up in the upper left hand corner, and it doesn't boot,

I don't know what's going on here, I typed exit, it brings me to the log in screen where I type in my password, and it brings up the white terminal things again.

I tried searching, and all I could find was maybe I am booting into terminal or something? I'm not sure, I just really need help getting into Ubuntu

Thanks!
Zach

---

### Post by amsterdamharu on 2010-08-24
When it's done booting could you press control + alt + F1, this should give you a black dos like screen where you can login.

After login can you type the following commands?
```
sudo service gdm start
```It will ask you for your password again.
That should bring you to a graphic login screen, if not please post any output you get? Then press control + alt + F7 and see if there is anything useful there.

What Ubuntu version did you install (what iso file did you use)?

---

### Post by drewbub on 2010-08-24
Seems like X is starting but gnome isn't.


Try to start gnome from the terminal or install it

I think it is gdm3

---

### Post by zachHH on 2010-08-24
I was able to get to the virtual terminal and log into ubuntu 

I typed gdm stop, I gave my password, and it posted gdm stop/waiting. But nothing happened.

Ctrl+Alt+F7 shows me nothing but a blinking cursor in the top left and a black screen.

I installed Ubuntu 10.04 32-Bit from the official free CD from canonical given to me from a friend.

---

### Post by zachHH on 2010-08-24
> 
Seems like X is starting but gnome isn't.


Try to start gnome from the terminal or install it

I think it is gdm3


How would I install/start it from the terminal ctrl+alt+F1? I'm really new to ubuntu, well I have used it a bunch but never had to go through this kinda stuff :(

---

### Post by zachHH on 2010-08-24
> Last edited by amsterdamharu; 10 Minutes Ago at 08:11 PM.. 					 					 						Reason: Sorry wrong command 					 				

Ok, I tried again using START in the command instead of STOP. I get this:

```
 start: Job is already running: gdm
```

---

### Post by drewbub on 2010-08-24
> **zachHH said:**
> I was able to get to the virtual terminal and log into ubuntu 

I typed gdm stop, I gave my password, and it posted gdm stop/waiting. But nothing happened.

Ctrl+Alt+F7 shows me nothing but a blinking cursor in the top left and a black screen.

I installed Ubuntu 10.04 32-Bit from the official free CD from canonical given to me from a friend.

EDIT: SEE NEXT POST

Im on my phone so I can't say for sure bit trybto start with
sudo service gdm start 
Or
sudo service gdm3 start

If not installed try
audi apt-get install gdm3

---

### Post by drewbub on 2010-08-24
Ok i just logged into my machine...

Try first:
```

sudo service gdm restart

```

if that doesnt work then maybe reinstall gnome:
```

sudo apt-get purge gdm
sudo apt-get install gdm

```

Also, what kind of computer is this? What is the graphics card?

---

### Post by zachHH on 2010-08-24
I found a similar thread, and the problem stayed unresolved.

I typed gdm start, and it said it was already running. I tried to install it, it said already installed.

I tried restart, it said Unknown instance.

I  purged and then reinstalled gdm. and now I get a splash screen that looks like it's loading. but it stays on that screen loading and never goes any further.

---

### Post by drewbub on 2010-08-24
> **zachHH said:**
> I found a similar thread, and the problem stayed unresolved.

I typed gdm start, and it said it was already running. I tried to install it, it said already installed.

Try purge gdm then install

---

### Post by zachHH on 2010-08-24
Sorry, I edited late.

I tried to purge and reinstall gdm, and now I get an endless splash screen.

---

### Post by zachHH on 2010-08-24
Now i'm getting my original question, I get  a white terminal at boot again.

Do you think if i just reinstalled ubuntu this would happen again because of my graphics card? Or was it just a random glitch or something.

It's a toshiba satellite a215-s7428 with ati radeon, im not sure of any specifics.

---

### Post by drewbub on 2010-08-24
You could try a reinstalling it might help..

Boot a livecd and see if you can get to the desktop.

Also, if you are using the 64 bit version you should try the 32 bit.

You can check by running

uname -r

---

### Post by zachHH on 2010-08-24
I know for sure im using the 32 bit version, but on the live cd i can access the desktop and install without any problems.

I'll guess i'll just reinstall. I hope this doesn't become a problem again in the future

Thanks for your help!

Zach

---

### Post by amsterdamharu on 2010-08-25
Sorry this is a bit late but found someone with a similar problem, they fixed it by installing a newer version of gdm:

[http://ulyssesonline.com/2010/08/14/gdm-does-not-start-in-ubuntu-10-04/](http://ulyssesonline.com/2010/08/14/gdm-does-not-start-in-ubuntu-10-04/)

Basically they removed gdm and installed gdm2:
```

sudo apt-get purge gdm
sudo add-apt-repository ppa:gdm2setup/gdm2setup
sudo apt-get update sudo apt-get install python-gdm2setup

```

---

### Post by zachHH on 2010-08-25
Thanks for that article, I am already reinstalling ubuntu but if I have this problem again I know what to try.

Thanks for all your help!

---

### Post by drewbub on 2010-08-25
Let us know if the reinstall works

---

### Post by amsterdamharu on 2010-08-25
Maybe a misconfigurated xorg, can you try this command after you've logged in on tty1 (press control + alt + F1)?
```
sudo dpkg-reconfigure xserver-xorg
```
Then restart the computer to see if that helped (press control + alt + delete).

could you post the output of:
> lspci | grep VGA
and
```
sudo lshw -C video
```
Sorry that this is becoming a big pain for you by now, I think there is some hardware in your computer that requiers some manual work. Probably the ATI card.

---

### Post by amsterdamharu on 2010-08-25
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

That link might help some, the basic installation will not work of course since it requires you to have a graphic user environment but if you know what videocard you have you might get somewhere with the more detailed instruction part.

---

### Post by uim on 2011-11-28
I have the same problem. 

I have Ubuntu 10.10 installed in a VM (Virtualbox) on a Win7 64 bit host system.  It has been working fine for months, but this morning I fired it up and I first get the normal login screen, but after logging in, I get a white command prompt box in the top left corner.  I tried the suggestions for purging and reinstalling gdm and reconfiguring xorg.  Neither helped.  I still get the white box.  I have been using this installation on an almost daily basis for almost a year, and then this suddenly happened this morning.

Any ideas?

---

### Post by uim on 2011-11-30
I just wanted to post back here that I ended up reinstalling after trying everything I could think of to fix it.

---

### Post by oldos2er on 2011-11-30
Closed, necromancy.

In the future you might have better luck finding an answer by starting a new thread.

---

