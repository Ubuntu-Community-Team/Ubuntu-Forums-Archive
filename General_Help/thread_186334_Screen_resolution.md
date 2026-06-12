---
title: "Screen resolution"
date: 2006-06-01
forum: General Help
---

### Post by hyphen4 on 2006-06-01
How do I change my screen resolution?

---

### Post by JSchwage on 2006-06-01
System > Preferences > Screen Resolution

Seriously, is it that hard to find? ;)

---

### Post by kevlar16 on 2006-06-01
Ubuntu 6.06 does not allow screen resolution higher than 640 x 480. This has been the case every time when I tried the beta and RC releases in the last several months. And yes, I did try 'System > Preferences > Screen Resolution' :)  I even played with the xorg.conf file. Does anyone know how to fix this? My videocard is ATI Radeon 8500.

---

### Post by blakamin on 2006-06-01
What driver is it running??:???:

---

### Post by confused57 on 2006-06-01
[QUOTE=kevlar16]Ubuntu 6.06 does not allow screen resolution higher than 640 x 480. This has been the case every time when I tried the beta and RC releases in the last several months. And yes, I did try 'System > Preferences > Screen Resolution' :)  I even played with the xorg.conf file. Does anyone know how to fix this? My videocard is ATI Radeon 8500.[/QUOTE]

You say you edited the xorg.conf file, I assume you mean 
"sudo nano /etc/X11/xorg.conf".

Did you try:
```
sudo dpkg-reconfigure xserver-xorg
```

You should be able to set what resolutions you want to select by using this.

---

### Post by crrieger on 2006-06-01
Same problem here.  I have a Radeon 9200 and am also stuck at 640x480 @ 60Hz.  I've tried "sudo nano /etc/X11/xorg.conf" and "sudo dpkg-reconfigure xserver-xorg" with no success.  I've also tried updating the ATI drivers through EasyUbuntu with no luck after it finished.  I didn't have any problems at all under Breezy, so this one has me thrown a bit.

---

### Post by joshrobinson on 2006-06-01
[QUOTE=crrieger]Same problem here.  I have a Radeon 9200 and am also stuck at 640x480 @ 60Hz.  I've tried "sudo nano /etc/X11/xorg.conf" and "sudo dpkg-reconfigure xserver-xorg" with no success.  I've also tried updating the ATI drivers through EasyUbuntu with no luck after it finished.  I didn't have any problems at all under Breezy, so this one has me thrown a bit.[/QUOTE]


i have a radeon 9250 and it picked my resolution fine.. have you put your resolution into xorg.conf? like "1024x768" after the 24 bit depth entry?

---

### Post by crrieger on 2006-06-01
Go figure, I did another reboot after all that and it gave me access to the missing resolutions.  I'll still have to add a few larger ones, but at least I can see a complete screen now.

---

### Post by joshrobinson on 2006-06-01
[QUOTE=crrieger]Go figure, I did another reboot after all that and it gave me access to the missing resolutions.  I'll still have to add a few larger ones, but at least I can see a complete screen now.[/QUOTE]

yeah i guess it didnt read your settings for some reason, it takes a reboot to re-read the xorg.conf.. im not sure if cntrl+alt+backspace re-reads the xorg file.. but it should.. havent really tried

---

### Post by davester on 2007-07-02
I just installed xubuntu and experiencing same resolution problem as seen in postings.  I have done the sudo dpkg-reconfigure xserver-xorg command.  I input my password , enter, the terminal screen just remains blank - heellp

---

### Post by MimeyNaomi on 2008-06-10
Tried dpkg-reconfigure xserver-xorg, and it didn't give me an option to change the screen resolution, just a lot of keyboard layout options.  So I opened xorg.conf with gedit, and I can't see where to place a new screen resolution; there is no list of resolutions, all I get is:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by Wiebelhaus on 2008-06-10
Same issue here as above.

---

