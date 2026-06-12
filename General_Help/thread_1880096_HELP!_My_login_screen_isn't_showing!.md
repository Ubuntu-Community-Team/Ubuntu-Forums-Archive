---
title: "HELP! My login screen isn't showing!"
date: 2011-11-12
forum: General Help
---

### Post by linuxuser12345 on 2011-11-12
I am using Ubuntu 11.04 on a netbook, and I decided to try Lightdm, and I figured out I didn't like it, so I removed it via the Ubuntu Software Center. Now, I just logged out and absolutely NO login screen appears! All I get is a black screen with an "x" as the mouse cursor! I can't even log back in now! How do I get back into my GUI and get GDM as my login screen back?

---

### Post by linuxuser12345 on 2011-11-13
Is there a way I can set GDM back as the default login screen through a terminal?
How do I start a terminal without being in my GUI?

---

### Post by randyklein99 on 2011-11-13
Reboot and choose the recover option in the grub menu (you may have to hit shift during POST to get the grub screen).  Once you are at a terminal: 
```

sudo dpkg-reconfigure gdm
```

---

### Post by linuxuser12345 on 2011-11-13
Actually, a simple shut down and start up fixed the problem! :)

Thank you

---

