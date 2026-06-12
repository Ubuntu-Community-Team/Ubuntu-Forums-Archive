---
title: "Samsung laptop disabling touchpad on startup"
date: 2011-05-06
forum: General Help
---

### Post by mamboze on 2011-05-06
Hi,
I've just installed 10.04 on a Samsung RV511 laptop. No problems and much, much better than the Windows 7 it came with. But I do have just a little niggle. I can disable the touchpad with 'modprobe -r psmouse' after I've logged in, but I would like this to happen automatically at startup. 

I've tried putting the above code in the home folder .bashrc, but I get this error message:

FATAL: Error removing psmouse (/lib/modules/2.6.32-31-generic/kernel/drivers/input/mouse/psmouse.ko): Operation not permitted

Do I need to write a bash script file? Or how else can I get the code to run as I want? 

Any help much appreciated. :D

---

### Post by ububeginner on 2011-05-06
You could try going to system>preferences>startup applications and select add, put your command in the command box and give it a name like "disable touchpad"

---

### Post by mamboze on 2011-05-06
Thanks for your help, but no success. 

I installed GSynaptics in the hope that it may help, but when I click on the Preferences>Touchpad option, I get this error message:

"GSynaptics couldn't initialize.
You have to set 'SMHConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

I've found the folder xorg.conf.d but no xorg.conf. I couldn't find XF86Conf.

I think I have to put a bash script in a file somewhere but I'm not sure where. I've read online that chmod has to be invoked for the file to be treated as executable.

Any suggestions welcome  :)

---

### Post by mamboze on 2011-05-07
Just an update! 

I've tried the procedure set out here:

[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

using this:

#!/bin/bash
modprobe -r psmouse

saved as touchpad_disable

and placed in /etc/init.d

but no success. 

What to try next? I'm out of ideas. I'm obviously missing something here.

---

### Post by mamboze on 2011-05-07
Further explorations

I've followed the procedure set out in: 
[http://crunchbanglinux.org/forums/topic/4282/disabling-touchpad-taptoclick-with-gsynaptics-nb-the-caveat/](http://crunchbanglinux.org/forums/topic/4282/disabling-touchpad-taptoclick-with-gsynaptics-nb-the-caveat/)

again, no dice, error message for gsynaptics as before.

Does anybody know how to setup a laptop so that the touchpad is disabled on startup??  Surely, this can't be rocket science.

---

### Post by mamboze on 2011-05-08
OK, I've been playing around with this stuff all day and I'm reasonably sure this is how it's done. Anyhow, it is somewhere near the mark.

save a script file like touchpad_disable in /etc/init.d

install and run Bootup Manager (BUM) and reboot (not sure that this reboot is necessary)

find and activate touchpad_disable in BUM.

Reboot and the touchpad is disabled. :D :D

---

### Post by spcwingo on 2011-05-08
Have you tried blacklisting that module?  Open a terminal and enter this command:

```
sudo nano /etc/modprobe.d/blacklist.conf
```

At the end of that file enter this:

```
blacklist psmouse
```

Save and close (CTRL+O followed by CTRL+X).  That should keep it from loading at all.  :)

---

### Post by mamboze on 2011-05-08
Thanks for the suggestion. I hadn't thought of blacklisting (only knew of it vaguely). But I'll give it a run. It looks a simpler way to disable the touchpad.

---

### Post by GaryLittlemore on 2011-06-21
Mamboze, I've just bought a Samsung RV511 was your install instead of Win 7 or along-side it? I'm looking to know if I'll get any problems installing along-side Win 7

---

### Post by mamboze on 2011-06-28
@GarryLittlemore, sorry for the delay in responding to your query.
I discarded win7 and installed 10.04. No problems at all with the installation. Video OK and wifi driver (Broadcom) worked straight off. I do need windows for apps for which no equivalent exists in Linux (that I know of), one is some OCR software and the other is a multimedia RAD. For this, I installed VirtualBox. This is a very stable arrangement. I also have had it installed on a desktop for more than a year. The only downside with VB is a speed reduction, which with a dual core CPU is hardly an issue, at least for my requirements.

Hope this helps

---

### Post by lemhop on 2011-07-07
> **spcwingo said:**
> Have you tried blacklisting that module?  Open a terminal and enter this command:

```
sudo nano /etc/modprobe.d/blacklist.conf
```

At the end of that file enter this:

```
blacklist psmouse
```

Save and close (CTRL+O followed by CTRL+X).  That should keep it from loading at all.  :)
Thanks spcwingo, worked a treat after a reboot \o/

---

### Post by spcwingo on 2011-07-07
> **lemhop said:**
> Thanks spcwingo, worked a treat after a reboot \o/

No problem, I'm just glad to have helped someone.  Have fun with Ubuntu.

---

### Post by mamboze on 2011-07-17
Hi,

I installed a larger HD on my laptop and reinstalled 10.04.2. 

to spcwingo, I tried your technique, it's quick and easy to setup and worked great, thanks  :D

---

### Post by spcwingo on 2011-07-17
> **mamboze said:**
> Hi,

I installed a larger HD on my laptop and reinstalled 10.04.2. 

to spcwingo, I tried your technique, it's quick and easy to setup and worked great, thanks  :D

Cheers!  :D

---

### Post by eneville on 2012-12-24
I know it's already solved, but this seems ideal to me:

```

# lsusb | grep -i mouse >/dev/null && sudo rmmod psmouse

```

This way, at script run time (start up, I've put this in /etc/rc.local) the touchpad mouse can be removed.

Obviously, it doesn't insert the module again if the mouse is unplugged.

---

