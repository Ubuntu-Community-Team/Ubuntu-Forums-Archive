---
title: "Finally, I got a SanDisk Cruzer 16gb thumb-drive/U3 to boot!"
date: 2009-09-23
forum: General Help
---

### Post by dummy910 on 2009-09-23
I followed just about every how-to on the net, yet the only one that would boot via the instructions was the [**PendriveLinux** ]("http://www.pendrivelinux.com/")flavor, all well and good, but I really wanted either 9.04 or the 9.10 flavored **[Ubuntu-Gnome]("http://ubuntu.com")** to boot as an install medium for clients machines, as well as a troubleshooting tool.

To make a very long story short, I laid finally ended up formatting a "fat16" partition on the "1st" 4gb of this 16gb drive(the rest whatever layout ya need to use), then ran [COLOR=Red]**[Unetbootin]("http://unetbootin.sourceforge.net/")**[/COLOR] to install the given( in this case, 9.10alpha .iso)and bam!, Houston, we now have a drive that boots!

Finally, and _just about every how-to I ran across on the net states to format the partition as fat32_. Well not in this case mission control, [COLOR=Red]_it's fat16_[/COLOR]

**Note:**
For anyone running across a drive with [COLOR=Red]_the miserable "U3"_[/COLOR] , it lies on as an "isofs" boot partition, and MUST be removed. Just go to the sansdisk site and download the windoze-only tool named the [COLOR=Red]**[U3 Launchpad Removal Tool]("http://u3.sandisk.com/launchpadremoval.htm")**[/COLOR] that will allow you to wipe all the partitioning off that thumb-drive your trying to get to boot. The thumb-drive WiLL NOT boot until this tool-wiper is run, period.

---

### Post by zami on 2009-11-03
> **dummy910 said:**
> I followed just about every how-to on the net, yet the only one that would boot via the instructions was the [**PendriveLinux** ]("http://www.pendrivelinux.com/")flavor, all well and good, but I really wanted either 9.04 or the 9.10 flavored **[Ubuntu-Gnome]("http://ubuntu.com")** to boot as an install medium for clients machines, as well as a troubleshooting tool.

To make a very long story short, I laid finally ended up formatting a "fat16" partition on the "1st" 4gb of this 16gb drive(the rest whatever layout ya need to use), then ran [COLOR=Red]**[Unetbootin]("http://unetbootin.sourceforge.net/")**[/COLOR] to install the given( in this case, 9.10alpha .iso)and bam!, Houston, we now have a drive that boots!

Finally, and _just about every how-to I ran across on the net states to format the partition as fat32_. Well not in this case mission control, [COLOR=Red]_it's fat16_[/COLOR]

**Note:**
For anyone running across a drive with [COLOR=Red]_the miserable "U3"_[/COLOR] , it lies on as an "isofs" boot partition, and MUST be removed. Just go to the sansdisk site and download the windoze-only tool named the [COLOR=Red]**[U3 Launchpad Removal Tool]("http://u3.sandisk.com/launchpadremoval.htm")**[/COLOR] that will allow you to wipe all the partitioning off that thumb-drive your trying to get to boot. The thumb-drive WiLL NOT boot until this tool-wiper is run, period.

E3 is miserable indeed.

So I'm trying to use the removal tool, but it just can't find the USBstick. I can't get the program past the message "please insert a U3 smart drive".  Did you (or anyone?) have this issue?

I checked wincfg and Wine sees the drive, just not the removal tool.

Any advice?

-zami

edit:
If I can just throw in a gripe here...  

I had a nice E3-free Lexar stick, but my kids broke it playing "ship" (think StarWars - apparently a USB stick is a very convincing Corellian Corvette), so I went and got a new stick, only to find it equally unusable due to this E3 crap!  And in my feeble attempts to remove it, I think I may have locked it up and *really* made it useless.  Might try my husband's Windows machine and see if it's happier in there, and better yet if I can use the removal tool from a proper Windows install (as opposed to a Wine install).

-zami

edit; part deux:
yes, another edit...
The drive loved Windows, and I had no problem using the removal tool from there.
Booooo on E3 for making me go find a Windows machine.  I really hate bullyware.

-zami

---

