---
title: "splash"
date: 2010-06-05
forum: General Help
---

### Post by mozi on 2010-06-05
Hi,
after latest updates in lucid I've lost splash screen on startup, how to fix it? I tried to reinstall plymouth but nothing changes,
thanks

---

### Post by echo6 on 2010-06-05
What graphics card have you got?

Look at /usr/share/doc/plymouth/README.debian there may be something in there that will help troubleshoot.

---

### Post by flyver on 2010-06-05
I had to enable a new splash theme, and then re-install the standard one.

```
sudo update-alternatives --config default.plymouth
```
Then I chose the splash theme whose description differed the most compared to mine (mine was *0, I chose 2)

Then:
```
sudo update-initramfs -u
```

I chose to restart my computer, and then I did the very same over again, only this time I chose the original splash screen.

And that's it!

Reference: [http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

---

### Post by mozi on 2010-06-05
thanks, that worked :)

---

### Post by flyver on 2010-06-05
:d

---

