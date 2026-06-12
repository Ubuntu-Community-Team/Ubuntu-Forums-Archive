---
title: "list touchpad middle click after upgrade"
date: 2009-10-30
forum: General Help
---

### Post by xinix on 2009-10-30
I used to be able to do a middle-click by tapping the top-right corner of my touchpad.  This doesn't work after upgrading to Karmic.  Tapping the bottom-right still produces a 'right-click'.  
Any ideas on how I can solve this issue?

---

### Post by bluetwinkle on 2009-10-31
I have the same problem. I also never knew about the 2-finger and 3-finger clicks, but after trying it, 2 finger click gives me a right-click, and 3-finger clicks don't work for me. I really want my top-right corner back...

---

### Post by Chuckaluphagus on 2009-11-06
> **xinix said:**
> I used to be able to do a middle-click by tapping the top-right corner of my touchpad.  This doesn't work after upgrading to Karmic.  Tapping the bottom-right still produces a 'right-click'.  
Any ideas on how I can solve this issue?

This worked for me:

type ```
synclient RTCornerButton=2
``` at the command line and hit "Enter".  Should take effect immediately.

---

### Post by Deeday on 2009-11-08
Thanks _Chuckaluphagus_, that indeed works, but the effect only lasts until the next system reboot.
Does anyone know how to make that setting permanent? e.g. by adding that line to a script that is automatically executed at every system start-up; anyone knows how to set up such script?

Cheers!

---

### Post by xinix on 2009-11-09
Yay, middle click on the touchpad is back!  Thank you so much.

---

### Post by andretav on 2009-11-17
Deeday, 

I made this as that: System » Preferencies » Session Applications (my system is in portuguese, so the name can be different, but is the option of applicatons that run in the session start). 

In the programs app, click "add" and put the command in the entry. Name and describe it as you wish and save; it's done.

---

### Post by Deeday on 2009-11-20
Great! thanks _andretav_. I knew there was an easy way to do it.

Deeday

---

### Post by Taemojitsu on 2009-11-27
Add a HAL policy as the 'correct' way to set the permanent option. Described on these pages:
[https://help.ubuntu.com/community/SynapticsTouchpad#Configuration%20with%20HAL%20fdi%20files](https://help.ubuntu.com/community/SynapticsTouchpad#Configuration%20with%20HAL%20fdi%20files)
[https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL](https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL)

In my case, with tweaks done previously to change the size of the tapping regions specific to my touchpad, at location /etc/hal/fdi/policy/snyaptics.fdi there is the following text:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.RightEdge" type="string">5000</merge>
      <merge key="input.x11_options.LeftEdge" type="string">1944</merge>
      <merge key="input.x11_options.TopEdge" type="string">2000</merge>
      <merge key="input.x11_options.BottomEdge" type="string">3856</merge>
      <merge key="input.x11_options.RTCornerButton" type="string">2</merge>
    </match>
  </device>
</deviceinfo>
```

I'm not logging out for a while to make sure it worked, but if it didn't I would have updated this post.

---

### Post by matthewbpt on 2009-11-27
I thought HAL was being deprecated? There should be a new correct version to do this since the Ubuntu devs are starting to fade out HAL.

---

### Post by Taemojitsu on 2009-11-28
Could be. But it works lol (confirmed after restart/relog), and for all users on a computer.

I think the method that using a HAL policy is more current compared to, is adding it as a line in the X windows config file. X is supposed to be more automatic now or something.

So there may be a newer method as you say.

---

