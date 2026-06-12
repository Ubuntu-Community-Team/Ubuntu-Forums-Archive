---
title: "Z22 Palm locks after karmic install"
date: 2009-11-01
forum: General Help
---

### Post by plain_jim on 2009-11-01
My z22 worked fine with jpilot in Jaunty.  After installing Karmic, I'm having the following problem with both my Acer netbook and my self-built desktop: Most of the time (say, 8-9 out of 10), within a few seconds after connecting my z22 to the computer via usb cable, either the z22 locks up on whatever screen, or it locks up and shows a houndstooth/checkerboard-like pattern.  I can get the z22 working again after a soft reset.  Occasionally, I am able to sync, but I cannot predict when (I had thought if I kept pressing the buttons and changing screens, that that was effective in keeping the z22 responsive, but it has not proven to be the case).  I have set my /etc/modules to start the module "visor" (without quotes), but the problem occurs even without sync-ing, or even without jpilot  being started.

---

### Post by Freelance Physicist on 2009-11-03
I was just having the exact same problem after upgrading to Karmic (freezing, houndstooth pattern).  I followed the directions from your post [here](http://ubuntuforums.org/showpost.php?p=6154925&postcount=3) and everything worked.

Essentially, 

Double check to make sure /etc/modules has a visor entry (usually this gets erased by upgrades, but not this time).
goto System -> Preferences -> PalmOS Devices
Under Devices tab, make sure your device has settings:
Type: USB
Timeout: 2
Device: /dev/ttyUSB1
Speed: 115200

Add the Pilot Applet to a panel (right click on panel, "Add to panel...", select Pilot Applet).

Syncing actually works better now than on any previous version of ubuntu (originally I had Device set as /dev/pilot and Speed at 57600).  I don't use jpilot, so I ignored those instructions.

Hope this helps.

---

### Post by plain_jim on 2009-11-03
I'm glad it's working for you.  The Z22 does fine if I plug it into the UDS cable... until I start the visor module.  Once the visor module is going (either from booting with it in /etc/modules, or from running 'sudo modprobe visor' in a terminal), I get the lockups and houndstooth again.

I'm sync-ing to an old Windows box; I'll continue that until either I can find a fix, or the Palm dies (after all, they're techno-dinosaurs now, right?), or the Windows box does.

---

### Post by oliv54 on 2009-11-04
I've got a solution for you (and me, because I had exactly the same problem) !
Just type in a terminal: "sudo apt-get install wicd" and reboot.

The problem seems tu come from network-manager (see [this page]("https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/421673")). So if you replace it by WCID (for example), everything works again.  That's not a real solution to the bug, but it's enough for the moment.

You don't need Jaunty any longer ! ;)

---

### Post by plain_jim on 2009-11-04
> **oliv54 said:**
> I've got a solution for you (and me, because I had exactly the same problem) !
Just type in a terminal: "sudo apt-get install wicd" and reboot.

The problem seems tu come from network-manager (see [this page]("https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/421673")). So if you replace it by WCID (for example), everything works again.  That's not a real solution to the bug, but it's enough for the moment.

You don't need Jaunty any longer ! ;)
Well, *THAT* worked about as well as anything ought to!  Thanks.  I'm saving these instructions in case there's a problem with any future install.

---

### Post by 824957q on 2009-11-04
ok i have linux kubuntu i think i took my self out of the administraters thingy and it says your username is unknowm to sudo! what do i do i cant install anything and i stilll do need to install the flash!!!!!!! hellllllp

---

### Post by plain_jim on 2009-11-05
> **824957q said:**
> ok i have linux kubuntu i think i took my self out of the administraters thingy and it says your username is unknowm to sudo! what do i do i cant install anything and i stilll do need to install the flash!!!!!!! hellllllp

Are you typing your user name into the terminal?  It doesn't ask for that; it only asks for your password. How do you login at startup?

---

### Post by Andy026 on 2009-12-01
> **oliv54 said:**
> I've got a solution for you (and me, because I had exactly the same problem) !
Just type in a terminal: "sudo apt-get install wicd" and reboot.

The problem seems tu come from network-manager (see [this page]("https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/421673")). So if you replace it by WCID (for example), everything works again.  That's not a real solution to the bug, but it's enough for the moment.

You don't need Jaunty any longer ! ;)


Great link!  I read everything from that link and concluded to uninstall modemmanager, which I did (via Package mgr), and my Treo 755p now works great.  It was continuously rebooting, and previous instructions of installing visor and other things were ineffective (although I still have visor in modules).  Thank you!

---

### Post by plain_jim on 2010-01-03
Or... what you can do is this: when you want to sync the Palm:[LIST=1]
[*]Right-click on the "Network-Manager" icon in the upper right of your screen, and uncheck "Enable Networking";
[*]Wait a minute or two;
[*]Sync the Palm with jpilot in the usual way;
[*]Remember to DISCONNECT the Palm device;
[*]Right-click on the "Network-Manager" icon again, and re-check "Enable Networking".
[/LIST]
It works for me - but, of course, YMMV.

---

