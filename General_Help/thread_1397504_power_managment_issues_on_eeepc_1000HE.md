---
title: "power managment issues on eeepc 1000HE"
date: 2010-02-03
forum: General Help
---

### Post by jeff.sadowski on 2010-02-03
$ uname -a
Linux jeff-laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux
$ gnome-power-manager --version
Version 2.28.1

I have an eeepc 1000HE

I had finally got everything working after upgrading the kernel using:
sudo aptitude upgrade

Then after trying a different setting in the power management I noticed a problem.

When I select on the "On AC Power" tab for "When Lid is Closed" set to "Blank screen" (I'd like the option to do nothing) it no longer works properly. The "On Battery Power" tab for "When Lid is Closed" is still set to "Suspend" but when I unplug the power and shut the lid it does not suspend. It did before I made the change.

I started checking if acpi was working properly.
using 
sleep 5;cat /proc/acpi/button/lid/LID/state
then shutting the lid it appears everything is correct so If I could use my own scripts I could fix things.

I do see errors in dmesg

> 
[   83.724106] ACPI: EC: missing confirmations, switch off interrupt mode.
[   84.244089] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] 20090521 evregion-424
[   84.244139] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_.EBTS] (Node f70130f0), AE_TIME
[   84.244257] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_.UBCS] (Node f7016f90), AE_TIME
[   84.244356] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.CBST] (Node f7017120), AE_TIME
[   84.244451] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.BAT0._BST] (Node f7017060), AE_TIME
[   84.244559] ACPI Exception: AE_TIME, Evaluating _BST 20090521 battery-385


I'd like to know where to report those errors. If there are flags I can put in grub to fix the errors or maybe some other ACPI method of fixing the error?

It should still work with the errors. Those same errors existed when suspend was in the On AC power's lid closed option. And it suspended on lid closed with the power plugged in or not.

Is there a better power management application for gnome? Preferably one that gives an option to do nothing on lid close? I like the battery status option in the system tray like gnome-power-manager offers I want that still.


---------------------------------------------------------------------------------------

update

I still get those error messages in dmesg. However I have it working correctly even with those messages. I did it by using gconf-editor apps->gnome-power-manager->buttons on lid-ac I used the option nothing (funny after selecting that I have that option the other way now too.) Since that change my laptop works correctly as I wanted it configured. I can now plug in an external display and shut the lid and still work. And it will suspend if I pull the power like I wanted it.

---

