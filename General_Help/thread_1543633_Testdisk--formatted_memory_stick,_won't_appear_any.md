---
title: "Testdisk--formatted memory stick, won't appear anywhere!"
date: 2010-08-01
forum: General Help
---

### Post by ysaric on 2010-08-01
I am using Ubuntu 10.04.

I was having problems with bad sectors on a Sony memory stick--a couple of photos that we couldn't get off.  So I installed testdisk and photorec and successfully got the photos off.  That's the good news.

I decided I format the stick using testdisk.  I unmounted it and formatted it (FAT) . . . I don't know whether I re-mounted it, there was some message about rebooting.

In any event I now can't get the stick to show up *at all*, no matter what I do.  testdisk doesn't seem to see it, it doesn't come up on my desktop when I plug the camera in.  The camera doesn't recognize that it, my windows boxes don't see it either.

Any help would be greatly appreciated.  If any output would be helpful just let me know.  *sigh*

---

### Post by llamabr on 2010-08-01
Ugh.  Sony memory sticks.  Why can't they just conform to the standard?

Do you have one of those adapters?  Plug it into the thing, give me 5 pushups (or however many you do in about 15 seconds), and then post:

```
dmesg | tail
```

If that works, let's reformat it using mkfs, and not testdisk

---

### Post by ysaric on 2010-08-01
Can I do that with the stick in the camera and the camera connected to the computer?  I don't at this point have any other way to access it from the computer--no 7-in-1 card reader or built-in slot, etc.

---

### Post by llamabr on 2010-08-02
> **ysaric said:**
> Can I do that with the stick in the camera and the camera connected to the computer?  I don't at this point have any other way to access it from the computer--no 7-in-1 card reader or built-in slot, etc.

Probably.  With my sony camera, I have to press a button after I plug it in to get it to mount.  But if that's the way it normally works, then yes, the same instructions will apply.

---

### Post by ysaric on 2010-08-03
Output of dmesg | tail

> jim@jmj-main:~$ dmesg | tail
[   38.101777] wlan0: deauthenticating from 00:16:01:ed:0d:42 by local choice (reason=3)
[   38.101819] wlan0: direct probe to AP 00:16:01:ed:0d:42 (try 1)
[   38.104922] wlan0: direct probe responded
[   38.104925] wlan0: authenticate with AP 00:16:01:ed:0d:42 (try 1)
[   38.106728] wlan0: authenticated
[   38.106745] wlan0: associate with AP 00:16:01:ed:0d:42 (try 1)
[   38.109184] wlan0: RX AssocResp from 00:16:01:ed:0d:42 (capab=0x431 status=0 aid=3)
[   38.109186] wlan0: associated
[   38.109847] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.741433] wlan0: no IPv6 routers present
jim@jmj-main:~$ 


Camera was plugged in and turned on, waited the required amount of time (and am feeling quite buff for it, thanks :).

What am I not seeing that I should?  What is my next step?

Thanks much for any information or assistance.

---

