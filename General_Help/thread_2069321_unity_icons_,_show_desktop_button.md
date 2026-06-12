---
title: "unity icons , show desktop button"
date: 2012-10-10
forum: General Help
---

### Post by mIXpRo on 2012-10-10
hi,

in ubuntu 12.10 beta 2 ,how to :

1- add custom icons to unity (and don't say run the app and lock the icon to the dock cause it's not working)

2- add show desktop button 

3- install myunity


thnx for all the help.

another thing :

scrolling with middle mouse button is reversed in chrome .
but normal in nautilus , what's this ??!?!? first time ever .

---

### Post by GreatDanton on 2012-10-10
1. To add Icons I usually just drag and drop icons from the dash.

3. My Unity is not available for the latest release so you will have to wait, or stick with 12.04. If you want to customize it a little bit you can try via:  CompizConfig Settings Manager/ Ubuntu Unity plugin

Hope this helps.

---

### Post by MG&amp;TL on 2012-10-10
2 - Install CCSM, look under 'experimental' in the Unity tab, tick 'show desktop icon'.

---

### Post by mIXpRo on 2012-10-10
there is no show desktop in ccsm for ubuntu 12.10 beta 2

---

### Post by GreatDanton on 2012-10-10
Maybe this is what you are looking for?

---

### Post by MG&amp;TL on 2012-10-10
> **GreatDanton said:**
> Maybe this is what you are looking for?

Whoah....okay, I need to actually be running a beta when I check these threads. The last time I checked it wasn't like that...sorry guys! Will check in morning.

---

### Post by wojox on 2012-10-10
> **MG&TL said:**
> The last time I checked it wasn't like that...sorry guys! Will check in morning.

It still isn't like that.

---

### Post by mIXpRo on 2012-10-10
> **GreatDanton said:**
> Maybe this is what you are looking for?

i have that but it doesn't do anything ,
besides , as i remember , it says show desktop icon ,
not disable...

---

### Post by mIXpRo on 2012-10-11
so basically no solution for any of my issues ?!?!?!?

is it all because of the beta thing ???

---

### Post by grahammechanical on 2012-10-11
What issues? You do not say what the issues are. You just say


> 2- add show desktop button 

Now it turns out that you want to disable it.

What do you mean by "show desktop button?" I do not have an icon on my 12.10 Launcher that will let me bring the desktop to the fore. It is already disabled.

The "Disable show desktop in the switcher" tick box seems to do nothing because the show desktop icon is in the switcher, which is activated by Alt + tab. Tick the box to Disable show desktop in the switcher" and the desktop icon will be removed from the switcher.

Regards.

---

### Post by mIXpRo on 2012-10-11
my "issues" (not really issues but features that i want) are  3 listed in the beginning ,and one real issue is the mouse related one (the 4th), and show desktop button , its a button on unity dash (not switcher) along side the trash and .... that when clicking on it shows the desktop (similar to the switcher show desktop ).

---

### Post by wojox on 2012-10-11
Ctrl+Alt+Tab will let you show the desktop.

---

### Post by GreatDanton on 2012-10-11
You can press just alt+tab and it will be the same result.

---

### Post by evilsoup on 2012-10-11
CTRL+WINKEY+D shows the desktop.

---

### Post by mIXpRo on 2012-10-11
thanks this works , 

but what about  :

1 - custom icons , i.e i have downloaded blender3d 2.64 and it comes in a directory , what i want is to be able to drag the binary blender file (or a link to it) to the unity dash so i can access it easly (and it's not just blender3D theres a lot like that which i have).

2 - and the mouse its driving me cray , its weird , scrolling is reversed inside chrome and other applications , and other it's regular .
i have updated to the latest packages .

---

### Post by evilsoup on 2012-10-11
For putting custom icons in the dash/launcher, you have to [make a .desktop file]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") and put it in ~/.local/share/applications/

Here's an example .desktop I created:

```
[Desktop Entry]
Type=Application
Name=Celtx
Exec=celtx
Comment=Write movie and television scripts
Categories=Applications
StartupNotify=true
Icon=/home/evilsoup/.celtx/celtx/icons/default48.png

```

For the 'Exec=' line, normally you'd have to include the /absolute/path/to/executable, but I have a symlink to the celtx executable in my $PATH. You have to mark it as executable (right click --> PROPERTIES --> PERMISSIONS tab --> click 'Allow executing file as program'), and you may need to log out & in again for the dash to detect it.

I can't say for your other problem, but you might be better off starting a new thread for it.

---

### Post by DogMatix on 2012-10-11
You could check out the utility 'Unsettings' I believe it has a show desktop icon option and I have found this article >> [link]("http://www.noobslab.com/2012/09/install-unsettings-007-in-ubuntu.html")<< that states it works in 12.10, although I have never used 'Unsettings' myself. Maybe someone can confirm this for you?

---

### Post by mIXpRo on 2012-10-11
> **evilsoup said:**
> For putting custom icons in the dash/launcher, you have to [make a .desktop file]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") and put it in ~/.local/share/applications/

Here's an example .desktop I created:

```
[Desktop Entry]
Type=Application
Name=Celtx
Exec=celtx
Comment=Write movie and television scripts
Categories=Applications
StartupNotify=true
Icon=/home/evilsoup/.celtx/celtx/icons/default48.png

```

For the 'Exec=' line, normally you'd have to include the /absolute/path/to/executable, but I have a symlink to the celtx executable in my $PATH. You have to mark it as executable (right click --> PROPERTIES --> PERMISSIONS tab --> click 'Allow executing file as program'), and you may need to log out & in again for the dash to detect it.

I can't say for your other problem, but you might be better off starting a new thread for it.


thanks a lot , it worked .

---

