---
title: "vmware fullscreen + XGL/Compiz/fglrx = not working"
date: 2006-06-06
forum: General Help
---

### Post by zitch on 2006-06-06
I've installed XGL/Compiz on my laptop sporting a ATI Mobility Radeon 9600 using ATI's drivers and got it running rather smoothly and stably to use as my normal workstation.  I have then installed vmware server so I can run Windows XP Pro when I need to and setup testing and development virtual servers as I need them, and I have gotten that running quite well (To the point where I can run Map software in Windows XP that's connected to a USB GPS receiver very well in the car!). 

The only problem I'm having is trying to run the VMWare console fullscreen.  When I attempt to do so, I get the following error:

```
Unable to find an appropriate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.

Failed to switch to full screen  mode.
```

I don't have XF86Config as a file, and I have a feeling this might be related to using display :1 instead of :0 to work around the bug in the ATI driver, but I don't have a clue as to how to fix this full screen switch problem.

It's not particulary urgent, but any suggestions?

---

### Post by antiram on 2006-06-06
don't set "unredirect fullscreen window" in main window of gset-compiz
set "autofit window", "autofit guest", "don't resize" in vmware->preferences->display

---

### Post by zitch on 2006-06-06
Well, that by itself didn't work (I couldn't find the "don't resize" option under Edit->Preferences->Display in the VMWare console), but it did spark an idea.

I ended up doing gedit ~/.vmware/preferences and modified the line that said pref.autoFitFullScreen = "fitHostToGuest" to pref.autoFitFullScreen = "fitGuestToHost" and that did the trick! 

Thank you for your help!

Edit: Well, that does work, but apparently VMWare will constantly rewrite that file and set it back to "fitHostToGuest" and I'll get the same error later anyways.  I'll have to ask VMWare about this...

---

### Post by noelferg on 2006-06-07
Am also having same problem - can't run in Full Screen mode

Any help appreciated

---

### Post by zitch on 2006-06-07
Well, it looked like I had a brain fart yesterday...

Basically, the guest is running in a resolution that's not supported by the Host server, so it complains if you try to run fullscreen then.  If you turn off the Autofit Guest option, set the guest to a supported resolution (Maybe in the list under Preferences->Screen Resolution), the fullscreen option should now work.  For example, I had set my guest OS to run at 1440x900, then I was able to use the fullscreen option.

---

### Post by ehula on 2006-06-07
[QUOTE=zitch]Well, it looked like I had a brain fart yesterday...

Basically, the guest is running in a resolution that's not supported by the Host server, so it complains if you try to run fullscreen then.  If you turn off the Autofit Guest option, set the guest to a supported resolution (Maybe in the list under Preferences->Screen Resolution), the fullscreen option should now work.  For example, I had set my guest OS to run at 1440x900, then I was able to use the fullscreen option.[/QUOTE]

Did you get this working, or are you just supposing? My guest is set to a supported resolution in /etc/X11/xorg.conf, but I still get the error:

"Unable to query the valid mode lines from your X server; will not try to change host resolution when entering fullscreen mode."

The only way I am able to get this working is if I use the same resolution in the guest as the host. Before xgl, I was able to use any guest resolution, and when I switched to full screen, the host changed resolution to match the guest.

---

### Post by zitch on 2006-06-07
Now I don't know.  It now works for any guest resolution, even for non-standard resolution, but my host will not change the resolution to match the guest, so for a 640x480 guest, it'll be centered on a giant 1440x900 screen (The native resolution for this laptop's screen)... :)

Not that this is a problem for me though because I wanted to have Windows XP available at 1440x900 in fullscreen mode, and it now works for me.  

Apparently, you have to have the vmware console closed before you can edit the ~/.vmware/preferences file, cause now the pref.autoFitFullScreen line is set to "fitGuestToHost" and stays that way like I want it to.  Maybe poking around in that file might reveal something?

---

### Post by ehula on 2006-06-07
So, has anyone who is using xgl been successful in getting Ubuntu to change it's resolution to match the guest OS when switching to fullscreen? If so, which video card/driver are you using?

---

### Post by ehula on 2006-06-28
[QUOTE=ehula]So, has anyone who is using xgl been successful in getting Ubuntu to change it's resolution to match the guest OS when switching to fullscreen? If so, which video card/driver are you using?[/QUOTE]
Bump

---

### Post by quad3d@work on 2006-08-14
[This did the trick for me]("http://www.ubuntuforums.org/showpost.php?p=1380049&postcount=436"), running NVIDIA 6800GT.

---

### Post by LGLozano on 2007-10-25
> **zitch said:**
> Well, that by itself didn't work (I couldn't find the "don't resize" option under Edit->Preferences->Display in the VMWare console), but it did spark an idea.

I ended up doing gedit ~/.vmware/preferences and modified the line that said pref.autoFitFullScreen = "fitHostToGuest" to pref.autoFitFullScreen = "fitGuestToHost" and that did the trick! 

Thank you for your help!

Edit: Well, that does work, but apparently VMWare will constantly rewrite that file and set it back to "fitHostToGuest" and I'll get the same error later anyways.  I'll have to ask VMWare about this...

This worked for me... I'm using a Dell GX620 with an ATI X600. I tried everything else and nothing worked. I'm using VMWare Server 1.04

Thanks!

---

### Post by dropsonde on 2007-11-12
This worked for me!!  Thanks!
I did however run into an issue whe I changed resolutions on the guest OS in full screen.  After the change to the preferences file, I launched VMware.  I switched to full screen and voila it worked.  Only problem was that I had the two black bars on the side since my aspect ratio was off.  I wen to change resolution and it kicked me to windowed mode.  When I tried to relaunch full screen I got the original error message "Unable to find an appropriate host video mode".  I quit out of VMware and was able to launch full screen fine when I went back in.  Not a big issue, but I thought I'd mention it. 

DS

---

### Post by chadjohnson on 2008-01-15
Another solution that might work...
```

DISPLAY=:0 vmware

```

To make your shortcuts work like this, change their command to
```

env DISPLAY=:0 vmware

```

---

