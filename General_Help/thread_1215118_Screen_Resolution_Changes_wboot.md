---
title: "Screen Resolution Changes w/boot"
date: 2009-07-16
forum: General Help
---

### Post by Robt6 on 2009-07-16
Discription of Hardware - and previous fixes
I've installed Ubuntu 8.10 on an old Emachines T1120, all stock except for a memory card to max out memory at 512mb.This is an install into a partition on the hdd, using grub to dual boot Xp or Ubuntu. Compiz has been removed (as per previous post) to get past blank orange screen.
Monitor: Compaq 5017. KVM switch to share monitor with Compaq Presario

On to the problem - Boot Ubuntu,  and screen resolution may be:
800x600  or 1280x768. It changes just about every time Ubuntu is booted.
When it starts 800x600, The only choices in Preferences > Screen Res- is 800x600 and 640x480. If It starts 1280x768, I have all resolutions the monitor supports available. Also, quite often, when it starts with 1280x768, the desktop is shifted approx 2 inches to the left or right. Black vertical bar either to the left or right, and unable to see the entire desktop. Can we make it start at 1280x768 and still have all others available?

---

### Post by CatKiller on 2009-07-16
> **Robt6 said:**
> KVM switch to share monitor with Compaq Presario

I think that this is your culprit.

Your monitor reports its capabilities through EDID, which X uses to calculate the resolutions that your monitor is capable of. If you start the computer with the KVM switched to the display of the other machine, X doesn't get the EDID information it needs and so defaults to really low refresh rates that won't damage any monitors.

You could either make sure that the switch is always set appropriately when you start the machine, or you could specify the HorizSync and VertRefresh values in xorg.conf that X would normally get through EDID and tell X to ignore the (lack of) EDID values.

---

### Post by Robt6 on 2009-07-16
I have been rebooting w/ KVM on the Emachine and ecperiencing the resolution issue. But IT could be the source of the problem. so
I will try with NO KVM switch - monitor direct to computer. But, probably, not till tomorrow. will report results here then, 
Thanks.

---

### Post by CatKiller on 2009-07-17
Actually, I was surprised that you got the correct resolution at all through a KVM switch. Most of them seem to eat EDID information.

---

### Post by Robt6 on 2009-07-17
It is the KVM sw. Have booted from totally off, restarted, and res is always 1280x768. Now the question is How do I specify the HorizSync and VertRefresh values in xorg.conf? And can we make it start at 1280x768 and still have all others available? << not that important ))
gotta run again, so it may be a while before next reply. Thanks

---

### Post by CatKiller on 2009-07-17
> **Robt6 said:**
> Now the question is How do I specify the HorizSync and VertRefresh values in xorg.conf?

Now that you've got the values picked up by X without the KVM, you can get them from /var/log/Xorg.0.log if they aren't in you monitor's documentation. If they don't show up in the log, you can set ```
        Option          "ModeDebug"                     "True"
``` in the Device section of xorg.conf to get verbose output in the log.

Once you've got the correct ranges, they go in the Monitor Section, like so:
```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for your monitor.

In case the lack of EDID values still causes a problem, you can put

```
        Option          "UseEDID"                       "False"
``` in the Device section, but only do this if it doesn't work without.

>  And can we make it start at 1280x768 and still have all others available? << not that important ))

All the modes that fit in those refresh rate ranges will work. The highest available is picked by default.

---

### Post by Robt6 on 2009-07-17
Ok, If I were to edit xorg.conf, so that it plays well with the KVM switch, can I expect problems if I upgrade the monitor? Also, what is the terminal command to edit xorg.conf? Tried etc/X11/xorg.conf, but just showed a blank doc.
This is a NEW experience/procedure on this end as I'm really New with this (linux), like First timer.
EDIT--whoops--- HELPS TO TYPE conf. instead of comf.

would it, to be added to  look likt this?: 
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync   30.00-61.00 kHz
        VertRefresh   56.00-75.00 Hz
EndSection

I'm just a little aprehensive, cause I think/believe if I screw up, the screen is gonna go blank and then it'll be lights out so to say.

---

### Post by jebedia82 on 2009-07-18
Hello all
I had the same problem with my computer as yours Robt6.
After every boot, the resolution was the highest possible, not the one configured in the "System Configuration" menu.
Then, I modified the xorg.conf file (using vi editor ;) ) according to CatKiller indications and it's working for me.
I just specified the resolution I want in the screen section:
```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Modes   "800x600"
        EndSubSection
EndSection
```and modified the Device section this way:
```
Section "Device"
        Identifier      "Configured Video Device"
        Option  "UseEDID"       "False"    # LINE TO ADD
EndSection

```Concerning your "Monitor" section, I don't use it, but I'm not sure you have to write kHz at the end of the lines.

---

### Post by jebedia82 on 2009-07-18
Just to update you,only the "Screen" section update is needed in my case.
I don't have to update the "Device" section (for the UseEDID parameter) in order to have my resolution taken into account at every boot.

---

### Post by CatKiller on 2009-07-18
> **Robt6 said:**
> Ok, If I were to edit xorg.conf, so that it plays well with the KVM switch, can I expect problems if I upgrade the monitor? 

If you were to swap it for an older one that can't do the same resolution, then you'd need to change that file first. Either before you swapped the monitor or from a live cd. Especially if you've told X to ignore the EDID values.

> 
Also, what is the terminal command to edit xorg.conf? 


Sorry. You appeared more experienced than I guess you are. ```
gksudo gedit /etc/X11/xorg.conf
``` for a graphical text editor, or ```
sudo nano /etc/X11/xorg.conf
``` from the command line. Make a backup of the file first, just in case;
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
> 
would it, to be added to  look likt this?: 

I don't think you need the units either.
```
        HorizSync       30-61
        VertRefresh     56-75
```
should be fine.

> I'm just a little aprehensive, cause I think/believe if I screw up, the screen is gonna go blank and then it'll be lights out so to say.

It's easy enough to revert your changes from the command line, which you'd be able to get to from the Recovery mode menu when you boot the computer.

---

### Post by Robt6 on 2009-07-18
Ok, I get: "Could not save the file /etc/X11/xorg.conf.
You do not have the permissions necessary to save the file.(???)
using sudo gedit --- --- ---

---

### Post by CatKiller on 2009-07-18
Use gksudo with graphical applications like gedit. Use sudo for command-line programs like nano.

---

### Post by Robt6 on 2009-07-18
In the short amount of testing so far, it looks like adding these entries has worked:
Section "Monitor"
	Identifier	"Configured Monitor"
>        HorizSync       30-61 
>       VertRefresh      56-75

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
>SubSection "Display"
>                Modes   "1024x768"
>       EndSubSection

Even started up a couple of times with the KVM switched to the other computer, and resolution was correct. BTW, I really meant 1024x768, not 1280x--- in my first posts. Thanks to All for the assistance.
Will see how it goes over the next week, if all is OK, will edit firs post with SOLVED.

---

