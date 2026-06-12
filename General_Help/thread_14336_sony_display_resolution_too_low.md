---
title: "sony display resolution too low"
date: 2005-02-06
forum: General Help
---

### Post by jimgriffin on 2005-02-06
Hello,

Sorry to post this, but i'm new to linux. I'm running Ubuntu on a mac, so it's the ppc version. I have a sony sdm-hs73 lcd display which has a native resolution of 1280x1024. The problem is the base install of ubuntu is only letting it run at 1024 x 768, so everything is slightly blurry and it's killing my eyes. I went into the screen resolution tool and 1024 seems to be the max. Does anyone know where I should start looking to fix this problem? I need to fix this first. Thanks!

Jim
[email]me@jimgriffin.org[/email]

---

### Post by Sye d'Burns on 2005-02-06
Check to make sure that your refresh rates have been correctly entered would be my first suggestion. Go to a terminal and type:

sudo nano /etc/X11/XF86Config-4 (unless you're using xorg)
enter your password

Then look through the config file and see 'Section Monitor'

Then if everything looks right, you might need to set up your video card's driver.

---

