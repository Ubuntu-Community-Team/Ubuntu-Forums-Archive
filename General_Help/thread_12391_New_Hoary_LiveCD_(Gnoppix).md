---
title: "New Hoary LiveCD (Gnoppix)"
date: 2005-01-24
forum: General Help
---

### Post by WorLord on 2005-01-24
Hello, all.  

I've downloaded the new Ubuntu LiveCD (new Gnoppix), and when it gets to a login prompt, I do not know what to do to log in.  I've read as many FAQ's and threads on the topic as I can, but cannot seem to find this information.  User "root" with no password fails.  User "credativ" doesn't work, and I can't log into a terminal (as root or otherwise) to change it.  

How did everyone else get around this?

 :oops:

---

### Post by albersag on 2005-01-24
[QUOTE=WorLord]Hello, all.  

I've downloaded the new Ubuntu LiveCD (new Gnoppix), and when it gets to a login prompt, I do not know what to do to log in.  I've read as many FAQ's and threads on the topic as I can, but cannot seem to find this information.  User "root" with no password fails.  User "credativ" doesn't work, and I can't log into a terminal (as root or otherwise) to change it.  

How did everyone else get around this?

 :oops:[/QUOTE]
 Maybe it could be gnoppix as user blank password

try root/root

I did not use this distro, so i can not be more helpfully

---

### Post by misGnomer on 2005-01-25
You are using the latest Gnoppix beta 0.9.3b3 (20 Jan release)?

That and the previous recent releases have booted straight into Gnome desktop here, with no login prompt.

The default user/passwd combo seems to be ubuntu/ubuntu. Instead of root, Ubuntu encourages the use of "sudo", with normal user's password (e.g. "ubuntu").

I just booted into 0.9.3b3 and set up pppoe connection with "sudo pppoeconf" without root password.

Hmm, I just tried to bring up the Gnome Users dialog which didn't work; instead the top panel froze and is now stuck highlighting the "Desktop" menu. Maybe Gnome was disturbed by my root login attemps. The bottom panel and terminal froze a little later as well so it's a soft reboot time soon...

Another new quirk was with screen resolution. My Viewsonic VE155 gets offered 75Hz refresh rate by default and that causes fuzziness which clears up after setting it at 70Hz. This time the whole screen (desktop) had stretched a few millimeters over both horizontal edges at the initial 75Hz, and at 70Hz the shift was a few mm but only towards the right edge.

---

### Post by misGnomer on 2005-01-25
Back after reboot... Now that I paid attention I noticed that the screen (Gnome desktop) jumped a few mm over the edges only during initialization when the panels where drawn. For a few moments before that the brown background was perfectly centered. During the text-mode boot the screen also spilled slightly over the left edge. This is probably an Xorg setup issue. (Viewsonic VE155 TFT & ATI RADEON 9200)

Also, I usually boot with "linux acpi=off nofstab noscsi dma atapicd" but for the last boot I had left out "acpi=off" and the session became corrupted and soon froze. Something to do with my VIA KT400A/VT8235 chipset still not being properly supported by ACPI?

---

### Post by WorLord on 2005-01-25
Something must be screwy with my image (b2).  Ubuntu/ubuntu doesn't work, either.

I'm going to DL a new image.

---

### Post by WorLord on 2005-01-25
Follow Up: 

Downloaded b3.  Still took me to a log in window, but ubuntu/ubuntu actually worked this time.  

I may upgrade to Hoary at home... this looked great.

---

### Post by Tiiba on 2005-01-26
I made a Gnoppix CD today, and it doesn't even try to boot. The screen sits at the last BIOS message and does nothing.

---

### Post by Daniel G. Taylor on 2005-01-27
I've been grabbing daily livecd ISOs from here: [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

They boot and give you an installer-like screen where you can pick your language and such, then it loads some modules and boots into a working GNOME session.

Just today I got the 26 Jan 2005 PPC livecd and tested it on my iBook G4 (worked nicely, btw). [Here's a screenshot](http://home.programmer-art.org/images/20050126-ubuntu-ppc.png).

If you use these, remember to report bugs!

---

