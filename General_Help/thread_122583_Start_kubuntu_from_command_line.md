---
title: "Start kubuntu from command line?"
date: 2006-01-28
forum: General Help
---

### Post by bluevoodoo1 on 2006-01-28
After logging out of GNOME I'm often facing the full black screen terminal. Logging back into GNOME is easy, "startx." Since that method bypasses the GDM (and the ability to change sessions), Is there a way for me to log into Kubuntu directly from the terminal?

---

### Post by Jason_25 on 2006-01-28
sudo /etc/init.d/gdm restart

---

### Post by bluevoodoo1 on 2006-01-28
yes, I should have mentioned that I tried that and it "failed."

---

### Post by bluevoodoo1 on 2006-01-28
I wrote sudo /etc/init.d/gdm start ... not restart. That's why it didn't work. 

THANKS!

---

