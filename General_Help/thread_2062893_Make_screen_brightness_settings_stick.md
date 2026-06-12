---
title: "Make screen brightness settings stick"
date: 2012-09-25
forum: General Help
---

### Post by chellrose on 2012-09-25
I have a Toshiba Satellite running 11.10 with TDE.  I want to have the laptop's screen brightness be quite a bit lower than the default.  The Fn hotkeys for brightness, for this particular model, haven't played well with Ubuntu since Jaunty or so.  Thus, I have a little script that I run to manually set the brightness level.

I've figured out how to make the script run on startup so that the brightness will automatically be set.  However, any time I close my laptop's lid, the screen reverts to the default brightness when the lid is opened.  I have it set to not do anything special when I close the lid, so it isn't hibernating/suspending/whatever.

Is there a way to make the brightness setting from the script stick?

Thanks. :)

---

### Post by bra|10n on 2012-09-26
Just a question, and not relating to your script...

Does adding 'acpi_osi=Linux' to your kernel's boot parameters not work on your laptop?

---

### Post by chellrose on 2012-09-27
Thanks for the suggestion; I hadn't tried that before.

Unfortunately, I added acpi_osi=Linux to my boot parameters, and it doesn't appear to have had any effect.

---

### Post by bra|10n on 2012-09-27
I sort of thought it wouldn't but it is the easy option 'when it works'.
There used to be a package in the Ubuntu repo's for Toshiba hardware, "toshset?" or something...
You might investigate that, afterall it's only a package search...

EDIT
The setting in KDE related to closing of laptop is buggy; by chance have you tried your script with this setting disabled. 
I know this sounds odd, but not half as odd as when you hover and read the accompanying tooltip...

Good luck.

---

### Post by chellrose on 2012-09-28
I'm pretty sure I do have that setting disabled.  In KLaptop, I go to "Configure KLaptop", then the "Button Actions" tab.  I'll attach a screenshot to show what my settings are.

---

### Post by bra|10n on 2012-09-28
Wowl that's a blast from the past. What KDE version are you running? 

Anyway, I'm now curious as to the system performance settings. Have you looked into what might be 'deactivated' for want of a better word, for each of the different modes, thinking maybe user scripts are ignored perhaps under conservative?, even though I can see it's disabled. Maybe select the equivalent of 'high octane' and then revert to setting to "off" again. Stranger things happen in KDE...

But look into **toshset** or whatever it's called I mentioned earlier. It might just be the easier solution.

Just a quick snapshot of what I was talking about earlier regarding the tooltip, to which you are probably still scratching your head,

[IMG]http://i.imgur.com/ZCsqh.png[/IMG]

And the tooltip reads: [COLOR=RoyalBlue]"When this option is selected, applications will not be allowed to inhibit sleep when the lid is closed."[/COLOR]

---

### Post by bra|10n on 2012-09-28
> **Sissy13 said:**
> Thanks for the suggestion; I hadn't tried that before.

Unfortunately, I added acpi_osi=Linux to my boot parameters, and it doesn't appear to have had any effect.

I just remembered. I forgot to tell you to run sudo update-grub after adding the above line. Duh!
Not sure if you did or not. Here a reboot is also needed.
This is aimed at getting your Fn keys working as they should.

---

### Post by chellrose on 2012-09-28
I'm using Trinity, which is the current project aimed at maintaining the KDE 3.xx style desktop environment.   I suspect the brightness/Fn key issue is an underlying Ubuntu problem, though, because GNOME posed the same problems in earlier Ubuntu releases.

I find one package called "toshset" in my package manager, and it seems to be already installed.  The package description is
> 
Application lens for unity
This package contains the "application" lens which can be used inside Unity to launch and install applications.
I also searched for packages beginning with just "tosh" and didn't turn up anything new.  I think there used to be a toshutils package, but that doesn't seem to exist now.

I did run sudo update-grub and reboot after adding that line to my kernel's boot parameters.  Unfortunately, it didn't appear to do anything.

Thanks. :)

Edit: I think I do still have Unity installed (since it was installed by default with my Ubuntu install), but I never use Unity.  Could Unity packages/settings be conflicting with those from TDE?  If so, how do I uninstall Unity without breaking other things?  Searching "Unity" in the package manager yields a whole list of packages, none of which appear to be the actual underlying DE.

---

### Post by bra|10n on 2012-09-30
@Sissy13,

I happen to be googling some errors earlier and came upon quite a few posts Toshiba/acpi related. Many linked to some older bug reports still without resolution, with the more recent postings accepting that nothing more than you have already done with your script can be achieved. I failed to find 1 person who resolved the "remember screen brightness" issue after either sleep/logout/reboot.
All I can do is suggest you use a shortcut in the system tray where you can toggle your script on/off easily. This confirms neither TDM or Unity d/e are to blame here and this is purely a hardware issue. Unfortunate...

---

### Post by chellrose on 2012-09-30
That *is* unfortunate.

The script I'm using to change the brightness manually looks like this:
```

#!/bin/bash
setpci -s 00:02.0 F4.B=18

```
(where the "18" can be edited to increase or decrease the set brightness.  IIRC, it can be anything from 0 to 100.)
To make it work, I have to run it with "sudo".  Do you know if there is a way to do this without sudo?  Right now I'm just running it from the command line every time it's needed, which of course entails typing in my password _every_ time.  Gets a little old, and it would be particularly useful to "de-sudo" this if I am to make a tray icon as you suggested.

Thanks!

---

### Post by bra|10n on 2012-09-30
```
#!/bin/bash

ksystraycmd --startonshow --keeprunning --tooltip "Adjust Screen" --icon application-pgp-signature ~/.screen_brightness.sh
```Above is a small script which you can make executable and add to autostart. It will place an icon in your sys_tray on startup by which you can toggle on/off your existing script (which for this purpose I have referred to as ".screen_brightness.sh"), and I have assumed lives in your home folder. (note the . (hidden file)). Names and file locations of course can be changed to your liking ;)

But only add the above script to autostart as this script will then call your script as required.
Why your script needs root privileges to function I really don't know. If it is owned by you, and not root, does it still function? I can't imagine screenbrightness settings needing elevated privileges TBH.

But i'm not a bash expert by any means. Perhaps others might be able to offer some advice on this?

---

### Post by chellrose on 2012-09-30
Thanks!  I'll give that system-tray script a go.  Does the screen_brightness.sh *need* to be hidden for some special reason?  (Right now, it isn't, but I can certainly do that.)

The existing script is owned by me and executable by me.  When I try to run it without permissions I get this error:
```

pcilib: Cannot open /sys/bus/pci/devices/0000:00:02.0/config

```

---

### Post by bra|10n on 2012-10-01
Please check the contents of /etc/pm/sleep.d/ for files relating to resume/wake. 
Check any files with a text editor and *hopefully* you will recognize some code.
Here is the contents of 1 file here,
```
#!/bin/sh
#
# 90alsa: suspend/wakeup ALSA devices

case "$1" in
hibernate|suspend)
;;
thaw|resume)
aplay -d 1 /dev/zero
;;
*) exit $NA
;;
esac
```I wonder if your script can't be incorporated into this one or called from this alternatively?

---

