---
title: "Webcam and Battery Issues."
date: 2010-12-26
forum: General Help
---

### Post by Hamatt on 2010-12-26
Hey all. I have a few things I would like fixed. I'm gonna go ahead and say I'm a pretty big noob at this ubuntu area. Had to break ties with windows and had no cash, so i chose Ubuntu. I did a clean install of Maverick on my laptop a month back and I've found a few pet peeves here and there. 

First, the battery problem. I usually run with my AC adapter plugged in, so the battery is almost always fully charged. However, if I unplug my adapter, I receive a message telling me I have only four minutes of battery left. I know I have more than four minutes and the assorted meters say that also. 

Next my webcam. Ubuntu must not have found it during install, so I can't use it at all. I would just download a driver, but my laptop manufacturer isn't graceful with support, much less driver downloads. I'm at a loss as to how to begin here.

I know that both of these could just be a driver update away from being solved, however I'm not sure how to do that. Everything is appreciated. Ask if you need more info. Thanks!

---

### Post by IWantFroyo on 2010-12-26
I don't know about the battery thing (keeping it plugged in does wacky stuff) but I'll try to help you with the webcam.
Go to System-Administration-Additional Drivers and see if it has anything webcam related. If it doesn't, then the driver is probably in a Linux kernel, so go to kernel.org (not kernel.com, that one's just a blank page with a little :Op in the corner[I'm serious]), and download the kernel.

---

### Post by Hamatt on 2010-12-26
hmmmmm. This has gotten me into far more than what I thought it would. When I got to the "make O=/home/name/build/kernel menuconfig" command as per readme file in the kernel installtion, i get :"
 *** Unable to find the ncurses libraries or the
 *** required header files.
 *** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** Install ncurses (ncurses-devel) and try again.
 *** 
make[1]: *** [scripts/kconfig/dochecklxdialog] Error 1
make: *** [menuconfig] Error 2"

So, I googled around and installed this ncurses. But, I noticed errors in it's install and now I still can't use it. Any suggestions?
By the way, I checked out kernel.com. IWantFroyo is right. That is wacky.

---

### Post by Casper35th on 2010-12-27
First what kind of laptop is it? The battery level indicator being wrong sounds like something to do with the power management.

---

### Post by Hamatt on 2010-12-27
It's an MSI A6005. For more on the webcam problem: this model has a button that turns the camera on and off. There is no light or indicator to tell whether it is on or off.

---

### Post by Ir0nMa1deN on 2010-12-27
For the webcam download Cheese from Ubuntu Software Center. I have the same battery issue as you but it updates by itself and shows up correctly after like a minute.

---

### Post by Hamatt on 2010-12-27
Tried the cheese suggestion. No dice. Thanks though!

---

### Post by Ir0nMa1deN on 2010-12-27
weird, did you try any other webcam applications to see if they work? if nothing does work, maybe your webcam isn't compatible.

---

### Post by Hamatt on 2010-12-27
I tried skype. No camera found their either.

---

### Post by Ir0nMa1deN on 2010-12-27
just out of curiosity, what happens when you run cheese? is there just a black screen, or are there any error messages about it not detecting a webcam? I thought maybe once you open cheese, you could press the button that turns on the webcam to turn it on manually (even though cheese is supposed to turn it on automatically)

---

### Post by Hamatt on 2010-12-27
I downloaded another program called Camorama. While I was running that, I pressed the button several times and Boom. there it was. Cheese and skype both work with it now. Thanks! Sorry for bothering you guys on that one. I'm not as worried with the battery issue, so I can call this one solved. Thanks everyone!

---

