---
title: "Ubuntu 10.04 Netbook Edition installation on HP Mini 110 problem"
date: 2010-04-29
forum: General Help
---

### Post by go7Ul1ai on 2010-04-29
Hello,

I have installed Ubuntu 10.04 Netbook Edition onto my girlfriends HP Mini 110 using a USB, it says installation is successful, so I restart and straight after the BIOS, a blinking cursor appears on the top left corner and stays there, no matter how long I leave it. There is nothing I can do, it's not letting me do anything.

I have tried this twice, anyone experiencing this? Any solutions?

Lee

Edit: So I've got it working, but there were lots of messages on start up indicating there are errors with firmware or something? (text went too fast to read).

Edit 2: The only way it would boot the system up is if I press "F10" on the bios, then press any keys before it freezes on me..

Edit 3: Now I can't get it to boot at all

---

### Post by karzon on 2010-05-01
I'm having the exact same issue with the same hardware.

If I hold down shift while it boots I can get to the grub2 menu and recovery mode works from there. It's really odd, if I just reset countless times, sometimes it works. I believe it has something to do with switching graphics mode, but I don't know. very frustrating. She's looking at me waiting for her netbook back lol

---

### Post by karzon on 2010-05-01
it has something to do with the b43 broadcom wireless drivers.

If you just start tapping keys during boot-up, you'll see for whatever reason it will boot up fine. I then connected to wired connection and updated then installed the proprietary STA driver. all works fine now. boots every time. The only thing is even thought it connects to my WiFi now, i always have an exclamation point on the connection. But it works fine.

Let me know if this works for you....

---

### Post by Nostoc on 2010-05-01
This is what you are looking for

[http://ubuntuforums.org/showthread.php?t=1467734](http://ubuntuforums.org/showthread.php?t=1467734)

---

