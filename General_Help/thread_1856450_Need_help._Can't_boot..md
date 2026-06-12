---
title: "Need help. Can't boot."
date: 2011-10-08
forum: General Help
---

### Post by fatteralbert on 2011-10-08
I made some changes in a config file to get my wacom to work, but now I can't start Ubuntu. 

This is what I did. I opened 50-wacom.conf typing 

gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf

Then I put the following in the file:

[I][I]Section "InputDevice" 
        ...              
Option          "TopX"        "100" 
             Option          "TopY"        "200"               
Option          "BottomX"     "14000"         
Option          "BottomY"     "6000"         
...     
EndSection

[/I][/I]After that  I tried to reboot, but I get nothing. The screen is just black. [I][I]

I realise now that it wasn't the smartest thing to do just copy and paste the text from internet whitout thinking[/I][/I]

You can understand my panic. I need to get it back up. 

Please help!

---

### Post by collisionystm on 2011-10-08
> **fatteralbert said:**
> I made some changes in a config file to get my wacom to work, but now I can't start Ubuntu. 

This is what I did. I opened 50-wacom.conf typing 

gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf

Then I put the following in the file:

[I][I]Section "InputDevice" 
        ...              
Option          "TopX"        "100" 
             Option          "TopY"        "200"               
Option          "BottomX"     "14000"         
Option          "BottomY"     "6000"         
...     
EndSection

[/I][/I]After that  I tried to reboot, but I get nothing. The screen is just black. [I][I]

I realise now that it wasn't the smartest thing to do just copy and paste the text from internet whitout thinking[/I][/I]

You can understand my panic. I need to get it back up. 

Please help!

Keep tapping the UP arrow key while the system is booting. This will get you to the grub menu. See what options you have from there. Try an older kernel maybe?

Also, get a live cd and edit that file.

---

### Post by fatteralbert on 2011-10-08
tapping the up button worked. 

I got the grub menu and tried failsafe grafic mode. got the answer "no screens found" 

so I try "Drop to root shell prompt" but I need help. How can I edit the corrupt file from there?

---

### Post by ajgreeny on 2011-10-08
From the root shell prompt use ```
nano /usr/share/X11/xorg.conf.d/50-wacom.conf
```then edit the file back to what it was.  Use the cursor keys to move around the file and after editing, Ctrl+X to save it.  Then reboot.

If that does not work you can try renaming the file as a backup ```
mv /usr/share/X11/xorg.conf.d/50-wacom.conf /usr/share/X11/xorg.conf.d/50-wacom.confbak
```and again reboot.

---

### Post by fatteralbert on 2011-10-08
it's working now. thanks a bunch.

---

