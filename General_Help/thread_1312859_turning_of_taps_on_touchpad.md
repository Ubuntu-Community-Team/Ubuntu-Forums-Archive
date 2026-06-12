---
title: "turning of taps on touchpad"
date: 2009-11-03
forum: General Help
---

### Post by frrobert on 2009-11-03
I am running Ubuntu 9.04 CLI install with openbox on a 1000ha eee.

I am trying to turn off the taps on the touchpad.

I created an fdi file and put it in /etc/hal/fdi/policy/ and rebooted but the taps still work.  Any ideas?  Below is the code in the file.

Thanks in advance.

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!-- 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">

  <device>
   <match key="input.x11_driver" string="synaptics">
<merge key="input.x11_options.TouchpadOff" type="integer">2</merge>
</match>
  </device>


</deviceinfo>

```

---

### Post by P4man on 2009-11-03
Did you see this>
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Should be as simple as disabling it in mouse preferences.

---

### Post by KeLa on 2009-11-03
Have you tried from menu:
System->Preferences->Mouse
and there on Touchpad tab uncheck the
"Enable mouse clicks with touchpad"
That works for me on several different laptops
even on eee 901.

---

### Post by frrobert on 2009-11-03
Thanks for the ideas but I did a command line install then installed xorg,then open box, so I don't have the graphical preference dialogs.

I could not get the fdi file to work but I did figure out another route.

xinput set-int-prop "ETPS/2 Elantech Touchpad" "Synaptics Off"  8 2

which turns off the taps on the touchpad using xinput.

---

