---
title: "runlevels and scripts? - cli login to automatic gui session"
date: 2010-10-28
forum: General Help
---

### Post by Zahlerstreik on 2010-10-28
I haven't posted in a long time so forgive me if I do something wrong. I want to consult with you guys before I take any steps that might mess up my system. 


I'm looking to modify my current Maverick 64 bit system to boot to a multi-user CLI login, and once the user logs in, have it launch a gnome session as if you had logged in from the standard gui login screen. 

I searched and read this thread [http://ubuntuforums.org/showthread.php?t=89491]("http://ubuntuforums.org/showthread.php?t=89491")

The first step seems to be to disable gdm on all runlevels. It normally starts on 2,3,4,and 5. If I understand correctly, this will cause the system to boot completely normally (with all other services running like normal) excepting gdm, thus booting to a console login.

That's pretty much where I get lost, as I really have no linux experience. How do i make an uncontested script to start my default gnome session?

Any help would be greatly appreciated. Thanks! -Z

---

### Post by sisco311 on 2010-10-28
That's an old thread, see this one: [thread]1607830[/thread]

Run:```
startx
```to start the GUI session.

---

