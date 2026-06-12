---
title: "X won't start after &quot;playing&quot; with drivers (Lucid)"
date: 2010-06-24
forum: General Help
---

### Post by Pajdorix on 2010-06-24
I'll try to give as much info as possible.
So, Xubuntu 10.04, ATI Radeon X600...

What I did is opened Synaptic Package Manager, selected xserver-xorg-video-ati and xserver-xorg-video-radeon for REMOVAL, and selected fglrx driver for INSTALLATION. Then clicked Apply. Then tryed to launch Urban Terror. Didn't work at all. Then I changed desktop resolution to check something and then returned it to what it was. Then I opened Synaptic Package Manager again (to undo what I did), selected fglrx drivers for removal, and xserver-xorg-video drivers for installation. After that I continued using computer until I wanted to restart.

Booting now gets me to graphical login page, which by my logic means video card is working. When I enter password it starts loging in but then the screen just goes blank, with monitor LED blinking as if there was no signal.

/etc/X11/xorg.conf does not exist
/var/log/Xorg.0.log does not have any (EE) lines

Maybe I should check/change the desktop resolution, but I don't know how to do it for a terminal :S

anyone knows what's going on?

[Xorg.0.log]("http://rapidshare.com/files/402408538/Xorg.0.log.html") just in case

edit:
if I enter 
sudo dpkg-reconfigure xserver-xorg
in the terminal, it asks for root password and then nothing happens (it goes to a new line blah@blah-xubuntu$ )

---

