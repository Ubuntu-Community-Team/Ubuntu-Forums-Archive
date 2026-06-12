---
title: "rdesktop/tsclient"
date: 2010-05-10
forum: General Help
---

### Post by ppb1701 on 2010-05-10
okay last week I wasn't having any problems.  I am rdping to our terminal server for work.  Today it's been freezing and disconnecting after 30 secs to a few minutes with the reset by peer message.  At times though today it froze for a while before reading the lost connection to which in fullscreen mode was killing using the keyboard.

So I rebooted into slax (my other option was vista ewwwww) and fired up tsclient and connected to the server and haven't had any problems since.  So I'm not dead in the water but would be nice to get it going correctly again in lucid.

I've reinstalled rdesktop, tried reminna instead of tsclient, killed my session on the server, rebooted my laptop, tried a different mtu.  Only thing I can think of is one of the updates from the last few days changed something but I'm not sure what.

---

### Post by gradinaruvasile on 2010-05-10
I use Remmina for RDP in Debian Squeeze and works really well.
Try using lower colors - i always use 256 colors and works faster and more reliable. Dont use bitmap caching or compression - i found that this caused random disconnects.
If the server is running Windows Server, try the "attach to console" option.

---

