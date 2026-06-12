---
title: "Help needed with xorg.conf"
date: 2010-03-30
forum: General Help
---

### Post by spikeyspc on 2010-03-30
Hi everyone,
 
I am new to Ubuntu so please excuse me if I sound retarted :p. 
 
I have built a new computer with Ubuntu 9.10. I have an Nvidia Quadro FX370LP with dual 24" Asus monitors. At each boot, only one monitor would show up. I chould then go into the Nvidia control setting and change it to show both screens. Upon saving I got this error Message.
 
Failed to parse existing X config file '/etc/X11/xorg.conf'!

I tried Bangeko's suggestion of...
1) open a terminal
2) sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2) sudo touch /etc/X11/xorg.conf 
3) sudo nvidia-settings
4) hit "save configuration"
 
I thought it worked but after rebooting, I got the CLI logon screen. After logging on, I tried to do startx and it comes back with no such file or directory, unable to connect to xserver. I have also tried to change directories to /etc/x11 then open the xorg.conf to see if I can modify it but it doesn't allow me past the /etc/, the x11 folder seems to be corrupt.
 
Is there a way to restore the default settings without wiping off Ubuntu? kind of like system restore on windows? I already have programs installed and files on this which I don't want lost and redoing if possible.
 
Note: When I first got the PC, I tried to install it followed by doing the updates. After which the computer would go to the white ubuntu symbol and get stuck. The only way I knew around this was to reinstall ubuntu and NOT install the updates. Not sure if this helps determine whats wrong.
 
Thanks for all your help.:D

---

### Post by spikeyspc on 2010-03-30
I was speaking with someone that uses a different flavor of linux and they were saying that I could rerun the script that installs the X files. He doesn't know where or exactly how to do that. Do any of you know how to do that and if that would help in my situtation??? Thanks.

---

### Post by patchwork on 2010-03-30
Remember that files and directories are case-sensitive (/etc/X11, not /etc/x11)
Reinstalling X may not be necessary.  First, let's see exactly what is going on.

Please post the output of ```
cat /etc/X11/xorg.conf
``` and ```
cat /var/log/Xorg.0.log
```

---

### Post by nana336 on 2010-03-30
I have the same exact problem problem. After changing screen resolution to Auto or 1900X1200, I can't save the Settings. Its giving same above error. I tried all the options from 3/4 forums. till now no resolution from any. Mine is also NVDIA ...

Here are contents of 
[COLOR=Blue]cat /etc/X11/xorg.conf[/COLOR]

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

[COLOR=Blue]cat /var/log/Xorg.0.log[/COLOR]
log file is big, so I'm attaching it..

[COLOR=Red]Any help from Ubuntu Guru's will be a great fro lot of people..[/COLOR]

---

### Post by patchwork on 2010-03-31
nana, just to be clear, the error you're getting is the failed to parse message?  What steps have you already taken (i.e using gksu nvidia-settings, etc)?

The last case scenario would be to explicitly call the preffered mode manually in the xorg.conf.   This typically isn't necessary (especially since your monitor's information is being recognized by the X server).

---

### Post by spikeyspc on 2010-03-31
> **patchwork said:**
> Remember that files and directories are case-sensitive (/etc/X11, not /etc/x11)
Reinstalling X may not be necessary. First, let's see exactly what is going on.
 
Please post the output of ```
cat /etc/X11/xorg.conf
``` and ```
cat /var/log/Xorg.0.log
```
 
Sorry about typing /etc/x11, I meant to type in /etc/X11.
 
After typing in cat /etc/X11/xorg.conf, I can see the information that Nvidia put into the xorg.conf file. I can only see the bottom portion and don't know how to scroll up to see if the original information is left in it. but here is what I see.
 
user-desktop:0.0/AllowFlipping=1
user-desktop:0.0/FSAAAppControlled=1
user-desktop:0.0/LogAnisoAppControlled=1
user-desktop:0.0/OpenGLImageSettings=1
user-desktop:0.0/FSAAAppEnhanced=0
user-desktop:0.0/RedBrightness=0.000000
user-desktop:0.0/GreenBrightness=0.000000
user-desktop:0.0/BlueContrast=0.000000
user-desktop:0.0/RedGamma=1.000000
user-desktop:0.0/GreenGamma=1.000000
user-desktop:0.0/BlueGamma=1.000000
user-desktop:0.0/DigitalVibrance[DFP-0]=0
user-desktop:0.0/DigitalVibrance[DFP-1]=0
user-desktop:0.0/GPUScaling[DFP-0]=131073
user-desktop:0.0/GPUScaling[DFP-1]=131073
user-desktop:0.0/XVideoTextureBrigness=0
user-desktop:0.0/XVideoTextureContrast=0
user-desktop:0.0/XVideoTextureHue=0
user-desktop:0.0/XVideoTextureSaturation=0
user-desktop:0.0/XVideoTextureSyncToVBlank=1
user-desktop:0.0/XVideoSyncToDisplay=65536
 
 
 
cat /var/log/Xorg.0.log
Fatal server error:
no screens found

---

### Post by nana336 on 2010-03-31
After I change Screen NVDIA Settigns to Auto or 1900X1200 on my HP 24" Monitor, I'm getting the same error - Failed to p**** existing X config file '/etc/X11/xorg.conf'! 

I tried to manually change the settings as per previous forums..its not giving me access to change the .conf file. chmod on this file is also not working. Every time I reboot, I am changing screen settings manually - which is really annoying.

ANY HELP ON THIS MATTER IS HELPFUL OF LOT OF PEOPLE. No thread on this issue is CLOSED.

patchwork, can you please explain steps on :
The last case scenario would be to explicitly call the preffered mode manually in the xorg.conf.

---

### Post by realzippy on 2010-03-31
None of you guys manually have run nvidia-xconfig???

1.Delete existing xorg.conf,no need to backup.

```
sudo rm /etc/X11/xorg.conf
```

2.Make new xorg.conf

```
sudo nvidia-xconfig
```

3.Enjoy

```
gksudo nvidia-settings
```

Edit:
If chosen resolution not persists after reboot,run:

**rm /home/yourusername/.config/monitors.xml**

*replace yourusername with your users name...*


Edit2:
Only run those (rm) commands if you have a working NVIDIA-graphics driver installed...

---

### Post by sdowney717 on 2010-03-31
When I do this, I select the preview mode.
select all the text of the new xorg. 
Copy it
then open the existing xorg with root
paste 
save
reboot

I also will always get cant save the file using nvidia config program

---

### Post by realzippy on 2010-03-31
> **sdowney717 said:**
> When I do this, I select the preview mode.
select all the text of the new xorg. 
Copy it
then open the existing xorg with root
paste 
save
reboot

I also will always get cant save the file using nvidia config program


...the trick is to delete the existing xorg.conf first.

---

### Post by spikeyspc on 2010-03-31
> **realzippy said:**
> None of you guys manually have run nvidia-xconfig???
 
1.Delete existing xorg.conf,no need to backup.
 
```
sudo rm /etc/X11/xorg.conf
```
 
2.Make new xorg.conf
 
```
sudo nvidia-xconfig
```
 
3.Enjoy
 
```
gksudo nvidia-settings
```
 
Edit:
If chosen resolution not persists after reboot,run:
 
**rm /home/yourusername/.config/monitors.xml**
 
*replace yourusername with your users name...*
 
 
Edit2:
Only run those (rm) commands if you have a working NVIDIA-graphics driver installed...
 
 
A MILLION THANKS!!!:D
This worked perfectly. Ran Commands, Rebooted system, and I'm back. Woot!
I would also like to thank everyone that took the time to help with this problem as well.

---

### Post by nana336 on 2010-03-31
realzippy your the MAN... IT WORKED FOR ME...

As you said, Deletinf xord is key. Here are the steps that I did
1. Delete xorg.xonf file :cmd> sudo rm /etc/X11/xorg.conf
2. Make new xorg.conf file :cmd> sudo nvidia-xconfig
3. Also run NVDIA Settings :cmd> gksudo nvidia-settings
4. Incase, I gave full permissions on xorg.conf file :cmd> chmod 777 xorg.*
5. Delete moniors xml and let the new settings takes place. Without this, It didn't work for me after reboot. :cmd> rm /home/yourusername/.config/monitors.xml
6. Reboot
7. NJOY

---

### Post by nana336 on 2010-03-31
Realcrazy or any one ... Do you know why my email, screen, speaker, shutdown icons came into top middle of the screen and data and time are now on the top right most corner after this xorg changes ???

---

### Post by realzippy on 2010-03-31
> **nana336 said:**
> Realcrazy or any one ... Do you know why my email, screen, speaker, shutdown icons came into top middle of the screen and data and time are now on the top right most corner after this xorg changes ???

No.But you can move them.One is the so called "notification area".Right click it for options,e.g. "move" (unlock before).Data and time same...

Have fun.

---

### Post by nana336 on 2010-03-31
RealZippy thanks for your help...I can only move ShutDown icon to the right most. All the other icons like Email, Screen, Speeker - Still satys in the middle. No right click or anything is working on these icons...

Not a big deal but just thought you or someone know the solution.

Thanks a bunch.

---

### Post by nana336 on 2010-03-31
Realzippy I can move all the icons with couple of reboots, right click unclick lock to Pandel and Move the icons...

Overall my current Display Screen issues are resolved...Thanks to RealZippy and others...

---

