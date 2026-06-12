---
title: "installation problems"
date: 2009-12-21
forum: General Help
---

### Post by GrendelS on 2009-12-21
Hello,
I have a Samsung 1860 X20 laptop with ATI X700 running at 1400x1050. The install gives me several problems upon install:

"Das Panel ist beim Laden von >>OAFIID:GNOME_NotificationAreaApplet<< auf ein Problem gestoßen." meaning that the panel couldn't be loaded and it's asking me whether I want to delete it from my configurtion. Do I? And what is it?

The same thing comes up for the OAFIID:GNOME_Panel_TrashApplet, OAFIID:GNOME_WindowListApplet and ShowDesktopApplet and another one I just clicked into Nirvana before looking at what it said. I installed U9.10 three times now, the problem persists every time.

The desktop looks sparse, I suppose there's a connection.

Anyway, I also don't see a way to configure wlan or look at the file system (I had two partitions, but can't even open the folder root for some reason). Shouldn't I be admin on install? I remember installing Ubuntu 7 oder 8 and having to choose all kinds of settings, among others a user name and password. If I log off, I can't login as there doesn't seem to be a user account except root without a password.

G.

---

### Post by dagarwal82 on 2009-12-21
Try creating a new user from shell (log as root in shell)

# useradd deepak
# passwd deepak 

then login to gui through deepak account (choose your own username)

---

