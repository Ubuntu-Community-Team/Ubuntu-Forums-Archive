---
title: "Help configuring LightDM?"
date: 2011-11-06
forum: General Help
---

### Post by DaimyoKirby on 2011-11-06
Hi there.
I've seen pictures of the login screen that look like this: [IMG]http://i.imgur.com/Ehvnel.jpg[/IMG]
Is this the login screen just for Ubuntu 11.10, or is there a way for me to get it on Xubuntu 11.10?

Mine currently looks a little like this(except with the greybird background):[IMG]http://i.imgur.com/Iogwtl.png[/IMG]

---

### Post by raja.genupula on 2011-11-06
Hi man install gdm

```
sudo apt-get install gdm
```

while doing installation its gonna ask you which one is default  select gdm

and restart your system ,

---

### Post by samigina on 2011-11-07
He wants lightdm (the default for all the *buntus), so install GDM is not the answer.

FOr what I see, theres some problem with the lightdm theme.

Try reinstalling "unity-greeter" and "lightdm-gtk-greeter"

---

### Post by Elfy on 2011-11-07
I was in the #xubuntu channel - this came up there.

Apparently - > <charlie-tca> so to use the Ubuntu greeter requires installing unity-greeter 

and 

<madnick> sudo apt-get install gnome-settings-daemon

```
sudo apt-get install unity-greeter gnome-settings-daemon
```

Make sure that unity-greeter installed a .desktop file in xgreeters

```
ls /usr/share/xgreeters/
```

```
sudo nano -B /etc/lightdm/lightdm.conf
```
Edit lightdm.conf so that 

> user-session=xubuntu
greeter-session=lightdm-gtk-greeter

reads
> user-session=xubuntu
greeter-session=unity-greeter

To change the image used in the background edit unity-greeter.conf
```
sudo nano -B /etc/lightdm/unity-greeter.conf
```
> 
#
# background = Background file to use, either an image path or a color (e.g. #772953)
# logo = Logo file to use
# theme-name = GTK+ theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
#
[greeter]
[COLOR="Red"]background=/usr/share/backgrounds/warty-final-ubuntu.png[/COLOR]
logo=/usr/share/unity-greeter/logo.png
theme-name=Ambiance
icon-theme-name=ubuntu-mono-dark
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=hintslight
xft-rgba=rgb

Tested on 11.10

---

### Post by DaimyoKirby on 2011-11-07
Ok, thanks so much! That worked like a charm.

Going along with the topic of configuring LightDM (and I supposed now, the unity greeter), is there a way to configure who shows up at login?
For example, disable the guest account so it won't show up, only my account will, etc.

---

### Post by Elfy on 2011-11-08
To remove guest user - edit lightdm.conf again, add this

```
allow-guest=false
```

---

### Post by DaimyoKirby on 2011-11-08
Ok, that worked great. Thanks!
Would there also be a way to hide my account, and require manual typing of account username, such as:
[IMG]http://i.imgur.com/TSbOtl.png[/IMG]
Is there a way to achieve this? (Sorry, probably should have asked this first)


Also, Is there a way to change the new loading screens background:
(like this, but with the bar sliding back and forth, and saying "Xubuntu" instead of "Ubuntu")
[IMG]http://techspyre.com/wp-content/uploads/2011/10/Boot-Screen.jpg[/IMG]

---

### Post by Elfy on 2011-11-09
Sorry - no idea ... probably is, but someone else might know. If not try the irc channel.

That said there is a user.conf in /etc/lightdm - the line minimum-uid=500 could be edited to over 1000 perhaps and see if that works - if it doesn't recovery mode and put it back  - that is a guess though and I've not a vbox install to play in.

---

### Post by DaimyoKirby on 2011-11-10
Ok, thanks so much. I'll try in the irc.

---

### Post by Elfy on 2011-11-11
IF you do get it sorted can you come back and post how. Good luck.

---

### Post by mateosalta on 2012-02-20
I think that last graphic was the splash screen which can be changed in >Applications>Settings>Settings Manager>Session and Startup>Splash

Hmmm, although there is a new extra thing that loads before that? Let me know if that is the one you are talking about.

---

### Post by DaimyoKirby on 2012-02-23
You're talking about the screen that shows up after the BIOS screen, that indicates/shows that the OS is loading, right?

---

### Post by 0800peter on 2013-05-06
Just to leave a quick entry on my sucessfull atempt after ended up with a black screen after booting xubuntu to recover
ctrl-alt-f3 for terminal,
username, passwort 

sudo cp /etc/lightdm/lightdm.conf.cedarview-drm /etc/lightdm/lightdm.conf 

passwort 
sudo reboot

---

### Post by oldos2er on 2013-05-06
Old thread closed.

---

