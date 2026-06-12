---
title: "Compiz on KDE 4.3"
date: 2009-08-07
forum: General Help
---

### Post by wersdaluv on 2009-08-07
Many prefer KWin over Compiz for KDE4 but no matter what they say, Compiz is just a lot smoother on my system. It may have something to do with my intel X3100 graphics, Compiz may just really be faster, or both.

I want Compiz on my KDE 4.3 desktop but there are integration problems. I already installed compiz-kde and that gave me the choice in fusion-icon to use the KDE window decorator while on Compiz but choosing that option gave me no window border at all. It seems to be a known bug in Compiz 0.8.2. I've been looking for an elegant emerald or metacity theme that would fit Oxygen well but I haven't found one so far. Any suggestion?

I also noticed that the desktop pager plasmoid doesn't work properly with Compiz. Any fix for that?

Do you have suggestions for using Compiz on KDE 4.3?

---

### Post by Universal344 on 2009-08-07
As for the broken pager I don't know if that can be fixed at all.  When I tried to get Compiz to work with KDE it broke my virtual desktops all together.

---

### Post by olejon on 2009-08-10
> **Universal344 said:**
> As for the broken pager I don't know if that can be fixed at all.  When I tried to get Compiz to work with KDE it broke my virtual desktops all together.

I managed to get Compiz working fine in KDE 4.3.

First install compiz-kde, emerald and compizconfig-settings-mananger, then edit /usr/bin/compiz-decorator and set:

```
USE_EMERALD="yes"
```

Now go in CompizConfig Settings Manger in the menu > General options > Desktop size and set Horizontal to 4. Remove the pager from the panel.

Then go to System Settings (in KDE) > Default applications > Window manager

Choose "Use a different WM" and choose "Compiz", NOT "Compiz Custom".

Now go in System Settings > Desktop

Now add the pager again.

Now just download an oxygen theme for Emerald (kde-look.org), and choose it in Emerald Theme Manager in the menu, and voila, you have Compiz looking just as KWin.

Restart or log out and in again to get a fully working Compiz with the plasma-desktop.

---

### Post by wersdaluv on 2009-08-10
It didn't work for me :( I may not have done it properly

You mentioned going to System Settings > Desktop. What do I do there? hehe

---

### Post by wersdaluv on 2009-08-11
I got it! I should keep the System Settings > Desktop window open while adding the pager! Cool man! Very smart! lol

---

### Post by Barafu Albino Cheetah on 2009-08-11
Foer compiz to work on KDE there is a package called compiz-wrapper

---

### Post by t.rei on 2009-08-14
I would love to have the kde4-window-decorator working, but for me, it shows no borders at all currently. So I am stuck using gtk-window-decorator or emerald for now. Both not looking really well with oxygen.
 
currently my best combo is: qtcurve and gtk-window-decorator with the eGTK theme.

---

### Post by wersdaluv on 2009-08-15
I noticed that Compiz edges are messed up on KDE 4.3. I have to reset my edge settings for them to work each session.

---

### Post by Tipped OuT on 2009-08-15
UNINSTALL EVERYTHING FIRST THEN....

1. Go to System Settings.
2. Go to Add/Remove Software.
3. Search for "Compiz".
4. Install the first choice in the results.
5. Search for "CompizConfig".
6. Install the first choice in the results.
7. Go to System Settings.
8. Go to Default Applications, and under "Windows Manager" select "Compiz"
9. Apply the settings (it will now switch to Compiz) and restart your computer.
10. Welcome to Compiz Fusion.


You can then configure Compiz Fusion to the way you like it, with CompizConfigSettingsManager, which you can find in start menu, under Applications< Settings.

---

### Post by KiRiLoS on 2009-08-17
Is there a way to change the windows decorator other than emerald+theme?I would be happy if i was just able to select Dust theme!
Under Gnome i would just go to appearance and choose,in KDE i have no idea how i can choose which Gtk theme i want!

---

### Post by t.rei on 2009-08-31
KiRiLoS - you can just run 
```
gtk-window-decorator --replace
```
to switch to a gnome-theme-using window decorator.

(I still have no borders when running kde4-window-decorator :( )

---

### Post by Chronon on 2009-08-31
Compiz Fusion Icon gives a convenient way to change window decorator, switch or reload desktop manager or launch CCSM.

KDE4 window decorator works fine on my system.

---

### Post by wersdaluv on 2009-08-31
> **t.rei said:**
> KiRiLoS - you can just run 
```
gtk-window-decorator --replace
```
to switch to a gnome-theme-using window decorator.

(I still have no borders when running kde4-window-decorator :( )
They say that it's a known bug in the current version of Compiz

---

### Post by wersdaluv on 2009-08-31
> **Chronon said:**
> Compiz Fusion Icon gives a convenient way to change window decorator, switch or reload desktop manager or launch CCSM.

KDE4 window decorator works fine on my system.
What distro and which version?

---

### Post by WindPower on 2009-09-06
+1 for this. No borders at all when using Compiz! :( Unless I switch to another window decoration like Plastik or Modern instead of Oxygen.

---

### Post by Paki on 2009-10-08
> **wersdaluv said:**
> I noticed that Compiz edges are messed up on KDE 4.3. I have to reset my edge settings for them to work each session.

I have this problem as well. I install Compiz, use the Compiz settings to assign screen edges to functions, and it works until I log out of the session or reboot the system. Although the Compiz settings still shows the configuration that I requested, the functions assigned do not activate when I move the mouse cursor to the screen edges. If I disable the assigned function and then turn it back on, the screen edges work until the next time that I reboot.

Any ideas?

Thanks for any help!

---

### Post by WindPower on 2009-10-08
Dunno about the screen edges (they seem to work for me), but the window decorations can be fixed by installing [Nitrogen](http://www.kde-look.org/content/show.php/Nitrogen?content=99551). It looks just like the Oxygen/Ozone window borders, works with KDE color schemes (unlike Emerald themes), and works with KDE 4.3.x with Compiz.

---

### Post by Chronon on 2009-10-08
> **wersdaluv said:**
> What distro and which version?

Sorry about the delay.  My Compiz is referred to as 1:0.8.2-0ubuntu8.1 in my package manager.  I am currently using KDE 4.3.2 but at that time was using 4.2.x, I believe.  I am using Kubuntu 9.04.  I still don't have problems with my KDE window decorations.  I can freely swap back and forth between GTK and KDE window decorators with no apparent ill effects.

---

### Post by wersdaluv on 2009-10-08
> **Chronon said:**
> Sorry about the delay.  My Compiz is referred to as 1:0.8.2-0ubuntu8.1 in my package manager.  I am currently using KDE 4.3.2 but at that time was using 4.2.x, I believe.  I am using Kubuntu 9.04.  I still don't have problems with my KDE window decorations.  I can freely swap back and forth between GTK and KDE window decorators with no apparent ill effects.
Cool! It's a known bug for Ubuntu's Compiz version. Are you using the Oxygen or Ozone kwin theme? I found out that some older kwin themes work properly but not Oxygen or Ozone.

---

