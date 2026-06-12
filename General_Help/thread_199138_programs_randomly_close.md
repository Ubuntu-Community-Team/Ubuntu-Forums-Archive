---
title: "programs randomly close"
date: 2006-06-18
forum: General Help
---

### Post by moore.bryan on 2006-06-18
i started out with only swiftfox/firefox hit by this problem, now other programs are suddenly closing while i am working in them.  anyone else with this problem or any ideas?

---

### Post by AndrewB on 2006-06-18
How much ram is in your computer? You need a comfortable minimum of 256mb to run, imo.

---

### Post by Ramses de Norre on 2006-06-18
Hmm not enough ram shouldn't cause programs to just crash, but broken ram can, have you ran a memtest already? (it's in the grub menu)
Firefox closes here sometimes too, it just disappears but I can start it up again without any problem, it's the only app with the problem here though.

---

### Post by moore.bryan on 2006-06-18
i just ran memtest and everything passed... yesterday, OOo just closed and i had to recover.

---

### Post by Ramses de Norre on 2006-06-18
Hmm I'd search in the logs but I'm not sure which ones to look into first..

---

### Post by moore.bryan on 2006-06-25
in /etc/log ?

---

### Post by moore.bryan on 2006-07-04
dmesg shows nothing weird...

---

### Post by taurus on 2006-07-04
Your log files should be in /var/log...  Look in /var/log/messages.

---

