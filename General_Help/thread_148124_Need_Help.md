---
title: "Need Help"
date: 2006-03-21
forum: General Help
---

### Post by ampteed on 2006-03-21
Hi  my ubunto freezes on loging after install!
It starts to load hear some music and when the logo apears the system go in to a halt. the mouse freezes alsow!!!

sorry for my english!!!!

Thanks!

---

### Post by taurus on 2006-03-21
Look in /var/log/Xorg.0.log to see what does it say, assuming that you can get to a terminal?  <Ctrl><Alt>F2 would put you to a console so you need to log in first.  Then run
```

more /var/log/Xorg.0.log

```

---

### Post by ampteed on 2006-03-21
thanks! There were several warnings but no errors!
Could Not fix any of them so I reinstalled but the same problem!
any others ideas?

---

### Post by taurus on 2006-03-21
What is your video card?  Perhaps you need to use a generic driver for your video card and once you get into X, install whatever, nVidia or ATI, for it!  At the prompt, type
```

sudo nano /etc/X11/xorg.conf

```
Scroll down until you see the section for your video card.  Change whatever driver you have right now to vesa...
```

Driver              "vesa"

```
Save it and reboot.  Hopefully, your X won't crash anymore...

---

### Post by ampteed on 2006-03-22
Thanks :D
Its working fine

---

