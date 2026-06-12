---
title: "X Server Won't Start on Restart"
date: 2006-05-08
forum: General Help
---

### Post by DarkNemesis618 on 2006-05-08
I just installed the nvidia 8756 drivers for Ubuntu 5.10 x86_64.  The drivers installed fine.  But now whenever I restart my computer, X Server fails to start and I have to reinstall the drivers for it to work.  It's a pain in the @$$ and I was just wondering if anyone has any ideas.  Attached is my current (working at the moment) xorg.conf and the error log.  Thanks. ](*,)

Oh, it should be noted I have the nvidia GeForce 7900GT and as I understand, the 8756 drivers are the only ones at the moment that support my 7900 GPU.

---

### Post by johnc4510 on 2006-05-08
For my cheap FX 5500, I used the following commands to install the driver then configure it:
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
So you might try this after restart(In Terminal):
sudo nvidia-8756-config enable
After that ctrl+alt+backspace to retart x

No promises though!

---

