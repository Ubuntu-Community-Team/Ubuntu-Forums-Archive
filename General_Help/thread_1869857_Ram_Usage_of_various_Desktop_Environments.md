---
title: "Ram Usage of various Desktop Environments"
date: 2011-10-26
forum: General Help
---

### Post by pepsifx357 on 2011-10-26
RAM usage comparison in Ubuntu 11.10 between various Desktop Environments.  This was done in a a virtual machine using Virtual box with a stock Ubuntu 11.10.  All of the desktop environments were all installed on the same system, which may have caused undesired results, as certain DEs might have startup programs running on other DEs.  Each session was started after each reboot, a single terminal window was opened and ram usage checked using: ```
free -m
```
 
In Megabytes

KDE via Kubuntu   = 325
(Default) Unity	  = 270
XFCE via Xubuntu  = 213
Gnome Classic     = 191
Gnome             = 188
LDXE via Lubuntu  = 148
Openbox           = 136
FVWM-Crystal      = 85
Fluxbox           = 75
FVWM		  = 66


FVWM is the winner in this little demonstration using only 66MB of ram. with fluxbox following closely behind with 75MB.  Fluxbox is my favorite lightweight. :)

As you can see, Unity is not a very lightweight DE, as many people have said.  KDE is still the top dog at hogging your ram at 325MB, with good reason.  It looks amazing!

```
sudo apt-get install kubuntu-desktop
```
Very nice looking and full featured.
```
sudo apt-get install xubuntu-desktop
```
A good desktop for everyday computing.  It doesn't look bad either.
```
sudo apt-get install gnome-desktop
```
I prefer this over unity.
Gnome classic comes with this package.
```
sudo apt-get install lubuntu-desktop
```
Much like xubuntu, good everyday DE.
```
sudo apt-get install openbox
```
When you load this up, you get a greyish background.  That's it.

I highly suggest something like lxpanel so that you can easily multitask and get to your software using shortcuts.
```
sudo apt-get install fvwm-crystal
```
A little more features than the standard fvwm. Looks a little better as well.
```
sudo apt-get install fluxbox eterm
```
if you install fluxbox without eterm, you will be greeted with a popup that will tell you that you need a desktop wallpaper rendering software.  It suggests eterm.  You can ignore this and still use fluxbox with a black background.
```
sudo apt-get install fvwm
```
I don't have much experience with this one.  It's ugly, but simple.

What would be cool is if you guys could do the same thing and post your results.  I imagine there would be differences.

---

### Post by xtremo on 2011-10-26
Surprised to see Xubuntu using more than Gnome Classic!

---

### Post by pepsifx357 on 2011-10-26
> **xtremo said:**
> Surprised to see Xubuntu using more than Gnome Classic!

Yeah, some of those results kinda surprised me.  I was hoping that maybe someone else could post a lower ram usage.

---

