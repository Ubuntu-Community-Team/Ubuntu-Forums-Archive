---
title: "Firefox Global menu"
date: 2011-10-16
forum: General Help
---

### Post by Soon2BeLegend on 2011-10-16
I am trying to install the firefox global menu extension so i can have the menu bar in the panel like in mac os x, but everytime i try to install it, it gives me an error saying "This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time." anyone know how i can get this installed?

---

### Post by Soon2BeLegend on 2011-10-17
Nobody knows?

---

### Post by hansdown on 2011-10-17
Hi, Soon2BeLegend.

Which version of ubuntu are you using?

---

### Post by Soon2BeLegend on 2011-10-17
Ubuntu 10.04 Lucid. Thanks!

---

### Post by hansdown on 2011-10-17
I still use 10.04, and love it.

You may need to upgrade firefox, from 3.6>4.0

To find your version, click the firefox "help" icon, and click "about firefox".

What version are you using?

---

### Post by Soon2BeLegend on 2011-10-17
I'm using the version 7.0.1

---

### Post by hansdown on 2011-10-17
Didn't see that coming.

Are you installing from synaptic?

---

### Post by Soon2BeLegend on 2011-10-17
no, ive tried installing from terminal and ive tried installing from ubuntu software center.

---

### Post by hansdown on 2011-10-18
Sorry for not being, altogether helpful.

Are you software sources correct?

system>administration>software sources.

The "main", should be checked.

Click reload.

See if that helps.

---

### Post by Soon2BeLegend on 2011-10-18
everything is checked, including the "main"

---

### Post by David006 on 2011-10-18
I am happily using Ubuntu 11.10 + FF 7.0.1, but with 'global menus' disabled (for FF).

When I updated to Ubuntu 11.10 (from 11.04), FF 7.0.1 was included AND had 'Global Menu Bar' 2.0.1 enabled.  It worked fine, but wasn't what I wanted.


Have you resolved this yet?

---

### Post by Frogs Hair on 2011-10-18
For the global menu bar integration extension to work you need the global menu installed .  There is a global menu PPA available for 10.04 and 10.10 (Gnome Panel)  and I used it , but it is not the same as the one in the current panel .

---

### Post by hansdown on 2011-10-18
Frogs Hair is correct.

The ppa is here.

[http://www.ubuntugeek.com/how-to-install-globalmenu-in-ubuntu-10-04lucid9-10karmic.html](http://www.ubuntugeek.com/how-to-install-globalmenu-in-ubuntu-10-04lucid9-10karmic.html)

[http://www.youtube.com/watch?v=MK2D5DZGVN0](http://www.youtube.com/watch?v=MK2D5DZGVN0)

---

### Post by Soon2BeLegend on 2011-10-20
I have global menu installed on my computer.

---

### Post by hansdown on 2011-10-20
Click the links in my last post, and install the ppa.

The video is very helpful.

---

### Post by Soon2BeLegend on 2011-10-20
i have done that before posting this. this applet doesnt work with firefox normally and im trying to install the extension that will let it work with firefox. but it is giving me an error as i described in my first post.

---

### Post by hansdown on 2011-10-20
I just installed global menu, from that ppa.

I notice, it has packages from,** main**, **universe**,** multiverse**, and **restricted**.

You may need to install

```
sudo apt-get install ubuntu-restricted-extras
```

---

