---
title: "Screensaver/password problem"
date: 2006-02-09
forum: General Help
---

### Post by QettoE on 2006-02-09
Hey everyone.

I have a rather weird problem. Everytime my screensaver starts it locks my screen (what I wanted), but it doesn't let me back in with the password I provide so I have to ssh to it and reboot it. I only have one user and one password on this machine.

Also, I can't find the option where I can alter my screen shut off time.

Thank you in advance,

---

### Post by flight_master on 2006-02-09
Hi,

>  Also, I can't find the option where I can alter my screen shut off time.

Right-Click on your desktop -> Configure Desktop -> Display -> Power Control 


Can you login with the password that you set? Perhaps you are using a non-standard character?

Regards,
Christian

---

### Post by QettoE on 2006-02-09
[QUOTE=flight_master]Hi,



Right-Click on your desktop -> Configure Desktop -> Display -> Power Control 


Can you login with the password that you set?

Regards,
Christian[/QUOTE]

Chars are all numbers... Does that power control shut the computer dows or just the display?

---

### Post by QettoE on 2006-02-09
[QUOTE=flight_master]Hi,



Right-Click on your desktop -> Configure Desktop -> Display -> Power Control 


Can you login with the password that you set? Perhaps you are using a non-standard character?

Regards,
Christian[/QUOTE]

Chars are all numbers...

---

### Post by QettoE on 2006-02-09
One of my friends suggested this:

```

chown root.root `which kcheckpass`
chmod 4755 `which kcheckpass`

```

Everything seems to be fine now.

---

