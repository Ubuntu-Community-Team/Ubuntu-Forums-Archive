---
title: "Plymouth error: cant display splash screen at boot up"
date: 2011-09-07
forum: General Help
---

### Post by ubun2freak on 2011-09-07
Hi guys, I'm messing around with Plymouth splash screen problem.
I've installed Plymouth in my Ubuntu 11.04 and it used to work well before. 
Recently, after booting to Ubuntu using Grub2, my screen just turn black until entering the kdm login screen. I've tried Plymouth Manager to install theme but it didn't work as well. So any helps would be greatly appreciated.

---

### Post by stinkeye on 2011-09-07
Do you mean you have installed a plymouth theme?
If so, and it's not working you can go back to the original or choose your new theme with
```
sudo update-alternatives --config default.plymouth
```

Followed by
```
sudo update-initramfs -u
```

---

