---
title: "MSI U120 Screen dim issue 11.10"
date: 2011-10-29
forum: General Help
---

### Post by mundbora on 2011-10-29
First off I think Ubuntu is great with one exception. My U120 has to be plugged in for the brightness to work. If I try to adjust it with the FN buttons or the software brightness control the screen flickers and system freezes.
I'm trying out 10.04 to see if that works but if this problem is corrected I will be back to 11.10 for sure.

Thanks to everyone who contributes and the creators of Ubuntu :)

---

### Post by mundbora on 2011-10-30
I have found an acceptable work around for this. 

First I had to stop the gnome from adjusting the brightness. That was simple enough due to the advice and commands given here:  [http://askubuntu.com/questions/18603/how-to-stop-gnome-power-manager-from-changing-the-global-backlight-setting](http://askubuntu.com/questions/18603/how-to-stop-gnome-power-manager-from-changing-the-global-backlight-setting)

Now, before I use my F4-F5 keys to adjust the brightness I click any of the drop down menus at the top right hand corner. For some reason, this stabilizes the brightness controls and everything works fine.  If I don't do that (especially on battery) everything freezes and I need to reboot.

This is good enough for me :)

---

### Post by Guðni on 2011-10-31
Thank you, this worked for me as well on MSI PR-200.

In my case it always got very unresponsive as soon as I unplugged the AC cord. And even if I opened System Settings -> Screen.

I have to say though that it is a bit weird that it doesn't freeze with drop down menus open.

---

### Post by mundbora on 2011-10-31
> **Guðni said:**
> Thank you, this worked for me as well on MSI PR-200.

In my case it always got very unresponsive as soon as I unplugged the AC cord. And even if I opened System Settings -> Screen.

I have to say though that it is a bit weird that it doesn't freeze with drop down menus open.


Glad to hear it! I'm still hoping for this issue to be worked out for the next release.

Cheers

---

### Post by trukker on 2011-11-02
I have exactly the same problem... but on an MSI PR-200

Starting System Settings->Screen locks up the whole system... I've used the posts above to turn off the Dim setting, but the result is the same: total lockup requiring a hard reboot.

Any ideas? Or at least how to report the bug?

---

### Post by mundbora on 2011-11-02
> **trukker said:**
>  
Starting System Settings->Screen?
 
I'll take a look at this later. 
I reloaded Ubuntu yesterday and watched the install process. You can actully see when the problem is injected during the install software phase towards the end. If there was some way to completely remove whatever is causing it I would be happy enough using the keys to adjust the brightness. I have heard that disabling the FN keys works but I don't know how to do that.
 
I also noticed that my Wifi is still being dropped if I uspend the computer on battery and need to reboot to get it back.
 
Without these bugs I would be completely sold on this software. Maybe 12.04 will correct it?

---

### Post by mundbora on 2011-11-02
> **trukker said:**
>  
Any ideas? Or at least how to report the bug?
 
Bug reporting :)
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by mundbora on 2011-11-02
I just stumbled upon this...maybe this will help with U120s!
 
 
[http://www.pcworld.idg.com.au/review/notebooks/msi/wind_u120/296965](http://www.pcworld.idg.com.au/review/notebooks/msi/wind_u120/296965)
"If you do want to put Linux on the Wind U120, the forums at [[COLOR=#0080c0]MSIWind.net[/COLOR]]("http://forums.msiwind.net/default-msiwind") have plenty of tips and information on where to get drivers. " Links broken..sorry

---

### Post by mundbora on 2011-11-04
Update. I don't need to use a pull down menu to stabilize the brightness control after all. If I press Fn + Alt and then the brightness controls everything works fine. I still have to Disable Battery dimming and it doesn't resume if I close the lid on battery power.

---

### Post by federoma on 2011-11-11
I resolved by updating the BIOS firmware.

---

### Post by mundbora on 2011-11-12
> **federoma said:**
> I resolved by updating the BIOS firmware.

I read that would work...but am leery of killing my netbook as I don't have a dual boot machine and Linus Flashing freaks me out LOL.

---

### Post by mundbora on 2011-11-13
> **federoma said:**
> I resolved by updating the BIOS firmware.

Thanks for making me look at this option again! I flashed the bios with Freedos (after hours of research LOL) The dimming issue is now fixed! Now it's just the suspend and losing wireless when on battery...back to it!

---

### Post by mundbora on 2011-11-14
> **mundbora said:**
> Update. I don't need to use a pull down menu to stabilize the brightness control after all. If I press Fn + Alt and then the brightness controls everything works fine. I still have to Disable Battery dimming and it doesn't resume if I close the lid on battery power.
 
All issues have been fixed! 
 
-Flashed my bios the Ubuntu way with Freedos and USB, (flickering/freezing stopped with brightness control and FN keys)
-Reloaded 11.10
-Rooted
-Found a script to solve the wireless dropping on battery resume, 
-and disabled screen dimming when I unplug to stop the system from freezing
 
I'm totally happy now

---

