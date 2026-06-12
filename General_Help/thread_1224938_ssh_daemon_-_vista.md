---
title: "ssh daemon - vista  ?"
date: 2009-07-28
forum: General Help
---

### Post by cbear on 2009-07-28
where can I find an ssh daemon to run on my vista machine ?  I want to write a script on my linux box to login to my vista machine once a week, run a few comamnds, then logout.  looks like vista does not support ssh native...and I don't want to use telnet for security reasons.

thanks !

---

### Post by JohnnySage50307 on 2009-07-28
Personally, I use PuTTY.  If you google-bomb "Putty download", you can find a free copy.  It's what the entire CS/ECE department recomends for ssh-ing into machines from Windows.

---

### Post by lykwydchykyn on 2009-07-28
I cannot be sure that it works on Vista in particular, but I've installed it on XP before using cygwin.  I believe if you google about a bit there is a very simple cut-down version that just installs openssh server and dependencies.

---

### Post by lykwydchykyn on 2009-07-28
> **JohnnySage50307 said:**
> Personally, I use PuTTY.  If you google-bomb "Putty download", you can find a free copy.  It's what the entire CS/ECE department recomends for ssh-ing into machines from Windows.

Putty is a client.  OP wants a server (daemon).

---

### Post by Hobgoblin on 2009-07-28
A quick Google for ssh server windows vista found me [this](http://www.dslreports.com/forum/remark,17481324).

---

### Post by cybergalvez on 2009-07-28
give cygwin a try, it works with XP, not sure how it will work with vista

---

### Post by t4thfavor on 2009-07-28
Cygwin was difficult under xp, I can only imagin it under Vista. Though, I did however get it to work, not well, but it did work.

It's been so long, I cannot remember what I didn't like about it, but I just know I didn't like it.

---

