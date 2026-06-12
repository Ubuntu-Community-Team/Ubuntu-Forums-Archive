---
title: "Graphics problems"
date: 2009-12-31
forum: General Help
---

### Post by Calum McFarlane on 2009-12-31
I'm new to Ubuntu so don't have much clue about how to fix this so help would be appreciated. I have a problem with opening windows. They open in the top left hand corner of the screen and block off the start bar, the windows don't have the normal bar at the top for minimising, closing etc... I cant drag the window out of the corner, enlarge it, minimise it, or make it go behind other windows that are open although the whatever is open in the window seems to run normally. Along with this problem the cursor is constantly stuck on the loading symbol. This is driving me crazy and stops me using Ubuntu, I'm forced back to using windows :( :(

---

### Post by MooPi on 2009-12-31
Truly a strange problem. Try this as a temporary fix, use ALT +left mouse and drag the window from corner.
Any help ?

---

### Post by Calum McFarlane on 2009-12-31
Nope seems to make no difference.

---

### Post by MooPi on 2009-12-31
Okay we'll try something else. With the mouse right click on an empty patch of desktop. Scroll down to create launcher. Under Name enter ```
Terminal
```Command enter ```
gnome-terminal
``` then click OK Let me know when you've completed. Are you still there ?

---

### Post by VastOne on 2009-12-31
> **Calum McFarlane said:**
> I'm new to Ubuntu so don't have much clue about how to fix this so help would be appreciated. I have a problem with opening windows. They open in the top left hand corner of the screen and block off the start bar, the windows don't have the normal bar at the top for minimising, closing etc... I cant drag the window out of the corner, enlarge it, minimise it, or make it go behind other windows that are open although the whatever is open in the window seems to run normally. Along with this problem the cursor is constantly stuck on the loading symbol. This is driving me crazy and stops me using Ubuntu, I'm forced back to using windows :( :(

Do you have compiz loaded? Emerald?  Do you have any proprietary drivers loaded for you gfx card? What card are you using?  

I have this same issue and have to reactivate visual effects every time I reboot, and I am running compiz and Emerald

Try going to System\Preference\Appearance\Visual Effects and trying the Extra setting to see if this gives you a fix.

---

### Post by Calum McFarlane on 2009-12-31
Ok have done that but the link doesn't work it says "Failed to execute child process genome (no such file or directory). I found that i can close a window using file close. 
VastOne - What is compiz and how do i find out what it is? Visual effects are set to None as setting to extra or normal does not work.I have ATI/AMD propriety FGLRX graphics driver. Card is ATI Radeon HD 3200

---

### Post by kevinatkins on 2009-12-31
This looks like a problem with desktop effects that can afflict some installations. Please could you confirm first whether the following works -

Go to System -> Preferences - > Appearance, on the window that appears, select the 'Visual Effects' tab and select 'None'.

You'll lose the drop shadows around windows and a few other nice effects, but hopefully your windows should now look normal..

---

### Post by VastOne on 2009-12-31
> **Calum McFarlane said:**
> Ok have done that but the link doesn't work it says "Failed to execute child process genome (no such file or directory). I found that i can close a window using file close. 
VastOne -How what is compiz and how do i find out what it is? Visual effects are set to None as setting to extra or normal does not work.I have ATI/AMD propriety FGLRX graphics driver. Card is ATI Radeon HD 3200

I would not worry about compiz now, if you do not know what it is it is not likely you have loaded it.

I think you need to have the correct radeon drivers for your system and I would start here in getting that

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Calum McFarlane on 2009-12-31
> **kevinatkins said:**
> This looks like a problem with desktop effects that can afflict some installations. Please could you confirm first whether the following works -

Go to System -> Preferences - > Appearance, on the window that appears, select the 'Visual Effects' tab and select 'None'.

You'll lose the drop shadows around windows and a few other nice effects, but hopefully your windows should now look normal..

The desktop effects have always been set to none as trying to change from this does not work. When I click on say "extra" it will try to load then the load box dissapears and "Extra" is selected but there is no change to desktop looks and if i close the window and open it again it is back to "None".

---

### Post by Calum McFarlane on 2009-12-31
> **VastOne said:**
> I would not worry about compiz now, if you do not know what it is it is not likely you have loaded it.

I think you need to have the correct radeon drivers for your system and I would start here in getting that

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Sorry if this is a stupid question but i can't find where to download the driver

---

### Post by VastOne on 2009-12-31
> **Calum McFarlane said:**
> Sorry if this is a stupid question but i can't find where to download the driver

Nothing stupid about any question....

I hate to say this but I had this card for 1 week struggling with what you are going through and then went out and bought a nVidia and never had an issue since...

You can get the drivers here

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

I have read that using Envyng will help with this as well.  Envyng is a driver management tool for nVidia and ATI and there are reports on Google that it has helped with the ATI

You may want to look at it

Good Luck

---

### Post by Calum McFarlane on 2010-01-23
Right, now back and reinstalled Ubuntu 9:10 to get rid of the old driver as previous problems made doing it the normal way a complete pain. The driver u suggested worked great thanks and allowed enabling of extra visual effects. 
That was all working fine for a couple of days until today when I tried to boot into Ubuntu and it came up with this error before the login screen "Ubuntu is now working in low graphics mode" it suggested a conflict with the kernal. Any help on this latest issue would be much appreciated.

---

