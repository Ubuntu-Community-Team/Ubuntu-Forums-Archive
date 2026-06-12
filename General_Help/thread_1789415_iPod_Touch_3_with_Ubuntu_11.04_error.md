---
title: "iPod Touch 3 with Ubuntu 11.04 error"
date: 2011-06-23
forum: General Help
---

### Post by trust-no-one on 2011-06-23
Hi guys,

Gotta say I'm absolutely loving Ubuntu 11.04! But that's not why I'm here. Recently, I've been trying to get my iPod Touch 3 to work with Ubuntu 11.04 64 bit. It mounted fine in 10.10, but 11.04 gives me the following error when I plug it in:

```
Unable to mount Steve's iPod
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
```I've already read other tutorials on how to fix this, but none of them worked... can anyone offer me suggestions of things to try or hardware or software details I need to give? I really want to be able to sync music to my iPod from Linux as iTunes is really annoying.

TIA
tno

---

### Post by smallblackanimal on 2011-06-23
[http://xmemory.tompium.com/2011/04/iphone-does-not-mount-after-ios421-or.html](http://xmemory.tompium.com/2011/04/iphone-does-not-mount-after-ios421-or.html)


That should do it.

---

### Post by trust-no-one on 2011-06-24
This works fine (I added the repo, updated etc.) but when I get to installing libimobiledevice1 withsynaptic, it isn't there.... there is only libimobiledevice2 (which is installed) and a -dev and -doc. What do I do?????

tiatno

---

### Post by robbiemacg on 2011-06-28
I was having a similar issue. As well as installing **libimobiledevice2** I had to also install **libimobiledevice-utils**.
I plugged in my partner's iPod touch got the infamous error message, ran the command  **idevicepair unpair** via CLI... unplugged the device, plugged it back in, and there it was in Banshee, no problem transferring songs, etc.

---

### Post by trust-no-one on 2011-06-29
Thanks for the response, but sill no luck. libimobiledevice-utils was already installed, and running "idevicepair unpair" only yielded a segmentation fualt... Please help!

tno

---

### Post by robbiemacg on 2011-06-29
I'd like to try to help you find a solution that's going to work for you.

The first time I ran the above command, a received the same error you did (or something very similar). I had had the iPod plugged in for a while and been trying various fixes. It was only when I unplugged the device, plugged it back in, and ran the  **idevicepair unpair **command immediately after seeing the infamous "DBus message" that I got the desired result.

If you do that, and the outcome's not favour able, maybe post the message you see in the terminal window, and we can go from there.

Have you tried to mount you iPod manually via the **ifuse** command or anything like that?

---

