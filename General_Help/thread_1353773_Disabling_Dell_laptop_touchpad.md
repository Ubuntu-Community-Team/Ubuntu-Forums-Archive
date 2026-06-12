---
title: "Disabling Dell laptop touchpad"
date: 2009-12-13
forum: General Help
---

### Post by reldon on 2009-12-13
I have installed the new 9.10 Ubuntu on my Dell laptop.  In the old version I could disable the touchpad.  Is there a way to do this with version 9.10?
For some reason I cannot find any option in the System-Mouse preferences dialog.  It only let's me disable it while typing.

Thanks,

Rel

---

### Post by smerral on 2009-12-13
Try:

sudo synclient TouchpadOff=1

To re-enable:

sudo synclient TouchpadOff=0

---

### Post by john newbuntu on 2009-12-13
Thanks for teaching me something new today Smerral.

---

### Post by Leppie on 2009-12-13
Is there a way to disable it automatically when an external mouse is plugged in, and disable it when the external mouse is removed?

---

### Post by pbrane on 2009-12-13
> **Leppie said:**
> Is there a way to disable it automatically when an external mouse is plugged in, and disable it when the external mouse is removed?

It's possible using udev rules. I have not been able to make it work consistently. You can google it and see if you find a solution that works. Another thing you can do is use this script to to manually enable/disable the touchpad depending on whether the mouse is plugged in. I assigned it to CTRL-F10 in gnome.

```

#!/bin/bash

if [ "$(grep -e Logitech /proc/bus/input/devices)" ]; then
		xinput set-int-prop "AlpsPS/2 ALPS GlidePoint" "Device Enabled" 8 0
else
		xinput set-int-prop "AlpsPS/2 ALPS GlidePoint" "Device Enabled" 8 1
fi

```

Run **xinput -list** in a terminal to get the name of your touchpad. Replace "Alps/PS2 ALPS GlidePoint" with the name of your touchpad.

And also replace "Logitech" in the test line if you have a different USB mouse vendor. You can **cat /proc/bus/input/devices | grep Mouse** to find the vendor name of your mouse. I have two entries in there so I can't use just "Mouse".

---

### Post by Themotorman on 2009-12-13
> **smerral said:**
> Try:

sudo synclient TouchpadOff=1

To re-enable:

sudo synclient TouchpadOff=0

I have loaded xubuntu 9.10 on an old Dell laptop 5000, the mouse did work until I updated now it doesn't. I thought that using synclient as above might do the job but I get e amsg that syn... is not loaded. Any ideas please? Thank you.

---

### Post by pbrane on 2009-12-13
make sure synclient is installed. you can try **sudo apt-get install xserver-xorg-input-synaptics** in a terminal. If it is installed it will say so, otherwise it will install the package. Or, of course, you can always launch synaptic package manager and check that way.

---

### Post by reldon on 2009-12-17
thanks for the help!!

---

### Post by CrazyCellist on 2009-12-25
With my old Dell, it wasn't so much the TouchPad annoying me, as it was the random Keyboard Stick movement.  Here's what my Latitude D800 needed:

xinput set-int-prop "DualPoint Stick" "Device Enabled" 8 0
xinput set-int-prop "AlpsPS/2 ALPS DualPoint TouchPad" "Device Enabled" 8 0

---

### Post by smerral on 2009-12-25
well I tried the "sudo synclient TouchpadOff=1" myself and it worked for so long and then touchpad re-enabled itself. I finally solved it by doing:

sudo modprobe -r psmouse

(to re-enable:

sudo modprobe psmouse)

If you edit edit/init.d/rc.local and put the command immediately below #! /bin/sh you can run it at boot.

Hope this helps!

Oh and merry xmas!!

---

### Post by dond on 2010-01-31
> **smerral said:**
> well I tried the &quot;sudo synclient TouchpadOff=1&quot; myself and it worked for so long and then touchpad re-enabled itself. I finally solved it by doing:

sudo modprobe -r psmouse

(to re-enable:

sudo modprobe psmouse)

If you edit edit/init.d/rc.local and put the command immediately below #! /bin/sh you can run it at boot.

Hope this helps!

Oh and merry xmas!!

Many thanks. This did work for me (Dell Studio 1555) though none of the previous posts did even though synclient was installed but perhaps the outstanding bug (#380126) may be relevant.

I tried to gedit edit/init.d/rc.local but saw only a blank page with no sign of #! /bin/sh so I left it alone. Would be good if the computer could detect the mouse at boot and disable the touchpad. I seem to remember this not being a problem with earlier versions of Ubuntu but then again my earlier laptop had a button which disabled/enabled the touchpad whereas the Dell does not.

---

### Post by dasunsrule32 on 2010-02-18
> **dond said:**
> Many thanks. This did work for me (Dell Studio 1555) though none of the previous posts did even though synclient was installed but perhaps the outstanding bug (#380126) may be relevant.

I tried to gedit edit/init.d/rc.local but saw only a blank page with no sign of #! /bin/sh so I left it alone. Would be good if the computer could detect the mouse at boot and disable the touchpad. I seem to remember this not being a problem with earlier versions of Ubuntu but then again my earlier laptop had a button which disabled/enabled the touchpad whereas the Dell does not.

If you are doing:

```

gedit edit/init.d/rc.local

```Then, yes, that is all you are going to see. You need to:

```

sudo gedit /etc/rc.local

```That will get you where you need to go. Holla!

---

### Post by pi/roman on 2010-02-18
> **Leppie said:**
> Is there a way to disable it automatically when an external mouse is plugged in, and disable it when the external mouse is removed?

I created a method here:[[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1401645[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1401645")

In the Addendum section c: toggle when using usbmouse.

---

### Post by Ishmayl on 2010-02-21
> **smerral said:**
> well I tried the "sudo synclient TouchpadOff=1" myself and it worked for so long and then touchpad re-enabled itself. I finally solved it by doing:

sudo modprobe -r psmouse

(to re-enable:

sudo modprobe psmouse)

If you edit edit/init.d/rc.local and put the command immediately below #! /bin/sh you can run it at boot.

Hope this helps!

Oh and merry xmas!!

That worked for me, thanks !

---

### Post by JEBB on 2010-05-20
I was successful using the method as per dasunsrule32.  I had to be told that a command needed to be entered without the leading # to be recognized as a command.  Now the typing problem appears to be history.

---

