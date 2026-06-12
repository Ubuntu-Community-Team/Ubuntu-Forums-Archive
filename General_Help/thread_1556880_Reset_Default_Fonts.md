---
title: "Reset Default Fonts"
date: 2010-08-20
forum: General Help
---

### Post by Dr. Guitar on 2010-08-20
Hi all! 

I accidentally deleted my /etc/fonts/font-config file and now my fonts are all terribly out of whack in several applications including Synaptic, Chromium, Firefox, etc. How do I reset my fonts back to the Lucid Lynx default?

Many thanks

---

### Post by Dr. Guitar on 2010-08-20
Just an update, resetting my gconf settings didn't work. Please help!

---

### Post by Bachstelze on 2010-08-20
Try reinstalling fontconfig

```
sudo apt-get install --reinstall --purge fontconfig fontconfig-config
```

---

### Post by M4he on 2010-08-20
Unfortunately, I cannot tell you how to reset it but I can upload mine: [ATTACH]167001[/ATTACH]
I'm running an up-to-date version of 10.04 so it should match. Just remove the ".txt" at the end and place it into /etc/fonts/

Good luck!

---

### Post by Dr. Guitar on 2010-08-20
Thank you so much! I got an out of memory error trying to reinstall fontconfig, but after replacing the text manually my system fonts now look like they should. However, my firefox font still hasn't been restored. Is there anything I can do about this?

---

