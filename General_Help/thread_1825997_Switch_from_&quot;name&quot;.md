---
title: "Switch from &quot;name&quot;"
date: 2011-08-16
forum: General Help
---

### Post by northwestern on 2011-08-16
Is it possible to remove the "switch from" option from the drop down menu in Ubuntu 11.04.

Many Thanks

Northwestern

---

### Post by fabricator4 on 2011-08-16
> **northwestern said:**
> Is it possible to remove the "switch from" option from the drop down menu in Ubuntu 11.04.

Many Thanks

Northwestern

Ha, it's well hidden in an unlikely place.  First run

```
sudo gconf-editor
```

Next open 
```
Apps
  ->Gnome Screensaver
```

And untick "user-switch-enabled"

You probably need to reboot.  I haven't verified that this works, as I don't want to reboot right at this minute.  Found it in a google search.

It's also possible that this is a red herring (in Gnome screensaver???)

Chris

---

### Post by northwestern on 2011-08-16
Thank for your reply, did as requested and rebooted but "switch from" is still there.
Thanks Northwestern

---

### Post by fabricator4 on 2011-08-16
> **northwestern said:**
> Thank for your reply, did as requested and rebooted but "switch from" is still there.
Thanks Northwestern

Yes, I had bad feeling about that advice - didn't make sense that it would be under screensaver.  The only other suggestion I found was to change the code (it's in C) and recompile.  Something I may have a look at when I've got a bit more time.  The menu needs to be a bit more configurable.

Chris

---

