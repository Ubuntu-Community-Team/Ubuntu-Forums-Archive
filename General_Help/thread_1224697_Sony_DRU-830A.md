---
title: "Sony DRU-830A"
date: 2009-07-27
forum: General Help
---

### Post by 3nertia on 2009-07-27
I have a Sony DRU-830A usb dvd burner. When I put a cd in it it pops up, and puts an icon on my desktop. But it says it's not mounted. I wanna be able to mount it to a specific directory, but I have no idea what the device path is. I've checked dmesg with no luck. Anyone got any ideas. No idea what version of Ubuntu, but I think it's 8.10 and has recently been updated (not sure with what). Sorry if this has been posted elsewhere, I searched and could not find it. Also, my apologies if this isn't the right place for this post.

---

### Post by 3nertia on 2009-07-27
Guess noone has any ideas about this? Can't wait 'till XChat downloads...Maybe someone lingering in the Ubuntu chat rooms will know...

---

### Post by komputes on 2009-07-30
The device path s not /dev/cdrom#?

What do you get when the external CD drive is plugged in and you run:

```
$ ls /dev/cd*
```

---

