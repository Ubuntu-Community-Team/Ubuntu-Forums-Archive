---
title: "No login sound"
date: 2012-02-26
forum: General Help
---

### Post by louisgonick on 2012-02-26
I changed my login sound some time ago, now its gone. Nothing plays when I turn my machine on. Neither i hear sound while raising my volume up or down. 

I might have messed up the default sounds
How can I get them back?

---

### Post by Old_Grey_Wolf on 2012-02-26
What version of Ubuntu are you using? I assume 11.10 from your profile.

Look in  /usr/share/sounds/ubuntu/stereo to see if you have a file named desktop-login.ogg. If it is not there you will need to copy it from a Live CD/USB.

If the file is there then look at "startup applications" and make sure that "gnome login sound" is selected to run.

---

### Post by louisgonick on 2012-02-26
> **Old_Gray_Wolf said:**
> What version of Ubuntu are you using? I assume 11.10 from your profile.

yes.

---

### Post by Old_Grey_Wolf on 2012-02-26
> **louisgonick said:**
> yes.
I edited my post above.

---

### Post by Old_Grey_Wolf on 2012-02-26
louisgonick,

Did that suggestion work?

---

### Post by louisgonick on 2012-02-26
> **Old_Gray_Wolf said:**
> louisgonick,

Did that suggestion work?

The file must have been deleted, do you know where can I download the login sound? I tried looking in a Live Cd and couldn't find it

---

### Post by Old_Grey_Wolf on 2012-02-26
Did you boot from the Live CD and look in /usr/share/sounds/ubuntu/stereo?

You will not find the file if you only look at the CD's contents.

If the file is there then copy it to your hard disk.

---

