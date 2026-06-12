---
title: "Display Problem/No login screen"
date: 2011-02-02
forum: General Help
---

### Post by Gertlex on 2011-02-02
I installed Ubuntu 10.10 in the past hour and have had no shortage of troubles so far...

Right now it's unusable, but to describe it I'll start from the first problem.

1) The first attempt to install the OS froze.
2) After the second attempt succeeded, it looked like the OS was installed fine.

I use two identical monitors, one of these is rotated 90°.  By default they were showing the same image at the correct resolution (1920x1080).

3) I easily found Tools/Preferences/Monitor in the menus (Might not be exact nomeclature).  Unchecking mirror display, and setting one of the screens' rotation to "right" showed the correct setup in the preview.  Clicking apply logged me out, and both screens were still in the default rotation and showing the same thing.
4) Tried applying another handful of times, with the same result. WTF.
5) Tried clicking Set as Default.  This logged me out, too, and now I had the wrong (vertical) monitor as primary.  Horizontal monitor wasn't displaying anything.
6) Tried again changing the defaults.
7) Was logged out and had black screens on both monitors... no log in prompt.  Waited a few minutes.  Nothing happened, nor any response from keyboard or mouse.

....

Rebooted twice, then tried the repair mode.  No idea how to fix this via command line, so rebooted again.  Each time I get the condition in (7) above.  Computer's now fine booted back up into Win 7.

Now for system specs.
Used the 10.10-desktop-i386.iso.  Got the torrent via the official site.
AMD Phenom II 1090T (64bit capable)
8gb RAM
ATI Radeon 5770 graphics card

I will note that 5-7 happened very fast so I'm not exactly sure what symptoms I did see.  I might have not escaped the default display setup.... there's a difference in the delay with which the two monitors turn on, probably because the graphics card has a DVI and HDMI port each connected to one of my monitors.

** Is my best bet to just reinstall ubuntu a third time?  **Should I be using the 64bit version? (My general inference from what I've read in the past is that a) it should work fine with 32bit, and b) linux doesn't handle running 32bit stuff on a 64bit OS as well as Win 7.0

Edit: WTF.  Now I can't get to my boot drive selection screen, so I can't reinstall if I want to without doing more investigative work first.  I get shunted to the OS list each time instead....

---

### Post by quadproc on 2011-02-02
I think that you might make better progress if you temporarily unplug the secondary monitor.  I have noted quite a few bugs related to multiple displays being active at the same time.  I was severely burned by something similar when I installed 9.04: it seems that X windows could not figure out which of my two graphics cards (HD4870) was supposed to be the primary one, so X just quit, without even making a log entry!  Fortunately, the X authors have fixed *that* problem.

I think that you will want to use the 64 bit OS.  I have been running it exclusively since 9.04 and, these days, most of the software is capable of handling the 64 bit hardware, or the software comes in both flavors.  I do run into one thing that is still inelegant: the LaCie 4L-gui program.  That program requires a "force architecture" option during installation and that is risky territory.

The first install not succeeding is cause for concern.  Could it be that your system actually did install OK but that the display locked up with a black screen?  I have seen quite a few bug reports mention that kind of behavior.

Not sure what you mean by your last edit.  The boot drive selection screen is something provided by the BIOS, while the OS list is provided by grub-pc.  Has your BIOS gone screwy?

quadproc

---

### Post by Bucky Ball on 2011-02-02
Try 10.04 LTS, 64bit if your machine is 64bit. You will get a smoother ride.

---

### Post by Gertlex on 2011-02-02
I evidently was just having bad luck with the bios drive selector.  Tried reinstalling on that same partition, but can't get to the login screen.  It gets stuck with the flashing underscore in the upper left...

I'll try the install of 10.04 LTS 64bit next.

Regarding the first install.  I was on the Where Are You screen, with something similar to "filesystem being checked" in the progress bar.  It stayed that way and any time the cursor was over that window, the cursor was the pointing hand.  The other two installs went much faster...

I suspect that some of the software I'm going to be using is definitely 32bit.  It's obscure engineering stuff.  But I'll try the 64bit install first.  Thanks.

---

### Post by quadproc on 2011-02-02
> **Gertlex said:**
> I evidently was just having bad luck with the bios drive selector.  Tried reinstalling on that same partition, but can't get to the login screen.  It gets stuck with the flashing underscore in the upper left...
I call that the "glass teletype" mode because the video hardware is just imitating a teletype under those conditions.  On this system, that mode lasts 15 seconds then the OS has finished loading and initializing and the OS invokes a bunch of stuff including X windows.  At this time, the blinking cursor gives way to the splash screen if that is enabled otherwise the screen goes completely black except possibly for messages.  On this system, that lasts 10 seconds.  Then the splash gives way to a login screen unless you have autologin set.  It sounds like you get most of the way there.  Do you get the login drumroll?  Can you click the left mouse button and log in, even though you can't see anything?  Can you type ctrl-alt-F1 and get a glass teletype command line?  If so, you should be able to examine the Xorg.0.log file which is located in /var/logs; piping it through *tail* and *more* should allow you to examine the last of what it was doing.  You might find some meaningful messages.  Likewise with dmesg.

Getting stuck just before login could indicate that you have a graphics driver problem.  On a brand new install it should be the open source driver and I found that that driver would fail to allow the system to start up about 1 time in 8; it appears to be a race condition and its occurrence tends to be random.
> 
I'll try the install of 10.04 LTS 64bit next.
 I did find one serious problem with 10.04 and now I can't remember what it was - one of the utilities would not produce any printer output.  This was probably fixed by some update that I didn't install.  BTW, there was a mini-release of 10.04 a few months after the original release and the new one was called 10.04.1
> 
I suspect that some of the software I'm going to be using is definitely 32bit.  It's obscure engineering stuff.  But I'll try the 64bit install first.  Thanks.Since the 64 bit processors are capable of acting like a 32 bit processor, things usually work just fine even if they were compiled for a 32 bit processor.  One thing that you will almost certainly need is the ia32 libraries.

quadproc

---

### Post by Bucky Ball on 2011-02-02
> **Gertlex said:**
> 

I suspect that some of the software I'm going to be using is definitely 32bit.  It's obscure engineering stuff.  But I'll try the 64bit install first.  Thanks.

64bit release has 32bit compatibility libraries so you should have no issue running your 32bit engineering apps. ;)

---

### Post by Gertlex on 2011-02-08
Thanks for the help all, so far.  I've *almost* solved this problem.  A friend pointed me to the ATI Catalyst drivers: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English)

Installing those has allowed me to set the monitors almost how I want... except I don't see an option letting me specify which monitor is the primary one...

More pressing right now is that Ubuntu isn't playing nice with the wifi card, apparently.  That'll be a separate thread if I can't figure it out in the next few days.

---

