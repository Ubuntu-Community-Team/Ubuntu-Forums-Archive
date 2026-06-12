---
title: "How to sync my Palm m130"
date: 2009-12-04
forum: General Help
---

### Post by RJ12 on 2009-12-04
Okay so I want to sync my Palm m130 with my USB cable. Do I install jPilot and then just plug in the palm or do I have to do anything else or... I am going to be wanting to sync apps on the palm also, so how would I go about this

---

### Post by sgosnell on 2009-12-04
It depends on what you want to sync to.  You can sync to Evolution, which will sync your calendar, memos, and contacts, or you can sync to JPilot, which will sync Keyring in addition.  Both will back up your apps.  Most other app conduits don't work, though.  Those sync conduits are written by the developers, who don't often offer Linux conduits.  

Gnome-pilot, which is installed in Ubuntu and does the sync with Evolution, will detect the Palm through the setup.  You can use that information to determine the settings for JPilot.  JPilot won't connect automatically, you have to enter the settings into the preferences, and click the hotsync button in it every time before you start the sync on the Palm.  Evolution will run gnome-pilot and sync automatically.  I tend to keep both synced, at different times.  You don't have to choose one or the other, you can sync to both, but might unexpected results now and then.

---

### Post by RJ12 on 2009-12-04
So this is what I need to do....?
1.Setup "PalmOS" Devices in System>Preferences
2.Install Jpilot
3.??

Also I dont want the keyring synced, will it give me a option not to do that?

Edit: I don't use evolution currently so I won't be using that

---

### Post by sgosnell on 2009-12-04
It will only sync Palm Keyring if you install the plugin and enable it.  This is not the Ubuntu keyring, it's something entirely different, a password safe for PalmOS.

Install JPilot, then go to File/Preferences and set things how you want.  You will have to select the correct port, and I have no idea what that is on your system.  You can go to System/Preference/PalmOS Devices and set up gnome-pilot, and if you add a device you can choose to have it detect the Palm.  That should give you the settings you need for JPilot.

JPilot is the closest thing to Palm Desktop I've seen for Linux, but it might be possible to run Palm Desktop in wine.  I've never tried it, but I may try ti someday just for grins.

---

### Post by RJ12 on 2009-12-04
Okay I will start installing JPilot



As for the Wine thing it will not work as there is no access to USB with wine (Keep that in mind)

---

### Post by RJ12 on 2009-12-04
Well it dosent seem to syncing. I set it up as usb: as it kept telling me to use that one..... but when I try to sync using JPilot nothing happens. Pulling up a terminal and typing lsusb sees the palm m130 but.....nothing on the pilot it eventually gives up and says could not establish connection

---

### Post by sgosnell on 2009-12-04
usb: won't work.  It should be one of the ttyUSB# entries.  I just dug out my USB cable and tried unsuccessfully to sync my Lifedrive that way.  I didn't mess with it too much, because I sync via wifi.  Obviously that isn't an option with an M130, though, and you may have to experiment with different devices.  /dev/pilot might work, I don't know.  Like I said, I sync via wifi, so I haven't done much in the USB area.  There should be several threads on the forum about this, though, and one of them should be of help to you.

---

### Post by RJ12 on 2009-12-04
Well the others werent working but I will try again :)

Update: It says could not connect to /dev/ttyUSB0/ Check your config as you requested old style usb serial but do not have the usb serial `visor' Kernel Module loaded. You may have to select a usb: device (Hence the trying with usb: )

---

### Post by sgosnell on 2009-12-04
Well, I'm not sure what to put after the usb:.  I use net:any for wifi.  Google might have some help...

---

### Post by RJ12 on 2009-12-04
Okay so now I think I may have found some instructions. I need to load the visor module with sudo modprobe visor is this safe to do. I dont want to mess up my computer

---

### Post by sgosnell on 2009-12-04
That should load the module named visor.  Shouldn't be a problem.

---

### Post by RJ12 on 2009-12-04
Well its syncing with Evolution but I'm okay with that. I will just start using evolution with calendaring and maybe email.


Thanks for all your help!

---

### Post by sgosnell on 2009-12-05
I fired up my old T3, and got it to sync with jpilot using usb:any.  Actually, it crashed, because it tried to sync with the newer PIMs from the Lifedrive, and it naturally choked on them, but the sync did start, and the path was recognized.

---

### Post by RJ12 on 2009-12-05
Ok well usb:any didnt work but I'm fine with using Evolution. I just wanted jpilot for the gui of installing apps but I like using the Terminal better:p but I still have to run sudo modprobe visor everytime I boot up the computer...... I heard I have to add something to a modules file. How would I achieve that?

I'm gonna mark this thread as solved now


This is why I love Ubuntu, because when I need help there is always people willing to help others:D

Thanks for you guy's time!

---

### Post by sgosnell on 2009-12-05
It should sync without any other futzing if you have Evolution running.  Evolution should start gnome-pilot, and that's what you need to have running to initiate the sync outside JPilot.  JPilot has its own sync method, but you have to click on the hotsync button there as well as on the Palm for it to work.  If gnome-pilot is running, you can sync without doing anything else.

If you put gnome-pilot in the startup programs (System/Preferences/Startup Programs) you shouldn't need to run the modprobe command.

---

