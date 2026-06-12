---
title: "disable volume indicator, how to?"
date: 2010-01-23
forum: General Help
---

### Post by ryanmills on 2010-01-23
I'm running karmic on my laptop and the volume control is on the front. I'm forever bumping it and having the GUI volume indicator pop up. Is there a way to disable the popup GUI indicator without disabling the sound?

---

### Post by Enigmapond on 2010-01-23
Just remove it from the panel. It's part of the "Notification Area".

---

### Post by ryanmills on 2010-01-23
That did not seem to do it, I should point out the GUI im talking about is not the one in the panel but the popup when the volume changes.

---

### Post by garvinrick4 on 2010-01-23
> **ryanmills said:**
> That did not seem to do it, I should point out the GUI im talking about is not the one in the panel but the popup when the volume changes.

There are more than one is it the small one that go's north and south or the big one that
go's east and west?

---

### Post by ryanmills on 2010-01-23
If north is up, then its the big one that goes east to west.

---

### Post by garvinrick4 on 2010-01-25
It is in Keyboard shortcuts, disable it.  That would be System/Preferences/keyboard shortcuts to
volume up and volume down. disable and no more large east and west. Or just make it like F11 for down and F12 for up and only pops up when you press the function keys. No need to use touchpad or mouse for sound then.

---

### Post by ryanmills on 2010-01-25
> **garvinrick4 said:**
> It is in Keyboard shortcuts, disable it.  That would be System/Preferences/keyboard shortcuts to
volume up and volume down. disable and no more large east and west. Or just make it like F11 for down and F12 for up and only pops up when you press the function keys. No need to use touchpad or mouse for sound then.


sweet that did it, thanks :)

---

### Post by D3V11 on 2010-01-25
```

sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled 

```

This will disable **all **popup notifications after you reboot. Don't ask me how to turn them back on...looking at the code, probably have to move the file back to **/usr/share/dbus-1/services/org.freedesktop.Notifications.service.**

---

### Post by garvinrick4 on 2010-01-26
> **D3V11 said:**
> ```

sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled 

```This will disable **all **popup notifications after you reboot. Don't ask me how to turn them back on...looking at the code, probably have to move the file back to **/usr/share/dbus-1/services/org.freedesktop.Notifications.service.**
  OP  wanted to remove a different pop-up than the Applet in Notification area.

---

### Post by benjamin222 on 2010-05-16
> **garvinrick4 said:**
> It is in Keyboard shortcuts, disable it.  That would be System/Preferences/keyboard shortcuts to
volume up and volume down. disable and no more large east and west. Or just make it like F11 for down and F12 for up and only pops up when you press the function keys. No need to use touchpad or mouse for sound then.

All this does is disable the keyboard shortcut, so if someone did this then they wouldn't be able to use their laptop's volume slider/buttons. Is there any way to actually Disable the volume pop-up gui!? I've been everywhere, this seems like it should be something really simple to fix. Apparently not.

---

