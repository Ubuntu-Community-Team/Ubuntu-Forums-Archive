---
title: "Lubuntu 12.04 OEM install?"
date: 2012-09-03
forum: General Help
---

### Post by ojdon on 2012-09-03
Hi there, I am just wondering if it is possible to do an OEM Install of Lubuntu 12.04 since I need to prepare an old laptop for a new home.

I have followed [this guide]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview") and downloaded a Lubuntu 12.04 alternate CD. Unfortunately, this guide is fairly outdated and I can no longer see the option to "Prepare for end-user configuration". 

Is there a way doing an OEM install of Lubuntu 12.04?

---

### Post by TheFu on 2012-09-03
> **ojdon said:**
> Is there a way doing an OEM install of Lubuntu 12.04?

I have to admit, when you say "OEM install", I immediately think you want to
* load up a bunch of crapware to track the new end-user
* load unwanted applications that cannot be removed by the end-user
 * load apps with mandatory accounts that some people don't want
* put a bunch of unwanted URLs into the bookmarks, mostly back to the "vendor support" site that nobody uses
* put a cheezy OEM graphic to be displayed at boot, instead of the most useful boot messages

Could you please explain what you really mean? 
I'm truly curious, even if I can't help at all.

---

### Post by ojdon on 2012-09-03
Yeah... That's not really what "OEM Install" means although that is what happens when you buy any Windows laptop. What I'm trying to do is this: 

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview")

But the option for "Install OEM Mode" isn't there. I'm assuming this has been rep[laced by "Expert Mode" on the Alternate CD in 12.04 but then the "Prepare for end-user configuration" option isn't there.

---

### Post by Bashing-om on 2012-09-03
ojdon;

The referenced 8.04 version of ubuntu is an older supported version. Much with the installer has changed since then. It is a very simple process to do a basic install with version 12.4.

Are you attempting some thing more than basic?
How about you do the install and in the event you have any troubles, ask ?
Process:
   1. Download desired .iso (flavor and version)
    2. Burn .iso to medium (cd or usb)
     3. Set bios to boot from desired medium
       4. Insert medium and install by following simple prompts.


[INDENT]hth <==BDQ
[/INDENT]

---

### Post by ojdon on 2012-09-03
I'm after the OEM install though if it's still available, so I can install Lubuntu 12.04 but without the need to enter in any user details since this laptop is going to be sold on.

---

### Post by TheFu on 2012-09-03
> **ojdon said:**
> I'm after the OEM install though if it's still available, so I can install Lubuntu 12.04 but without the need to enter in any user details since this laptop is going to be sold on.

Google found this solution:
* Boot the desktop installation CD
* At the normal boot menu, press F4 and the OEM menu should be displayed
* Select OEM install<enter>
* Choose installation from the menu.

Let me try it quickly in a VM.  At the main install screen, I pressed F4 to set a mode. That didn't appear to do anything.  After pressing <enter>, I hit "Install".  At the first screen displayed, it said "Install (OEM mode, for manufacturers only)".  This was on a regular 12.04 install.  I don't have a 12.04 Lubuntu handy.

Trying on a 10.04 Lubuntu ... it booted into the LiveCD with an install Lubuntu 10.04 icon on the desktop.  Clicking on that entered  "Install (OEM mode, for manufacturers only)", so it seems to work.

I'm doing the OEM install now ... didn't want to wait to completion to reply.
Very interesting question, but how are you going to load the crapware?

---

### Post by ojdon on 2012-09-03
I'm not going to load crapware? :S 

OEM Install = Normal install of Ubuntu but without having to enter in any account details, etc. :)

---

### Post by TheFu on 2012-09-03
> **ojdon said:**
> I'm not going to load crapware? :S 
That was a joke.:lolflag:

> **ojdon said:**
> OEM Install = Normal install of Ubuntu but without having to enter in any account details, etc. :)

It worked here for 10.04, though I was forced to set a hostname and password.  The login was "oem" - no prompt to change the userid.  I tried to login with a different user - it was rejected, not accepted as the new "master/sudo" login.

After a reboot, I found the **Users Settings** inside preferences for Netbooks, added a new user, and removed the oem user.  Had to go into advance settings to set the network/wifi config group permissions even though I'd made this user "administrator" - which I assume adds it to the sudoers (or admin) group - whatever this distro uses for sudo access.

Anyway, it worked, even if it seemed less than optimal.  I'm the first person to say to drop to a terminal and setup stuff that way, but perhaps for a OEM install, at the first login a little hand-holding would have been nice.

---

