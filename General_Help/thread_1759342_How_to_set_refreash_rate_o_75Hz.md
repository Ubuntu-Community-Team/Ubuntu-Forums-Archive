---
title: "How to set refreash rate o 75Hz"
date: 2011-05-15
forum: General Help
---

### Post by fahd47 on 2011-05-15
Hi guys i have just installed ubuntu 11.04.The thing is my screen is flickering but i cant find how o set my refresh rate o 75Hz to stop it.In the monitors panel it says monitor is unknown and i can only set the refresh rate as 50,51 and 52 Hz.Please help me how to set it to 75

[IMG]http://i653.photobucket.com/albums/uu258/fahd47/Screenshot.png[/IMG]

---

### Post by ajgreeny on 2011-05-15
You may find you can set it in a custom /etc/X11/xorg.conf, which you may need to make if you don't already have one.  I hjad to do this a long time ago with a CRT display, but it is never needed now normally.
The section I used was
```
Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```the figures having come from the monitor specification in its manual.  You wil note that also had to include resolution figures at that time.

---

### Post by fahd47 on 2011-05-15
thnx for replying but i am a newbie to ubuntu(1st installation ever).SO i dont know what to do with all that code.
Can u explain  in steps what i need to do.Oh and yes my monitor is not crt it is a lCD monitor HP  FP1707

---

### Post by ajgreeny on 2011-05-15
Firstly find you monitor refresh rates from the manufacturer's info on it, probably in the handbook listed specification.

Edit the figures I gave you in my version:-
```
HorizSync    30-80
VertRefresh    50-75
```and change to yours.

Open a terminal from the launcher on the left and in that type ```
gksudo gedit /etc/X11/xorg.conf
```hit return and the file wil open.  It may be empty, but don't worry about that, just paste the first part of my example in```
Section  "Monitor"
     Identifier        "Configured Monitor"
         HorizSync    30-80
         VertRefresh    50-75
EndSection
```with your own figures instead of mine, save the file and try logging out and back in again.  You can ignore the second part of my example which I only included as more info, but it shouldn't be needed.

---

### Post by fahd47 on 2011-05-15
i did as u said but i am getting this when i try to save the file

[IMG]http://i653.photobucket.com/albums/uu258/fahd47/Screenshot-1-1.png[/IMG]

---

### Post by ajgreeny on 2011-05-15
Not 

/[COLOR=Red]edit[/COLOR]/X11/xorg.conf 
but

/etc/X11/xorg.conf

You also must have opened it with ```
gksudo gedit /etc/X11/xorg.conf 
```to be able to save it

---

### Post by fahd47 on 2011-05-15
hi i corrected that and saved the file.Then restarted but all i am getting now is a test based startup screen.I tried entering my username password there and all i get is a blinking cursor with my username written in the starting.I tried entering the same command there so as to open that file again and delete what i edited but in that also i get some Gtk warning.
Plzz help me what do i do now!!

---

### Post by ajgreeny on 2011-05-16
> **fahd47 said:**
> hi i corrected that and saved the file.Then restarted but all i am getting now is a test based startup screen.I tried entering my username password there and all i get is a blinking cursor with my username written in the starting.I tried entering the same command there so as to open that file again and delete what i edited but in that also i get some Gtk warning.
Plzz help me what do i do now!!
What same command, and what GTK warning?  I think you mean you are in a command line and therefore you will not be able to use gedit.

You could use ```
sudo nano /etc/X11/xorg.conf
``` and edit the file back to what it was originally, but if the original xorg.conf that appeared from the ```
gksudo gedit /etc/X11/xorg.conf
```was empty, and you simply added the text I showed, you can safely remove the file using the command line with ```
sudo rm /etc/X11/xorg.conf
```then ```
sudo reboot
``` to hopefully get you back to a GUI, even if it is flickering.

PS:  In post 5 you appear to have tried to open or save **/etc/Xll/xorg.conf** (ie, with two lower case Ls in the X11 folder name.  Did you eventually get it to save as (now in upper case for clarity, but really all lower case except the X in X11) **/ETC/X11/XORG.CONF**

---

