---
title: "Time zone problem"
date: 2010-02-28
forum: General Help
---

### Post by hbquikcomjamesl on 2010-02-28
I have a problem, one that I don't remember seeing on RH8:

The battery-backed-up system clock on my dual-boot has, as I write this, the same thing my watch shows: 12:39 P.M.

DOS treats this correctly, i.e., as local time (Pacific Standard Time).

Ubuntu is treating it as GMT, and is accordingly subtracting 8 hours from it.

I can hardly be expected to change the battery-backed-up system clock every time I switch operating systems; that would defeat the whole purpose of having a battery backed-up system clock!

Obviously, I could tell Linux to assume it's physically in Greenwich, but that would make a mess of, for example, email timestamp processing.

How do I tell Linux to treat the battery-backed-up system clock as local time, while still properly handling timestamps out in the rest of the world?

---

### Post by Revolutionary101 on 2010-02-28
Only way I know how to change the time zone (I know this may not be what you are asking for) is by going to System>Administration>Time and Date.

If you change the time zone here it will have Ubuntu display the right time but I don't know if it will solve your e-mail problem.

---

### Post by hbquikcomjamesl on 2010-02-28
That would solve the immediate problem, but it would *cause* the email problem to which I alluded, and possibly other problems dealing with the outside world.

Then again, I have no immediate plans to run an email reader on that box: when my email actually gets downloaded, it goes to my iMac. If I'm accessing my email from elsewhere, I do so through a web-mail interface, so I could be swatting at an imaginary fly, depending on whether there are other "outside world" issues that could occur.

---

### Post by asmoore82 on 2010-02-28
I know there is an easy fix for this,
waaay back in my RedHat days there was a checkbox somewhere for
"System clock uses local time."

---

### Post by asmoore82 on 2010-02-28
got it!

edit "/etc/default/rcS" and change "UTC=yes" to "UTC=no"

```
gksudo gedit "/etc/default/rcS"
```

"/etc/default" was the first place I looked because I knew that was the proper
Debian/Ubuntu style place, but none of the filenames jumped out at me, so I...
```
grep -i utc *
```

---

### Post by hbquikcomjamesl on 2010-02-28
That did it. Thanks.

---

