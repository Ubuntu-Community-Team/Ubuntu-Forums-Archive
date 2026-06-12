---
title: "HP B210 + wireless"
date: 2012-01-16
forum: General Help
---

### Post by Bartender on 2012-01-16
Good day!

I wanted to get this out there before I forgot the steps.

Bought an HP B210 Photosmart Plus recently.  Assumed it would work wireless with Ubuntu because 2 years ago I connected to my Dad's wireless HP printer in about 5 minutes with only a little bit of guessing.

Didn't work that way this time.  I installed HPLIP (running 10.04) and tried about 18 different ways to get it working wireless.  The printer was configured correctly to our Linksys WRT54G router.  At least it said so.

When all else fails read the google.  I frankly did not understand the directions in post #2 of this [thread]("http://ubuntuforums.org/showthread.php?t=1656188"), but it got me started.  I downloaded the latest version of HPLIP from sourceforge and copied to Desktop.

Then I found this [thread]("http://ubuntuforums.org/showthread.php?t=1316616").  Post 3 looked pretty simple, although I don't know what "sh" means.  I'll try just about anything if it's simpler than the first thing.  

The version I had d/l'ed was called "hplip-3.11.12.run".  Latest version as of this date.  As mentioned above, I already had copied the d/l to the desktop.  So I opened a terminal and typed

```
cd Desktop
```

then

```
sh hplip-3.11.12.run
```

then I clicked Enter.  Woah!  AFAIK I've never executed a .run file but it was pretty cool.  It found needed dependencies, checked for an internet connection, then got the dependencies.  Then it tried to uninstall the version of HPLIP that I already had, but failed, so it said the new install would probably overwrite it.  

**So if you try this, uninstall HPLIP first if you've installed it from the repos.**  

Then, when it was almost done, it said to restart the printer.  Unless I was trying to use wireless, then it said to type in "i" for ignore.  I did this.  A few minutes later it *started* HPLIP, and I went thru the same steps for identifying a wireless printer as before, which entail connecting it via USB to configure.  It saw the printer (yeah!, one step beyond where I got before) then said there was an I/O error.

I gave up.  Got out of HPLIP and closed the terminal, where hplip.run appeared to have finished.

Then I went into printers.  There were two B210's.  One was apparently the USB install.  It said "disconnected".  I tried the other.  The wireless connection worked!

So, if you bought a Photosmart Plus B210 and gave up, or are thinking of getting one, you need a new version of HPLIP.  Maybe it works automagically with the latest versions of Ubuntu, but it does not with 10.04.  It's a little challenging to get the latest HPLIP, but not too bad.  And even if it looks like the setup failed, soldier on and with any luck at all it'll work anyway.

---

### Post by Bartender on 2012-12-17
Wanted to update this in case anyone else has run into similar situations.

So here I was, a year later, with the same HP B210+ printer, but a different PC running Ubuntu 12.04.  Also a modern Netgear WNDR3800 replacing the ancient Linksys WRT54G.  

I searched & found my old post (above), then followed the directions.  The latest stable version was 3.11.12 a year ago, now it's 3.12.11.  Don't let that confuse you! 

I downloaded the package, moved it to the Desktop, then ran the two commands as shown in first post.  Had to click "y" once or twice and enter password, then it did its thing for ten minutes or so.

About midway, it said that HPLIP 3.12.11 was already installed.  ??  I asked it to "overwrite" because I was already this far into it.  I didn't have the blue "hp" icon on the upper panel, but I hadn't gone looking for hplip either.  

Finally it said: 

[COLOR="Navy"]RESTART OR RE-PLUG IS REQUIRED
------------------------------
If you are installing a USB connected printer, and the printer was plugged in when you started this installer, you will  
need to either restart your PC or unplug and re-plug in your printer (USB cable only). If you choose to restart, run this
command after restarting: hp-setup (Note: If you are using a parallel connection, you will have to restart your PC. If   
you are using network/wireless, you can ignore and continue).                                                            

Restart or re-plug in your printer (r=restart, p=re-plug in*, i=ignore/continue, q=quit) :[/COLOR]

Since I wanted wireless I entered "i".

Then I got directions to plug the printer in via USB in order to make it work wireless.

The last entries in the hplip terminal said:

[COLOR="Navy"]error: Unable to lock /home/hammer/.hplip/hp-systray.lock. Is hp-systray already running?[/COLOR]


And that's where things went sideways.  The Ubuntu Printer utility popped up, and it found the printer but couldn't connect to it.  Said it was "off", which it wasn't.  I looked unsuccessfully for a place to enter the wi-fi encryption.  The HPLIP icon had installed itself to the upper panel, but I'd get a "somethingsomething.py" error when I tried to go into Device Mgr.

By this time I'd unplugged the USB cable because I'd been told to.  At a loss, I turned off the PC and restarted it.  After a restart, the HPLIP Device Mgr. seemed to work OK.

So I tried to send the printer a test page.  Nothing.  I scrolled thru the Device Mgr. tabs.  The first radio button in the last Device Mgr. tab (attached) indicated the printer was "off".  So I clicked on that radio button and the Test Page started to print.

So, it appears to be working, even though the process was not confidence inspiring.  Probably some of the "two steps forward, one step back" was self-inflicted...

---

