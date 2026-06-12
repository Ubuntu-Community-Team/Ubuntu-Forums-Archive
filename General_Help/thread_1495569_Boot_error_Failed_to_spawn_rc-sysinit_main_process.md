---
title: "Boot error: Failed to spawn rc-sysinit main process"
date: 2010-05-28
forum: General Help
---

### Post by Athunye on 2010-05-28
I have a minimal installation of Ubuntu, with lxde-core and some other apps I really use. Sometimes when I start the system, it hangs and nothing else happens. I hit Esc and then I see:
```

init: Failed to spawn rc-sysinit main porcess: Unable to open console: Input/Output error.

```

I get stuck there, and the only thing I can do is to hold the power button, shutdown, boot again, and pray it will boot fine. Sometimes it does, sometimes it doesn't.

---

### Post by ed1w2ard on 2010-06-04
Hi,

I had the same problem this morning. Flashing bootsplash and the init: Failed to spawn rc-sysinit main process: Unable to open console: Input/Output error.

I traced the problem to my USB keyboard. I replaced my keyboard about 3 days ago and it worked fine during these 3 days. This morning it went nuts. Now this keyboard has 2 extra USB 1.0 slots in it on the back (which I don use). Whenever I unplugged the keyboard Ubuntu boots up fine.
My guess is that the routine disk check is trying to access these ports causing it to hang and go nuts. I switched back to my old USB keyboard and all is fine now.
Check your usb connections and unplug them one by one to locate the source.

Hope this helps.

---

