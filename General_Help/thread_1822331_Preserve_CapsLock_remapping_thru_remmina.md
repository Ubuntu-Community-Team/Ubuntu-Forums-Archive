---
title: "Preserve CapsLock remapping thru remmina?"
date: 2011-08-10
forum: General Help
---

### Post by DavidBiesack on 2011-08-10
I use remmina on Ubuntu 10.10 to connect to a Windows 7 PC.

I universally map CapsLock to a Ctrl key (easier on my pinky when using Emacs as much as I do) on both Ubunto (via Keyboard Preferences > Layouts > Options) and on Windows via HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout.

However, when I connect to Windows via remmina, pressing CapsLock on my Ubuntu host keyboard results in a "real" CapsLock, not Ctrl key, being passed to Windows.

I'm not sure if this is in Ubuntu or remmina.

Does anyone know a workaround?

---

### Post by forty2 on 2011-08-14
Have you found a workaround for this issue?  It's bugging me too.

I think I've managed to figure out that the issue is not with Remmina itself, but FreeRDP, which Remmina uses as its RDP implementation.  There's a bug filed with FreeRDP here that seems to cover the problem: [http://www.freerdp.com/jira/browse/FREERDP-20](http://www.freerdp.com/jira/browse/FREERDP-20)

FreeRDP (and Remmina) seems to use the file /usr/share/freerdp/keymaps/evdev to map between xkb keycodes and Windows Virtual Key Codes.  I've played around with that file a bit trying to get it to map caps lock to control, but I haven't had any luck yet.

---

### Post by forty2 on 2011-08-14
I can't believe I missed this before, but it turns out there's an option for this in Remmina's Preferences dialog.

Open Preferences, go to the RDP tab (way on the right), then make sure "Use client keyboard mapping" is checked.  After I did that, my caps-lock-to-ctrl mapping works perfectly.

---

### Post by DavidBiesack on 2011-08-15
Thanks, I'll try that. I'm running 0.8.0 and the preferences do no show that; sourceforge shows the current release as 0.9.2. I'll have to see about updating remmina, tho it is not in the Ubuntu Update Manager I'm offered for 10.10, so I'll have to
look for a direct update install.

I did find that rdesktop sends my mapped keys through correctly.

---

### Post by AronVanAmmers on 2012-01-05
Cheers guys. Exactly what I was looking for.

I have Caps lock mapped to Back space both on the Ubuntu client (using xmodmap) and Windows XP host (using the registry fix mentioned above), but in Remmina my Caps lock became a regular Caps lock again.

With the "Use client keyboard mapping" the mapping works again. Remmina now just about perfectly suits my RDP needs.

I love you, Ubuntu community and open source developers :)

---

