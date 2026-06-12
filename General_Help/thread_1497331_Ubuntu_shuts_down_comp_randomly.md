---
title: "Ubuntu shuts down comp randomly"
date: 2010-05-30
forum: General Help
---

### Post by GeneralTor on 2010-05-30
Ubuntu keeps shutting down my comp randomly for no reason at all. It doesn't even display any message, it just goes down without warning.

I'm sure it's not a heat issue. My computer never gets very hot and even when it does it still is very reliable.

Can someone please help me fix this? I'm very new to Ubuntu so i'm sorry if this question has already been answered somewhere else.

---

### Post by dino99 on 2010-05-30
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

looks at errors into:

- .xsession-errors into /home (unhide it with menu)
- system/admin/log viewer  (menu)

check your video driver: system/admin/hardware driver, is yours activated ?

---

### Post by GeneralTor on 2010-05-30
I tried that but it didn't work.

I don't think it could be a driver problem either.

---

