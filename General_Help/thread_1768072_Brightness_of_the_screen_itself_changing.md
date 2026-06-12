---
title: "Brightness of the screen itself changing"
date: 2011-05-26
forum: General Help
---

### Post by pantich on 2011-05-26
I did last update to 11.04. And everything would be fine were it not that the brightness of the screen after a random (two minutes) to reduce the amount of time, to a random value (usually around 20-30%).
 I changed the settings in the preferences so that power is not shut down, also wearing the battery, but it's not work. Changing the settings in ubuntu tweak it did not help.
 If it will help in finding the problem, I have a laptop Lenovo IdeaPad Y560 Ati HD5730 card.
 Thanks in advance for your help.

---

### Post by emystein on 2011-08-23
I also have a **Lenovo Ideapad Y560 with an ATI Mobility Radeon HD 5730**. 
 
I tried to set /apps/gnome-power-manager/backlight/enable parameter to false in gconftool-2, following [http://askubuntu.com/questions/18603/how-to-stop-gnome-power-manager-from-changing-the-global-backlight-setting](http://askubuntu.com/questions/18603/how-to-stop-gnome-power-manager-from-changing-the-global-backlight-setting) but it didn't work for me. 
Then, a couple of days ago I have done a BIOS upgrade and that seems to have solved the problem. 

**My solution:**
 
I upgraded the BIOS to version 71, downloaded from the Lenovo driver download page specific to the Ideapad Y560 [http://consumersupport.lenovo.com/us/en/DriversDownloads/drivers_list.aspx?CategoryID=661448](http://consumersupport.lenovo.com/us/en/DriversDownloads/drivers_list.aspx?CategoryID=661448). 
 
To avoid downloading a wrong BIOS, I recommend you first to check your laptop model going to [http://consumersupport.lenovo.com/us/en/DriversDownloads/drivers.html](http://consumersupport.lenovo.com/us/en/DriversDownloads/drivers.html) and filling the form with your laptop serial number. 
 
**My specifications: **
 
Computer: Lenovo Ideapad Y560 
Processor: Intel Core i5 M560  @ 2.67GHz 
Graphics: ATI Mobility Radeon HD 5730 
 
OS: Ubuntu 11.04 
Video Drivers: ATI Propietary FLGRX Driver downloaded and installed via the Additional Drivers applet. 

Hope this helps.
Regards,

---

