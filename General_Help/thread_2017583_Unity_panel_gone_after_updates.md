---
title: "Unity panel gone after updates"
date: 2012-07-05
forum: General Help
---

### Post by Xero Xenith on 2012-07-05
**TL;DR:**
[list][*]Installed a hundred updates, Unity 3D panel gone.
[*]64-bit Ubuntu 12.04, nVidia drivers from a PPA, no other modifications.
[*]Things work fine in Unity 2D, but broken for all users in Unity 3D.[/list]

------------------------------
My Ubuntu 12.04 64-bit install was happily accumulating dozens of pending updates, until I shamefully disturbed its peace and installed them. Now I have no sidebar in Unity 3D on any user accounts.

My video card is a reasonably old nVidia (9500GT I believe) and one of the updates was from a driver PPA. If there's a way to auto-revert things back to the old version, I'm willing to try. (I just tend to automatically suspect the binary blob in cases like this... not sure if it would help though.)

I've searched this problem - it seems reasonably common - but unity --replace and other such commands throw back an error message. I can reproduce it exactly if helpful, but it claims that "unity-panel-service" is missing.

Another solution that worked for some (but not me) was checking ccsm and making sure the Unity plugin was enabled and not conflicting with any GNOME stuff. No luck for me here either!

Attached is a screenshot of what it looks like when I press the Super key (the Dash [?] works fine). Note that the highlight around where the panel should be is only there when the Dash is open - there's no trace at all of where the panel should be when the Dash is not open.

Unity 2D works fine, so I do have a working system, but I liked Unity 3D! Any help at all getting my panel back would be hugely appreciated :)

---

### Post by Xero Xenith on 2012-07-07
Bump - still having this problem. (Added a TL;DR to the post above.)

---

### Post by irv on 2012-07-07
I have to go off line in a few minutes, but may I suggest that you try restarting in recovery mode, and run a fix on the video from the recovery menu. That would be somewhere to start.

---

### Post by msammels on 2012-07-07
The panel isn't gone, per say, the icons are missing. If you hover over the left panel, do you get any text at all? Also, you didn't need to install the nVidia drivers from a PPA, as they come bundled with Ubuntu (System Settings -> Additional Drivers).

---

### Post by Xero Xenith on 2012-07-09
Now that my PC's finished its computathon, I can get back to this. Thanks for the replies :)

> **irv said:**
> I have to go off line in a few minutes, but may I suggest that you try restarting in recovery mode, and run a fix on the video from the recovery menu. That would be somewhere to start.

Thanks, will try that :)

> **msammels said:**
> The panel isn't gone, per say, the icons are missing. If you hover over the left panel, do you get any text at all? Also, you didn't need to install the nVidia drivers from a PPA, as they come bundled with Ubuntu (System Settings -> Additional Drivers).

The panel does appear to be gone. When I organise my desktop, the icons shuffle into the space normally taken by the panel. There's no hint at all of the panel when the dash is not open. It's pretty gone :P

EDIT: screenshots attached, sorry for low-res. Left one has the dash not open - the panel isn't there at all.

The unity-panel-service error is:
"unity-panel-service: no process found"

---

### Post by irv on 2012-07-09
I remember having this same problem back in 11.04 or 11.10. As I remember it happen after installing Gnome3 and when I went back to Unity I had this happen. I think what I ended up doing was re-installing the OS.
I am sure there is a fix for this, but I don't have an answer for you. Sorry. I feel it might have something to do with the video driver from the ppa for the 3d seeing the 2d is working. If you installed the driver from additional drivers can you try removing it from there?

---

### Post by jmfal on 2012-07-09
Try this in a terminal

```
 unity  --reset     
```

This might set unity to default, so any changes to the desktop may be undone.

---

### Post by Xero Xenith on 2012-07-09
> **irv said:**
> I remember having this same problem back in 11.04 or 11.10. As I remember it happen after installing Gnome3 and when I went back to Unity I had this happen. I think what I ended up doing was re-installing the OS.
I am sure there is a fix for this, but I don't have an answer for you. Sorry. I feel it might have something to do with the video driver from the ppa for the 3d seeing the 2d is working. If you installed the driver from additional drivers can you try removing it from there?

Happy to try this if it could help - do I just remove that package, remove/deactivate PPA, install one from normal repos, reboot? Thanks :)

> **jmfal said:**
> Try this in a terminal

```
 unity  --reset     
```

This might set unity to default, so any changes to the desktop may be undone.

Tried this a few times, no help :( Thanks for the suggestion though.

---

### Post by irv on 2012-07-09
What I was saying was if you installed driver from "System Setting", "Additional Driver" then remove them from there and use the default video driver. If that doesn't fix it you can always re-install it.
[ATTACH]220981[/ATTACH]

---

### Post by Xero Xenith on 2012-07-10
Yep, it turned out to be the driver! The old "blame the binary blob" works a treat...

These are the steps I took (posting for anyone else with the same issue caused by a PPA):

[list][*]Go into System Settings, Additional Drivers, remove from there (as above).
[*]Restart - you're now using the default driver. The panel now works [for me] in both Unity 2D and 3D, but significant graphical corruption (loads of flickering and things disappearing and windows getting corrupted).
[*]Go into Synaptic, Software Sources, disable the bad nVidia PPA.
[*]Refresh packages.
[*]Install nvidia-current.
[*]Restart - all is now well![/list]

Very happy it's working. Thanks for the help :)

---

### Post by irv on 2012-07-10
This is great to hear, and I see you are a happy Ubuntu user again. Why don't you mark this thread "Solved".

---

