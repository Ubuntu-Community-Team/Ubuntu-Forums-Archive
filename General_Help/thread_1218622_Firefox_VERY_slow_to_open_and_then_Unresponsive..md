---
title: "Firefox VERY slow to open and then Unresponsive."
date: 2009-07-20
forum: General Help
---

### Post by osc1882 on 2009-07-20
Don't know why. When I got home today my internet was not working, unplugged the cable modem, plugged it back in. That didn't seem to work so I restarted the computer. When I came back the Internet was working but firefox was taking a VERY long time to open and then once I did it was unresponsive right away and then it would work again for a very short amount of time and then righ back to unresponsive and that's how it has been acting for a few hours now. I'm useing.... a different browser right now. lol.

---

### Post by osc1882 on 2009-07-20
and before you asks, it looks like this:




grammatrain@tprb:~$ firefox

Error while parsing contractID: QueryInterface - TypeError: contractArray[1] is undefined

Error while parsing contractID: QueryInterface - TypeError: contractArray[1] is undefined

Getting service...
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket

Getting preference for key no_welcome_screen failed: [Exception... "Component returned failure code: 0x8000ffff (NS_ERROR_UNEXPECTED) [nsIPrefBranch.getBoolPref]"  nsresult: "0x8000ffff (NS_ERROR_UNEXPECTED)"  location: "JS frame :: chrome://foxytunes/content/utils.js :: anonymous :: line 987"  data: no]
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
wot_cache.add_target: caching start.ubuntu.com
start.ubuntu.com: 0: (r, c) = (94, 57)
start.ubuntu.com: 0: (i) = (0)
start.ubuntu.com: 0: (l) = (0)
start.ubuntu.com: 1: (r, c) = (95, 59)
start.ubuntu.com: 1: (i) = (0)
start.ubuntu.com: 1: (l) = (0)
start.ubuntu.com: 2: (r, c) = (94, 59)
start.ubuntu.com: 2: (i) = (0)
start.ubuntu.com: 2: (l) = (0)
start.ubuntu.com: 4: (r, c) = (94, 58)
start.ubuntu.com: 4: (i) = (0)
start.ubuntu.com: 4: (l) = (0)
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
^ADCOPClient::attachInternal. Attach failed Could not open network socket

---

### Post by Aflack on 2009-07-20
Just wondering, have you tried using FF without any add ons yet?

---

### Post by osc1882 on 2009-07-20
THANK YOU Aflack! That did it. I might be one of the add block servers? don't know. i"m going to reinstall my ad-ons now.

---

### Post by priestscientist on 2009-07-20
Hmm You know what? I am having a similar problem but not like that. Mine is different. Firefox comes on slow and when I go onto YouTube and try and watch a video the video skips a couple of frames. but when I play a video using MPlayer the video plays smoothly. What's up with that?

---

### Post by lovinglinux on 2009-07-21
> **priestscientist said:**
> Hmm You know what? I am having a similar problem but not like that. Mine is different. Firefox comes on slow and when I go onto YouTube and try and watch a video the video skips a couple of frames. but when I play a video using MPlayer the video plays smoothly. What's up with that?

See [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

---

