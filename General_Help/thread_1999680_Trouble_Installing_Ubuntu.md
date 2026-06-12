---
title: "Trouble Installing Ubuntu"
date: 2012-06-08
forum: General Help
---

### Post by MrHappyGoLucky12 on 2012-06-08
I can't seem to install Ubuntu.  When I attempt to, this is the error I get.  Sorry for the sloppy photo.  Any ideas what is going on?

[[IMG]http://img96.imageshack.us/img96/9428/20120608122505447.th.jpg[/IMG]](http://img96.imageshack.us/i/20120608122505447.jpg/)

---

### Post by phosphide on 2012-06-08
Could you provide a little bit more information to help? 

Is this your first time installing? 
Was this a fresh install, reboot after install, etc.? 
What version of Ubuntu are you trying to install?

Anything would be appreciated. Also, since the BusyBox issue is pretty common (more or less), see if this link will help you.

[http://www.tuxtrix.com/2009/12/solving-busybox-black-screen-problem-in.html](http://www.tuxtrix.com/2009/12/solving-busybox-black-screen-problem-in.html)

---

### Post by MrHappyGoLucky12 on 2012-06-08
It's my first time installing on this computer.  I wiped my hard drive and made a partition for Windows and a partition for Ubuntu.  Windows is up and running fine.  I'm trying to install 10.04.

---

### Post by phosphide on 2012-06-08
So is this the screen you get when you try installing from the live cd/usb stick? Are you able to run Ubuntu without installing?

If you can try running Ubuntu without installing. Once you have booted in, open up a terminal (Ctrl+Alt+T) or by going to Applications -> Accessories -> Terminal. Upon opening up a terminal, type **sudo fdisk -l** and post the output here.

---

### Post by MrHappyGoLucky12 on 2012-06-08
Yep, when I stick the live CD in, no matter whether I run it without installing or try to install it, I get that same error.

---

### Post by pqwoerituytrueiwoq on 2012-06-08
test the cd to make sure it burned correctly
i burn on slowest speeds to help prevent a bad burn and wasting the cd (i use a live usb when possible)

---

### Post by MrHappyGoLucky12 on 2012-06-08
How do I test it other than making another one?

---

### Post by phosphide on 2012-06-08
I don't know what he means by test either, though I would try to burn it again. However, before you waste another cd, can you post the hardware you have? Did you download 64-bit or 32-bit?

Also, how far do you get into the live cd screen?

---

### Post by MrHappyGoLucky12 on 2012-06-08
I can't get past the screen where you select RUN or INSTALL.  I am using the 64-bit version.  Here's the specs from the manufacturer.

[LIST]
[*]2nd Gen Intel® Core™ i5-2450M processor with a 3MB cache and 2.5GHz processor speed with Turbo Boost up to 3.1GHz.
[*]8GB DDR3 memory
[*]Blu-ray Disc-enabled DVD±RW/CD-RW drive
[*]13.3" LED-backlit display with 1366 x 768 resolution 
[*]Intel® Wireless Display
[*]750GB + 4GB SLC Serial ATA hybrid hard drive (7200 rpm)
[*]AMD Radeon HD 6470M graphics with 512MB dedicated video memory. HDMI output for connection to an HDTV.
[*]Built-in webcam and microphone
[*]1 USB 3.0 port and 2 USB 2.0 ports
[*]Memory Stick Duo and Secure Digital card slots.
[*]Built-in Intel® Centrino® Wireless-N adapter
[*]Stereo Bluetooth A2DP (2.1 + EDR) interface
[*]Built-in 10Base-T/100Base-TX/1000Base-T Ethernet LAN
[/LIST]

---

### Post by phosphide on 2012-06-08
Ok, I was just wanting to get idea of what you are working with. Let's try this:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you can get into the advanced page try to check your disk for defects. After that, see if you can change any of the other remaining settings to see if something is enabled that maybe shouldn't be.

That's the best I can do.

Also, just curious, why 10.04? Have you tried 12.04 yet? You can then just resort to the gnome-fallback and it will be pretty much the same as 10.04.

---

### Post by MrHappyGoLucky12 on 2012-06-08
I'll give it a try and report back.  Thanks! I'm using 10.04 because I've never used Ubuntu before and have the book, "Ubuntu for Non-Geeks: A Pain-Free, Get-Things-Done Guide" that goes with 10.04.

---

### Post by phosphide on 2012-06-08
Well, nothing wrong with 10.04 and it was a great release. Though, they are dropping support for it I believe next year. 12.04 is a 5-year LTS (Long term support) so you are probably much better off downloading that. The book you have is probably going to be a little outdated as well. A lot has changed since then.

---

### Post by MrHappyGoLucky12 on 2012-06-09
I made a new CD and still get the same error message.  Maybe I'll try the latest version.

---

### Post by oldfred on 2012-06-09
I am still using my Ubuntu 6.06 book. 

From that version a lot has changed. But over the years I have added a lot of notes, pasted pages in. And now have a lot of pages on my computer, but still use book for many things. Many of the basics have not changed, graphics and more gui ways of doing things have changed a lot.

---

