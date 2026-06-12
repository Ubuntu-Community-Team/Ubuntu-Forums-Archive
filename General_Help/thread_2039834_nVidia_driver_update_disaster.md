---
title: "nVidia driver update disaster"
date: 2012-08-09
forum: General Help
---

### Post by MichaelGld on 2012-08-09
I just used the Additional Drivers selection to update my driver version from 295.20 to 302.17. I rebooted, and when I logged in my gnome panels, Cairo Dock and Unity dash are all gone! the only way I can run things is from the terminal. 

I tried compiz --replace with no changes to my desktop and the following results from the terminal:

```
michael@michael-desktop:~$ compiz --replace

(compiz:3913): Gtk-WARNING **: Theme parsing error: gtk.css:96:42: Failed to import: Error opening file: No such file or directory
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing obs options...done
Initializing move options...done
Initializing widget options...done
Initializing commands options...done
Initializing resize options...done
Initializing reflex options...done
Initializing wobbly options...done
Initializing water options...done
Initializing animation options...done
Initializing cube options...done
Initializing rotate options...done
Initializing mag options...done
Initializing animationaddon options...done
Initializing scale options...done
Initializing td options...done
Initializing cubeaddon options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Xlib:  extension "XINERAMA" missing on display ":0".
Xlib:  extension "XINERAMA" missing on display ":0".

Screen geometry changed:
   0x0x1680x1050

unity-panel-service: no process found
Xlib:  extension "XINERAMA" missing on display ":0".
Segmentation fault


```Can anyone help me get those things back from the terminal?

---

### Post by Bobhuber on 2012-08-09
> **MichaelGld said:**
> I just used the Additional Drivers selection to update my driver version from 295.20 to 302.17. I rebooted, and when I logged in my gnome panels, Cairo Dock and Unity dash are all gone! the only way I can run things is from the terminal. 

I tried compiz --replace with no changes to my desktop and the following results from the terminal:

```
michael@michael-desktop:~$ compiz --replace

(compiz:3913): Gtk-WARNING **: Theme parsing error: gtk.css:96:42: Failed to import: Error opening file: No such file or directory
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing obs options...done
Initializing move options...done
Initializing widget options...done
Initializing commands options...done
Initializing resize options...done
Initializing reflex options...done
Initializing wobbly options...done
Initializing water options...done
Initializing animation options...done
Initializing cube options...done
Initializing rotate options...done
Initializing mag options...done
Initializing animationaddon options...done
Initializing scale options...done
Initializing td options...done
Initializing cubeaddon options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Xlib:  extension "XINERAMA" missing on display ":0".
Xlib:  extension "XINERAMA" missing on display ":0".

Screen geometry changed:
   0x0x1680x1050

unity-panel-service: no process found
Xlib:  extension "XINERAMA" missing on display ":0".
Segmentation fault


```Can anyone help me get those things back from the terminal?
You need to use the 295.59  driver which seems to be causing your problem.I have had nothing but problems with the newest drivers especially using gnome3 which I now use.

---

### Post by MichaelGld on 2012-08-09
I managed to get back to 295.20 via the Additional Drivers application and everything is back where it was.  How do I install 295.59?

---

### Post by Bobhuber on 2012-08-10
> **MichaelGld said:**
> I managed to get back to 295.20 via the Additional Drivers application and everything is back where it was.  How do I install 295.59?
If the drivers you have are working for your card don't bother. The newer drivers (259.59) can be downloaded and installed from the Nvidia web site but unless your are adept at using the terminal I would stick with what you have.

---

### Post by efflandt on 2012-08-10
Isn't the 8400 an older card?  Why would you even need newer drivers.  I did use x-swat ppa for 10.10 and 11.10 while trying to resolve a failing GT 430. And that driver works fine for my newer GTX 550 Ti, but so does default nvidia-current in 12.04.

They only weird thing is that I never needed to use "nomodeset" for 10.10, but had to use nomodeset on installed 11.10 (same nvidia driver version).  For 12.04 I had to use nomodeset for live/install iso, but no parameters for installed system.

---

### Post by Frogs Hair on 2012-08-10
8 series Nvidia cards use the Nvidia Current driver which is recommended in the additional drivers jockey. I notice The old 173 is available in the jockey again which had been unavailable on my setup for a few releases. 

Nvidia has unified drivers and that is why older graphics cards often use the same driver as newer cards. This eliminates the need to develop multiple drivers. This is true for Windows also. I stick with the recommended driver because the Nvidia current with automatic updates or PPA's don't offer any noticeable difference in performance on my system. 

The security update that came via the update manager did cause problems for some users, but the 8400GS/Nvidia Current combination on the computer I'm currently using was not affected.

---

### Post by MichaelGld on 2012-08-10
> **Bobhuber said:**
> If the drivers you have are working for your card don't bother. The newer drivers (259.59) can be downloaded and installed from the Nvidia web site but unless your are adept at using the terminal I would stick with what you have.

Thanks.

---

### Post by MichaelGld on 2012-08-10
> **efflandt said:**
> Isn't the 8400 an older card?  Why would you even need newer drivers.  I did use x-swat ppa for 10.10 and 11.10 while trying to resolve a failing GT 430. And that driver works fine for my newer GTX 550 Ti, but so does default nvidia-current in 12.04.

They only weird thing is that I never needed to use "nomodeset" for 10.10, but had to use nomodeset on installed 11.10 (same nvidia driver version).  For 12.04 I had to use nomodeset for live/install iso, but no parameters for installed system.

I guess I don't "need" them, but I have felt that one should, in general, keep ones drivers up-to-date.  In this case it was the "recommended" drivers that killed my desktop.

---

