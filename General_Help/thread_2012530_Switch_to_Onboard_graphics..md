---
title: "Switch to Onboard graphics."
date: 2012-06-29
forum: General Help
---

### Post by stevanity on 2012-06-29
Hey guys!

Ive been using Ubuntu for a while now and I had a Nvidia 9800 GT card when I was using it. But now the card has become pretty old and it stopped working. So I removed it and switched back to my onboard gfx on my Intel 946 GZIS Motherboard.

But Ubuntu seems to be looking for my old card and it is not loading at all. I see the bootscreen and later I get only  a blank screen. It doesnt show me the Login screen.

But I can access the terminal and login and do stuff. But I have no idea how to change the settings so that Ubuntu would use my onboard graphics.

Please help. Im working on a rails project and I need to get back on ubuntu asap :(

Thanks in advance :)

---

### Post by dcstar on 2012-06-30
> **stevanity said:**
> Hey guys!

Ive been using Ubuntu for a while now and I had a Nvidia 9800 GT card when I was using it. But now the card has become pretty old and it stopped working. So I removed it and switched back to my onboard gfx on my Intel 946 GZIS Motherboard.

But Ubuntu seems to be looking for my old card and it is not loading at all. I see the bootscreen and later I get only  a blank screen. It doesnt show me the Login screen.

But I can access the terminal and login and do stuff. But I have no idea how to change the settings so that Ubuntu would use my onboard graphics.

Please help. Im working on a rails project and I need to get back on ubuntu asap :(

Thanks in advance :)

You need to replace the existing /etc/X11/xorg.conf file with a copy of the default one in that folder. Do a search for detailed instructions.

---

