---
title: "GUI login complications"
date: 2010-03-22
forum: General Help
---

### Post by caanderson555 on 2010-03-22
I recently installed lucid on my new laptop (Thinkpad T410, since had some problems installing Karmic).  Originally ran great, yet after several days lost the ability to log on as adminstrator using the login screen.  After several seconds, it just sends me right back to the same screen. However, at the same time, I have no problem loging on as a different user via this screen.  I'm also able to login no problem using the command line.  I can toggle between this command screen and the visual user account, so can run what I need in root and then transfer to the user account so I can view it.

I really have no idea why one account would provide no problem logging in, while the other remains fine.  Not sure if it's a driver problem or what..  Kinda new to linux fyi.

Any help would be much appreciated!
let me know if you need any more information


Casey

---

### Post by dragos240 on 2010-03-22
> **caanderson555 said:**
> I recently installed lucid on my new laptop (Thinkpad T410, since had some problems installing Karmic).  Originally ran great, yet after several days lost the ability to log on as adminstrator using the login screen.  After several seconds, it just sends me right back to the same screen. However, at the same time, I have no problem loging on as a different user via this screen.  I'm also able to login no problem using the command line.  I can toggle between this command screen and the visual user account, so can run what I need in root and then transfer to the user account so I can view it.

I really have no idea why one account would provide no problem logging in, while the other remains fine.  Not sure if it's a driver problem or what..  Kinda new to linux fyi.

Any help would be much appreciated!
let me know if you need any more information


Casey

An admin login? Are you using the normal ubuntu? If so, the login manager in GNOME (gdm) by default, prohibits root login, you need to enable this feature manually, also make sure you have set your root password as well (I assume you have). Also, logging in as root is a VERY BAD idea, I suggest running individual programs as root, and only as needed.

EDIT: Also, ubuntu should have it's configuration file for gdm in /etc/gdm/gdm.conf (not 100% sure though.)
Try adding "AllowRoot=true" in the file, without quotes.

---

### Post by caanderson555 on 2010-03-22
Sorry for making it sound confusing, but what I meant was I was unable to login to my normal user account.  I do not login as root, but the account profile that allows me to access root.

---

### Post by dragos240 on 2010-03-22
> **caanderson555 said:**
> Sorry for making it sound confusing, but what I meant was I was unable to login to my normal user account.  I do not login as root, but the account profile that allows me to access root.

Ah, well lucid will not be officially released until April. Bugs are expected, I've never heard this one before. Ummm...... try logging in via a tty terminal. Write this down:

Login as your user account. (In the tty terminal, accessed by doing ctrl + alt + F1)
startx

You will not be able to mount drives, but you should be able to at least login.

---

