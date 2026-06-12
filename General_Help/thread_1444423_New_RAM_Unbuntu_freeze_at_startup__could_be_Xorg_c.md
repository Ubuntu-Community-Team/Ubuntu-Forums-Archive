---
title: "New RAM: Unbuntu freeze at startup / could be Xorg crash"
date: 2010-04-01
forum: General Help
---

### Post by Chesnut on 2010-04-01
Hello.
 My Ubuntu [9.10 (which is 64-bit)] crashes/freezes at startup, at the point where the login screen should appear. The mouse cursor icon pops up with the ubuntu background and that's it - that's where it freezes. My keyboard and mouse are unresponsive at the bootup process aswell. It happened after I had installed my new 4GB, but I am pretty sure my RAM is not faulty.

[SIZE="1"](The numpad lights on the keyboard are not working and the mouse scroll light is not flashing - they're not being detected at all?)[/SIZE]
 
My attempts to solve the problem:
*Tried reinstall - still same problem.
*Ran a memtest on my PC memory - took 50 minutes and no errors.
*Tried to run it in text mode (no Xorg) but I found out my keyboard and mouse are not working at the bootup.





[img]http://img40.imagefra.me/img/img40/2/4/1/chesnut/f_isjjm_d715de4.png[/img]



-------------------------


I fixed it! It was some kind of a hardware problem. First, I went on windows and uninstalled the unknown device drivers through the device manager, then I restarted windows and it said that installing the drivers failed and I shut the PC off, opened up the case and dusted it. Then I booted it up again, and it went up quicker than before, so I just chose Ubuntu in the GRUB menu and it worked. I even restarted it to double check it. I guess the dust had something to do with it.

---

### Post by Jive Turkey on 2010-04-01
I'm not really sure but some things you might try:
(in no particular order)
[LIST=1]
[*]Remove the DIMM from slot 3 and see if the system boots.
[*]Try slot 2 with the DIMM
[*]Double check you keyboard/mouse connections
[*]Try different keyboard/mouse.
[*]check your BIOS settings for keyboard related settings (ie USB keyboard enable) and expiriment with those.
[*]boot live cd, if keyboard works mount partition with the /var directory and look at the file /var/log/messages for hints and post them.
[/LIST]

---

### Post by Chesnut on 2010-04-01
> **Jive Turkey said:**
> I'm not really sure but some things you might try:
(in no particular order)
[LIST=1]
[*]Remove the DIMM from slot 3 and see if the system boots.
[*]Try slot 2 with the DIMM
[*]Double check you keyboard/mouse connections
[*]Try different keyboard/mouse.
[*]check your BIOS settings for keyboard related settings (ie USB keyboard enable) and expiriment with those.
[*]boot live cd, if keyboard works mount partition with the /var directory and look at the file /var/log/messages for hints and post them.
[/LIST]

My keyboard and mouse work just fine when booting to windows. It's just Ubuntu. (I dual boot and am writing this on Windows.)

---

### Post by M@se on 2010-04-01
similar problems with HP Pavilion 64 bit desktop. 6GB RAM. Whole rig is less than 30 days old and runs great on Windows 7. But cannot even get past the startup page of Ubuntu. Have tried about 4 times and 4 times had to power down

---

### Post by NCLI on 2010-04-01
Try his last suggestion, the one with the LiveCD.

---

### Post by Chesnut on 2010-04-02
I could not find anything suspicious. Here is the whole log:
[http://pastebin.com/LU900Sdj](http://pastebin.com/LU900Sdj)

-
Now I have a new theory: could it be an USB device? My port 5 reports an unknown device and I saw an error about it when I tried to run the safe-mode. I have no idea what the device could be, only USB things connected are my mouse and keyboard which are both detected.

---

### Post by dcstar on 2010-04-02
Run the memtest on your boot menu.

Linux pushes hardware a lot harder than Windows, what works in Windows can fail under full - Linux - load.

---

### Post by Chesnut on 2010-04-02
> **dcstar said:**
> Run the memtest on your boot menu.

Linux pushes hardware a lot harder than Windows, what works in Windows can fail under full - Linux - load.

I did. No errors.


I fixed it! It was some kind of a hardware problem. First, I went on windows and uninstalled the unknown device drivers through the device manager, then I restarted windows and it said that installing the drivers failed and I shut the PC off, opened up the case and dusted it. Then I booted it up again, and it went up quicker than before, so I just chose Ubuntu in the GRUB menu and it worked. I even restarted it to double check it. I guess the dust had something to do with it.

---

### Post by M@se on 2010-04-08
wow, if only it was that simply for me, lol

---

### Post by no2498 on 2010-04-08
M@se you using the 64 bit
dont think 32 bit will let you use 6 gigs of ram

---

### Post by M@se on 2010-04-10
yes, I use a 64 bit machine

---

