---
title: "Try LiveCDs w/o burning!  Just drag n drop, easy, quick, no hassle"
date: 2010-05-28
forum: General Help
---

### Post by NUboon2Age on 2010-05-28
Okay, this is just too cool of a tool to keep to myself -- I need to put it out there for posterity and hopefully it will benefit someone else.  Sorry if this comes off as a little over the top enthused, but i just think its incredibly cool.  

Its an Ubuntu-tested** program called **MultiBoot VirtualBox test iso**.  It comes with MultiBoot*, which is way cool by itself.*  

With **MultiBoot VirtualBox test iso** you can just drag and drop a distribution's iso image and without requiring any further VirtualBox set up and up comes the distribution running in VirtualBox.  

One small overcome-able hurdle is that the web site is in French. But it seems that the web site automatically starts up translate.google.com for me, and hopefully for others. Also some of the options in the main program are slightly unclear in their use of English but I didn't run into anything that seriously confused me. [Here's the main opening page]("http://liveusb.info/") in French (but once I entered the site it triggered the translate.google.com) thing for me. If it doesn't start the translation automatically for you here's the [Web site english translation, using translate.google.com]("http://translate.google.com/translate?js=y&prev=_t&hl=en&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fliveusb.info%2Fdotclear%2F&sl=auto&tl=en")

1) I think from reading the installation instructions you need to [install VirtualBox]("http://www.virtualbox.org/wiki/Downloads") first (its a little unclear to me because I had already installed VirtualBox, so it was completely seamless for me).  I didn't have to do anything special to configure VirtualBox.  I just installed it with Synaptic.

2) Follow the [installation instructions]("http://liveusb.info/dotclear/index.php?category/Installation").  For me (w/ plain Ubuntu system) I just downloaded the script file, double-clicked on it and everything else installed automatically.

3) Download an .iso or .img of whatever LiveCD distribution you're interested in... The main MultiBoot program has web links to the many supported LiveCDs to make it easy to browse through different possiblilities.

4) Enjoy. On my system the program is available on the menu from Applications->Accessories->MultiBoot VirtualBox test iso.  Start it.  Then drag the icon of the .iso LiveCD you want to run onto the the text box that says "Drag drop iso/img".  After a pause, VirtualBox starts and once it gets going it boots the LiveCD.


* **The main MultiBoot program** allows you by GUI to create bootable USB pen drives, w/ or without persistence and to actually have multiple OSs to choose to boot from on the same pen drive OR CD!!! How cool is that?  Although a bit more complex to use than USB Startup Creator or Unetbootin it supports many, MANY distributions ([list of supported distros]("http://liveusb.info/dotclear/index.php?category/OS-Supportes")), not just Ubuntu-derived distributions.  And provides access to Windoze 7/Vista as well through SysLinux. 

** web site says: "So far the script has been tested only under
Ubuntu hardy / intrepid / Jaunty / Karmic / lucid.
For Ubuntu hardy should activate + deposit hardy-backport
and under Debian / Debian-live version squeeze"

---

### Post by josephellengar on 2010-05-28
Wow, pretty cool tool.  But every time I launch it I get a message: Is your USB Key connected?  Please connect a fat32 formatted volume and mount it in /media.  Then relaunch.
My usb drive is fat32 and mounted on /media.  Did you run into this problem?

---

### Post by NUboon2Age on 2010-05-28
{to clarify, **rossholley is referring to the main MultiBoot program**, not what my post was about, the "MultiBoot VirtualBox test iso" program} 

That's interesting, because when I first used a blank pen drive MultiBoot saw it fine.  Later I used the same one after I'd erased it using MultiBoot (I experimented w/ it and then erased it), and I ran into the message you got.  I was still able to see it in GParted.  I haven't messed w/ it further to see if it wants me to reset the partition table or something.  I will at some point because somewhat like you I wanted to set up a pen drive that has multiple recovery and older computer friendly distros on it.

---

### Post by NUboon2Age on 2010-05-28
Is your pen drive mounting and is it visible on the desktop?  Mine isn't, so I figure I'll need to resolve that first probably before I can expect MultiBoot to see it.

BTW, I've run into some glitchy behavior in Lucid w/ not automounting USB pen drives that required changing the boot order and disabling floppy booting.  At the moment I know that's not the problem I'm encountering because another USB pen drive mounted correctly, but not the blank one.

---

### Post by NUboon2Age on 2010-05-28
Edit:  I have since learned that after MultiBoot reformats the disk,  unplug and replug and the pen drive mounts properly.  This appears to be due to an OS glitch, since MutliBoot relies entirely on OS calls like parted to do its formatting (and actually, all its functions -- it is basically an elaborate set of scripts with a GUI).  I don't know if knowing this would have helped rholley or not.  My response below in the quote box turns out to be entirely a red herring.

> I just got it working, by 

1) Erasing the pen drive in USB Startup Disk Creator, quitting that program.  Now I see the USB pen drive correctly mounting on the desk top.

2) Start MultiBoot and now I see the pen drive correctly and can work with it.

{sorry I'm not knowledgable enough to know why it worked in Startup Disk Creator and not when I erased it (and put an MBR on it -- maybe that was a problem) in 'Disk Utility'}.

---

### Post by josephellengar on 2010-05-28
> **NUboon2Age said:**
> I just got it working, by 

1) Erasing the pen drive in USB Startup Disk Creator, quitting that program.  Now I see the USB pen drive correctly mounting on the desk top.

2) Start MultiBoot and now I see the pen drive correctly and can work with it.

(sorry I'm not knowledgable enough to know why it worked in Startup Disk Creator and not when I erased it (and put an MBR on it -- maybe that was a problem) in 'Disk Utility'.

Oh, thanks.  That worked perfectly. :confused:

---

