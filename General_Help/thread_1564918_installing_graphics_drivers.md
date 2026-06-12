---
title: "installing graphics drivers"
date: 2010-08-31
forum: General Help
---

### Post by manishdhr on 2010-08-31
hi i am new to ubuntu ,i am using ubuntu 10.04
i am having some display problem, so i have downloaded drivers for my graphics card but i dont know how to install it
i unpacked it but the folder doesnt contains any configure file (i typed command ./confgure}
i guess i have to move files to bin folder 
i am the only user but i am not a root user in my pc
the follder contains vinstall and vuninstall fille and some other folders
help me thanx

---

### Post by Grenage on 2010-08-31
What graphics card do you have, is there no option for proprietary drivers under Administration/hardware drivers?

---

### Post by manishdhr on 2010-08-31
via s3g unichrome pro

---

### Post by Grenage on 2010-08-31
I have no experience of that manufacturer's drivers or cards, but it's quite possible that the vinstall is an install script:

```
sudo sh vinstall
```

Is there a README file?

---

### Post by manishdhr on 2010-08-31
no readme but release note

---

### Post by manishdhr on 2010-08-31
> **Grenage said:**
> I have no experience of that manufacturer's drivers or cards, but it's quite possible that the vinstall is an install script:

```
sudo sh vinstall
```Is there a README file?

*****@ubuntu:~/Downloads/5.75.32.87a-u1004-55689$ sudo sh vinstall
[sudo] password for *****: 
install the via driver!
....../usr/bin/install: cannot stat `./bin/libGL.so.1.2.via_unichrome': No such file or directory
/usr/bin/install: cannot stat `./bin/via_unichrome_dri.so': No such file or directory
...[: 196: via_unichrome: unexpected operator
[: 196: via_unichrome: unexpected operator
...-e ...done!
-e Original X config file was saved as /etc/X11/xorg.conf.viabak
-e Caution!!
-e Need reboot the system!

---

### Post by Grenage on 2010-08-31
Hi again,

I did a quick google ([https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)), and it looks like the drivers should be installed by default.  What problems are you having?

Also, I don't like the look of that log, could you paste the contents of your xorg.conf?

```
gedit /etc/X11/xorg.conf
```

---

### Post by manishdhr on 2010-09-01
> **Grenage said:**
> Hi again,

I did a quick google ([https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)), and it looks like the drivers should be installed by default.  What problems are you having?

Also, I don't like the look of that log, could you paste the contents of your xorg.conf?

```
gedit /etc/X11/xorg.conf
```


here
Section "ServerLayout"
       Identifier    "Default Layout"
       Screen        "Default Screen"
       InputDevice    "Mouse"
       InputDevice    "Keyboard"
EndSection

Section "Files"
#     RgbPath      "/usr/local/share/X11/rgb"
       ModulePath   "/usr/lib/xorg/modules"
#     FontPath     "/usr/share/fonts/X11/misc/"
#     FontPath     "/usr/share/fonts/X11/TTF/"
#     FontPath     "/usr/share/fonts/X11/OTF"
#     FontPath     "/usr/share/fonts/X11/Type1/"
#     FontPath     "/usr/share/fonts/X11/100dpi/"
#     FontPath     "/usr/share/fonts/X11/75dpi/"
EndSection

Section "InputDevice"
       Identifier    "Keyboard"
       Driver        "kbd"
       Option        "XkbRules"    "xorg"
       Option        "XkbModel"    "pc105"
       Option        "XkbLayout"    "cn"
EndSection

Section "InputDevice"
       Identifier    "Mouse"
       Driver        "mouse"
       Option        "CorePointer"
EndSection

Section "Monitor"
       Identifier    "CRT"
       Option    "Enable"    "true"            
EndSection

Section "Monitor"
       Identifier    "LCD"
       Option     "Enable"    "false"         
EndSection    

Section "Monitor"
       Identifier    "DVI"
       Option     "Enable"    "false"
EndSection    

Section "Monitor"
       Identifier    "TV"
       Option  "Ignore"    "true"
EndSection    

Section "Monitor"
       Identifier    "HDMI"
       Option  "Ignore"    "true"
EndSection    

Section "Monitor"
       Identifier    "CRT-2"
       Option      "Ignore"    "true"
EndSection

Section "Monitor"
       Identifier    "LCD-2"
       Option      "Ignore"    "true"
EndSection

Section "Monitor"
       Identifier    "DVI-2"
       Option      "Ignore"    "true"
EndSection

Section "Monitor"
       Identifier    "TV-2"
       Option      "Ignore"    "true"
EndSection

Section "Device"
    Driver     "via"
    VendorName      "VIA Tech"
    BoardName       "via"
    Identifier    "Configured Video Device"
    Option        "MigrationHeuristic" "greedy"
EndSection

Section "Screen"
       DefaultDepth 24
       SubSection "Display"
#             Virtual 2000 2000 
              Depth  24
       EndSubSection
       Identifier    "Default Screen"
       Device        "Configured Video Device"
EndSection

Section "Module"
      Load  "glx"
      Load  "dri"
      Load  "extmod"
EndSection

Section "DRI"
       Group 0
       Mode 0666
EndSection

Section "Extensions"
    Option    "Composite"            "Enable"
EndSection

---

### Post by manishdhr on 2010-09-01
thanx for the link you gave , i am following it

---

### Post by Grenage on 2010-09-01
Ok dokes, let us know how you get on.

---

### Post by manishdhr on 2010-09-01
thanx bro problem is solved , i downloaded updates and its working properly, thanx for giving your precious time and yeah also i m downloading drivers according to the link you gave me, Thanx again [Grenage]("http://ubuntuforums.org/member.php?u=263074") and good day

---

### Post by Grenage on 2010-09-01
Awesome, glad to hear it's working; take care.

---

### Post by manishdhr on 2010-09-01
you too

---

