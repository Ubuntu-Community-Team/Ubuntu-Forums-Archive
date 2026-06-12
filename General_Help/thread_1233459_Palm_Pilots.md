---
title: "Palm Pilots"
date: 2009-08-06
forum: General Help
---

### Post by Eggnog7 on 2009-08-06
I have a Palm Pilot Zire 21, and cannot get it to sync no matter what i install or try.  Can someone please tell me how to get it to sync?  I have tried numerous programs and it just won't cooperate.  Thank you all very much for the time to read and respond to this.  OH, by the way, I am running Jaunty Jackalope...if you need to know.

---

### Post by quixote on 2009-08-07
This isn't a solution, just a commiseration.  I had the same problem with a Palm Pilot V on Gutsy & Hardy.  I finally gave up, but it ought to be do-able on Jaunty, for pete's sake!

---

### Post by tjb_ithaca on 2009-10-28
Ubuntu Jaunty 9.04 (full version) on eeePC 900 (2GB RAM); Palm Zire 72; USB 2.0 cable sync to Evolution

I've spent hours searching through Google and Ubuntu forums to get Evolution to cable sync with my Palm Zire 72. I was about to give up, but wanted to delete the invisible Pilot Applet from my launchpad bar. I found a solution to both the invisible Pilot Applet and the inability to sync from the Zire 72 to Evolution. Bug #349650 in gnome-pilot (Ubuntu): "gpilotd running but no panel icon" at [https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/349650 ]("https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/349650")

Far down on this page,

[William McKee]("https://launchpad.net/%7Ewilliam-knowmad") wrote on 2009-07-05: [ #30]("https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/349650/comments/30")

The new package (gnome-pilot_2.0.17-0ubuntu2) has not made it into Jaunty yet. However, I did find it in Karmic[1] and was able to successfully download and install the 64-bit version for my Jaunty laptop. YMMV.

 William

 [1] [http://packages.ubuntu.com/karmic/gnome-pilot](http://packages.ubuntu.com/karmic/gnome-pilot)

This also works in 32-bit as noted elsewhere on the page.

I first reversed all the changes I made while trying other solutions that didn't work. Various configuration file changes and removing a gnome-link installation. You may have done other things. Perhaps the reversal wasn't necessary, but I didn't want to chance those changes breaking the new gnome-pilot install.

Next, using System > Administration > Synaptic Package Manager, I removed gnome-pilot 2.0.17-0ubuntu1 -- Note the "1" at the end.

Restarted Ubuntu to ensure all errant processes were closed.
 
Downloaded the new gnome-pilot 2.0.17-0ubuntu2 package, double-clicking on the downloaded package launched the package manager and installed the new gnome-pilot.

Right clicking on the launchpad bar enabled me to add the Pilot Applet,which thankfully, after adding, was no longer invisible in the launchpad bar.

I launched Evolution, went to Edit > Synchronization Options, and configured the options. I worked with the wizard on my initial tries. Because I previously synced the Zire 72 to my Mac, my answer to the wizard was "Yes", I previously synced to a PC. Because of my previous attempts, the wizard didn't come to my aid this time. A dialog box presented me with three tabs.

- PDA tab: Click the "Get from PDA" button and follow the instructions. PDA Owner and ID should appear.

- Devices tab:
  - Name: Cable, you may choose what you like.
  - Type: USB
  - Timeout: 2 worked for me
  - Device: usb: Looks odd, but worked
  - Speed: 57600 This is the default. I may try a higher speed later.
- Conduits: Backup: Selection advised. Other conduits with the first letter "E" such as "EAddress" are Evolution conduits. So far I've only synced addresses to see how the fields in Evolution Contacts filled in. A few fields on the Zire didn't have comparable fields in Evolution and so weren't imported. "Division" on the Zire didn't make it, but the major fields were intact.

Hope this will save someone else the time and frustration I experienced.

---

### Post by NUboon2Age on 2010-06-22
Lucid, Palm 700p, USB cable/cradle

1) **Purged** (aka Synaptic "completely remove") **modemmanager** package (because otherwise I was getting continous Palm resets (see Bug #421673).
2) **Removed visor from /etc/module file** (not there by default, I'd added when experimenting earlier) 
Note the visor module conflicts with libusb  which appears to have been available from Jaunty onward.

My settings in gnome-pilot:

- Devices tab:
  - Name: Cable, you may choose what you like.
  - **Type: USB**
  - Timeout: 2 
  - **Device: usb: **
  - Speed: 115200 (not default -- don't know if this is vital, but it worked for me)

---

