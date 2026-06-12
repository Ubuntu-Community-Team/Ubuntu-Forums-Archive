---
title: "black screen after logout"
date: 2011-12-09
forum: General Help
---

### Post by Tex-Twil on 2011-12-09
Hi,
I have a clean installation of Kubuntu 11.10 and when I log out my user I just see a black screen instead of seeing the login window. I have to open a new tty and "sudo service kdm restart" to see the login manager again.

What's wrong ?

cheers,

---

### Post by rickarino on 2011-12-09
Ditto.  

I've been using Control-Alt-F1 to get to a console login.  Logging in there, then issuing "sudo service kdm restart" to get the GUI back.  (Press Control-Alt-F7 to get back to the GUI)

I did note that there is a login displayed (kgreet is running after logout), and one can log in (assuming one can find the fields), but even after the stealth login, the screen stays black.

---

### Post by Tex-Twil on 2011-12-13
> **rickarino said:**
> Ditto.  

I've been using Control-Alt-F1 to get to a console login.  Logging in there, then issuing "sudo service kdm restart" to get the GUI back.  (Press Control-Alt-F7 to get back to the GUI)

I did note that there is a login displayed (kgreet is running after logout), and one can log in (assuming one can find the fields), but even after the stealth login, the screen stays black.

yep, it's pretty annoying.

---

