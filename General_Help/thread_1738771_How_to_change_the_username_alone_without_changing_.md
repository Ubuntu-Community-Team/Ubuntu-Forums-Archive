---
title: "How to change the username alone without changing the settings?"
date: 2011-04-25
forum: General Help
---

### Post by karthick87 on 2011-04-25
I want to change the username of my system without changing anyother settings.How to acheive this task?

---

### Post by KegHead on 2011-04-25
Hi!

Do you have Ubuntu Tweak installed?

If so, it's very easy!

KegHead

---

### Post by karthick87 on 2011-04-25
I prefer the manual way rather than installing additional packages like **[COLOR=Red]ubuntu-tweak[/COLOR]**.

---

### Post by conradin on 2011-04-25
[http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/](http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/)

---

### Post by matt_symes on 2011-04-25
Hi

Edit your /etc/passwd file. I think that will do it as well as usermod. If i'm wrong someone will pipe up.

Kind regards

---

### Post by WorMzy on 2011-04-25
```
usermod -l [COLOR="DarkGreen"]<NEW USERNAME>[/COLOR] [COLOR="Blue"]<CURRENT USERNAME>[/COLOR]
```

Unfortunately, you can't do this while logged in. One way around this is to boot into single mode and drop to a root shell, then run the command. Alternatively, log into another users account (create a temporary user if necessary, and make sure they have sudo privileges), then run the command. You'll (probably) need to rename your home folder too.

```
mv /home/[COLOR="Blue"]<CURRENT USERNAME>[/COLOR] /home/[COLOR="DarkGreen"]<NEW USERNAME>[/COLOR]
```

Prepend "sudo" to both commands if you need to.

---

### Post by karthick87 on 2011-04-25
How to boot into single mode?

---

### Post by matt_symes on 2011-04-25
Hi

Boot into the recovery console from the grub menu.

Kind regards

---

### Post by WorMzy on 2011-04-25
If you don't usually see the grub menu, hold down shift (grub2) or Esc (grub legacy) immediately after your PC POSTs when you first turn it on.

---

