---
title: "Upgrade broke file associations"
date: 2010-11-15
forum: General Help
---

### Post by Lara_Baker on 2010-11-15
A few weeks ago, my Ubuntu machine told me that the distribution I had was no longer supported so updates would no longer be available.  I updated the distribution twice, and am now on (I believe) release 10.1.4.  This is a much faster system, and I like it a fair amount.  However,...

A surprising number of things now don't work.  For example, the "Help" icon on the taskbar gives me the usual message "Starting Ubuntu Help," the cursor turns to busy, and then the notice of starting disappears, and nothing further happens.  The same thing happens when I try to open the "About Ubuntu" item in the "System" menu -- it can't find it.

Also, when I run Thunderbird as my e-mail reader, when I double-click on a .pps file, it tells me that no application is selected to run that file.  When I look at Thunderbird's configuration file, it tells me that OpenOffice Presentation is associated with that type of file.  When I double-click on a *.pps file somewhere else, I get the same "no application" message.  When I open Presentation and tell it to open the .pps file, it works perfectly.

Obviously, an association table or a configuration file is bad somewhere. Any suggestions on where to look would be much appreciated.

Thanks,  Lara

---

### Post by Enigmapond on 2010-11-15
Hi Lara and welcome to the forum. Not knowing which distro you had prior I'm unable to advise however...if it were me and it was not too long ago, I would just do a fresh install of Lucid off of a live CD and I think your problems will vanish.

Cheers!

---

### Post by Lara_Baker on 2010-11-15
Thank you kindly.  Now, I'll just look up how to make a live CD and will do the fresh installation next weekend when I have a couple of hours.  I assume that the live-CD install will recognize all the partitioning, etc., that exists now?

Thanks again.

Lara

---

### Post by Enigmapond on 2010-11-15
Yes, if you are meaning that you also have Windoze on one side...yes. It will give you the option to over-write or keep any partitions...here's the site with the OS and how-to's on installation. Good Luck..:)

[http://www.ubuntulinux.org/desktop/get-ubuntu/download](http://www.ubuntulinux.org/desktop/get-ubuntu/download)

---

### Post by Lara_Baker on 2010-11-27
I've created Live CD's both on a CD-ROM and on a USB -- they both give me the same actions.  When I boot from one of these, I get the option to "Try Ubuntu" or "Install Ubuntu."  I can't figure out how to _upgrade_ my 10.04 to the 10.10 on the "CD's" without installing from scratch (sorry about the pun) from the CD or USB.

Any suggestions would be much appreciated.

Thanks,

Lara

---

### Post by SeijiSensei on 2010-11-27
Thunderbird (and Firefox) maintain their own set of file associations that aren't necessarily consistent with the operating system.  If you right-click on a .pps file, do you get an "Open with" option?  If so, pick OpenOffice Presentation; you should be able to tell the OS to save that as the default association for future use.

Enigmapond suggests essentially blowing away your current installation and starting afresh with Lucid.  That's often a better solution that upgrading, especially if there are a few major versions in between.  However if you're not careful about backing everything up, you'll be in trouble.  So, at a minimum, make sure you've made a complete copy of /home to another device before reinstalling.

When you do re-install, consider creating a separate partition on the hard drive for /home so it will persist across any future re-installations.  You'll have to negotiate through the "manual" disk installer.  If that seems too difficult, then just let Ubuntu do its standard installation.  Either way, when you're done, copy the contents of the saved home directories.  I'd suggest not copying any of the "hidden" files that begin with a dot; just copy things like documents and the like.  The dotfiles contain configuration information that may be incompatible with the new version of Ubuntu that you're using.

---

