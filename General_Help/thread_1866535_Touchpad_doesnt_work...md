---
title: "Touchpad doesnt work.."
date: 2011-10-21
forum: General Help
---

### Post by srikarreddy92 on 2011-10-21
I have installed UBUNTU 11.1 in my sony vaio laptop model no. VPCEH25EN.So whenever i logon to ubuntu my touch pad does work or respond properly...Please suggest me for rectifying it...

---

### Post by techvish81 on 2011-10-21
it works somewhat or it doesn't work at all? provide details.

---

### Post by srikarreddy92 on 2011-10-21
Initially it used to move to the corner automatically when I touch the touchpad..but now its not at all working...Please help..

---

### Post by techvish81 on 2011-10-21
remove xorg synaptics touchpad driver and try. (it can be removed and reinstalled with synaptic package manager or software centre.

---

### Post by geekman2 on 2011-10-21
I have the same problem but after i reinstalled the drivers it still doesnt work

---

### Post by techvish81 on 2011-10-21
dont reinstall it , just reboot, ur touchpad will work like mouse atleast without that driver, if u have reinstalled u can try this to see what happens,
go to mouse from the dash and deselect " disable touchpad while typing"

---

### Post by redtabulation on 2011-11-06
I have the exact same problem. I think the laptop model doesnt really matter since i have a dell 1564 inspiron. Anyway so it didn't work the first time i booted the system after upgrading to 11.10. 
I restarted and it worked.
Kept on working for a couple more sessions. 
Then stopped working altogether mid session. 
Cant get it back now. 

Removing the "synaptics touchpad driver(64 bit version)" works. Note: you gotta logout and then login for the changes to occur.

But i would rather have the bug free driver, because this feels a little weird since it doesn't accelerate or its too damn fast.

---

### Post by Maisondouf on 2011-11-06
I have installed 12.04 from net with mini.iso and my touchpad doesn't work also.

with an USB mouse, I go in system parameters-> mouse and touchpad.

I see that acceleration and sensibility where set to minimum.
I try to set them to max, but nothing after re-logging

So, I uncheck "deactvate druring...", exit and re-logging.

Now touchpad is ok

nota: this on a Packard Bell Dot-S netbook
module psmouse is loaded for pad and usbhid for usb mouse

---

