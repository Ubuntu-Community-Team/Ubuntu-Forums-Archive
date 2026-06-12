---
title: "Upgrade to newer Ubuntu version"
date: 2012-01-15
forum: General Help
---

### Post by Welly Wu on 2012-01-15
Hello. I own an ASUS N61JV-X2 notebook PC with Crucial 8 gigabytes of DDR3 1,066 MHz SODIMM SDRAM and an Intel 2nd Generation X25-M 160 gigabyte MLC NAND FLASH Solid State Drive. I installed Ubuntu 10.04.3 64 bit Long Term Support as my primary operating system and I also configured it to enable full disk encryption using Advanced Encryption Standard CBC Mode 256 bit key strength and SHA-512 hash algorithm.

Canonical releases a new version of Ubuntu 32 and 64 bit Long Term Support every two years in April. The next version will be Ubuntu 12.04 64 bit LTS on April 26th, 2012.

I plan to download and save the Alternative Installation 64 bit .ISO file on my Seagate FreeAgent Desk external hard disk drive and I plan to burn the .ISO file to a blank CD-R or DVD-R disc depending upon the size of the final release to the general public version.

How do I upgrade Ubuntu 10.04.3 64 bit LTS to Ubuntu 12.04 64 bit LTS without having to re-install the entire operating system? Is there a command that I can type into a BASH shell to perform this upgrade?

Is it recommended to perform an upgrade in the manner in which I seek my answer to my question?

Is it better to get a copy of Ubuntu 12.04 64 bit LTS onto a CD-R or DVD-R disc and insert it into my ASUS N61JV-X2 notebook PC and perform the upgrade within GNOME? If this is possible, then I plan to download the .ISO file containing the default installation method for Ubuntu 12.04 64 bit LTS and burn it to a blank CD-R or DVD-R disc. Afterward, I will stick the disc into my DVD burner drive and perform the upgrade. I have Ubuntu 11.10 64 bit burned onto a CD-R disc and when I insert it into the DVD burner drive, it asks me whether I want to perform an upgrade. I chose not to do so because I want to stick with LTS releases exclusively.

Thanks for your help.

---

### Post by bluexrider on 2012-01-15
Ubuntu has a pathway to upgrade from one LTS to another built in the software manager.

That being said. It is always best to do a fresh install. 

Recommend segregation of "/home" to a separate partition then do a new install.

---

### Post by Welly Wu on 2012-01-15
So, all I have to do is to wait for Canonical to release the next LTS version and I will be notified if I want to upgrade? Is that how it works?

---

### Post by pqwoerituytrueiwoq on 2012-01-15
you can wait for 12.04 final or you can add the beta/alpha ppa and update you will be notified by the update manager

---

### Post by Welly Wu on 2012-01-15
Okay, thank you for the answer to my question.

I plan to download the .ISO files for the normal and alternative installation for Ubuntu 12.04 64 bit LTS and I will burn the .ISO files to blank CD-R or DVD-R discs. I will also copy the .ISO files to my Seagate FreeAgent Desk external hard disk drive as a backup.

---

### Post by snowpine on 2012-01-15
"How to upgrade Ubuntu" is very well-documented over at ubuntu.com: 

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

This page will be updated in April when 12.04 is released; if you are interested in helping test 12.04 pre-release then visit the [testing sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=412")! :)

---

### Post by Zill on 2012-01-15
> **Welly Wu said:**
> So, all I have to do is to wait for Canonical to release the next LTS version and I will be notified if I want to upgrade? Is that how it works?
Basically yes - if you have a default installation of 10.04.  However, this does depend how the Update Manager is configured.  To check, open the Update Manager (menu System, Administration) then click on the "Settings" button.

This will display the "Software Sources" info and if you click on the "Updates" tab this has a section entitled "Release Upgrade".  Click on the small arrow to see the options available.  If you have "Long Term Support (LTS) releases only" selected then you will be automatically notified when 12.04 is released.

---

### Post by grahammechanical on 2012-01-15
As you have already found out with 11.10 by saying this:

> I have Ubuntu 11.10 64 bit burned onto a CD-R disc and when I insert it into the DVD burner drive, it asks me whether I want to perform an upgrade.

Well, the 12:04 live CD that you create will offer the same option. It is best to be connected to the internet so that the install process can do any necessary updates at the same time.

We do not need to do a fresh install to upgrade from one release to the next but it may be advisable to do a fresh install when going from 10.04 to 12.04.

I do not have any scientific evidence but I am of the opinion that the difference between 10.04 and 12.04 is so great that a fresh install is preferable. This is (in my opinion) especially necessary if the desktop has been heavily modified with themes and docks and that sort of stuff.

Based on posts on this forum where people had difficulties going from 11.04 to 11.10 I wonder if the problem was due to upgrading a modified desktop. If you do decide to upgrade and not fresh install, then revert the desktop to its basic level. That is my advice.

Regards.

---

### Post by snowpine on 2012-01-15
If it is a "mission critical" environment then testing the upgrade is advisable, on a virtual machine or, better yet, a spare machine with identical hardware.

However it is so easy to clone your drive and backup your data that even a casual home user can have 100% confidence with the upgrade by taking a few basic precautions.

The biggest #1 precaution in my experience is to run a Live CD of the target 12.04 release and make sure you actually WANT to upgrade to the new release. :)

---

