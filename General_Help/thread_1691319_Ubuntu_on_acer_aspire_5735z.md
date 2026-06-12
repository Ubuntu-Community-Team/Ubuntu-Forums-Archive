---
title: "Ubuntu on acer aspire 5735z"
date: 2011-02-19
forum: General Help
---

### Post by megahost on 2011-02-19
I am currently running Ubuntu 10.10 on my acer aspire 5735z. It runs well other than a couple of issues.
*Battery meter if off a lot of the times
*Lag with trackpad after not touching it for a minute.
*Sometimes on bootup, my computer will start then shut down without entering a boot-up.

Are there any solutions to these? If so it is much appreciated. Thanks!

---

### Post by elundmark on 2011-10-09
> **megahost said:**
> 
*Sometimes on bootup, my computer will start then shut down without entering a boot-up.

Are there any solutions to these? If so it is much appreciated. Thanks!

I just bought one too, and installed the 11.10 beta2.
Still problems with boot at times; firstly I recommend not using the WiFi button (the one with the -orange satellite-dish icon), that seems to cause all kinds of weird stuff to happen, incl. not being able to boot the next time. 

Another thing I found works is removing the battery (or plug it in) or plugging/unplugging the power source, that seems to help it boot. But I've found that it boots well as long as one of the above hasn't happened since the last boot.

Another thing about the 5735Z, it suffers from the "random log out" [bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/778490"), at least mine does. A workaround is to disable **librecord.so** which monitors your keyboard, although this stops AutoKey from working, but rather that then loosing all unsaved work when you get logged out, and trust me, it happens a lot.

```
sudo mv /usr/lib/xorg/modules/extensions/librecord.so /usr/lib/xorg/modules/extensions/_librecord.so_
```

This is the workaround, enter it in the terminal. Note that an error message will appear at every login, that's a sign it worked.

otherwise, everything works, great little computer for Ubuntu :)

---

### Post by Aragornn on 2011-10-31
hi
I have the same laptop, and Ubuntu didn't work for me well.
the wifi don't work, I tried to install the drivers manually but I didn't succeed
didn't have issues with the wifi ?if so,how did you deal with it?
please help me I'm desperate
ps : I'm new to Linux

---

