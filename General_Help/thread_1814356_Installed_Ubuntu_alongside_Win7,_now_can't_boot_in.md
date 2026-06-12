---
title: "Installed Ubuntu alongside Win7, now can't boot into Windows."
date: 2011-07-29
forum: General Help
---

### Post by Shinigamii100 on 2011-07-29
Hello everyone, new Ubuntu user here :)

So last night I burned a cd with Ubuntu 11.04 64 bit. I popped it into the drive, restarted and chose to install it directly alongside windows. Everything worked fine, and I was very satisfied. But when I rebooted it went straight to Ubuntu. I tried going  into the boot option, and thought I had solved it because there were two drives I could boot from, but both take me back into Ubuntu. 

It would be nice if I could rectify the situation, or at least completely uninstall Ubuntu. If there's any additional info you need, just ask and I'll get it for you.

Thanks!

---

### Post by Sergius14 on 2011-07-29
Run in Terminal this:

```
sudo update-grub2
```

If it doesn't work, do further research about how to configure o reinstall Grub. There are may guides already.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

