---
title: "Sync Evolution mailbox with laptop"
date: 2006-06-19
forum: General Help
---

### Post by Enigmatic on 2006-06-19
I know that Evolution has built in support for PDAs and PPCs, but is there an easy way to sync my mailbox between my desktop and laptop?

---

### Post by Enigmatic on 2006-06-20
Would it work to have a cron job run everytime the laptop started on my network to rsync with my mboxes on the desktop? Since it is incremental, I think it would work fairly well, or am I wrong?

---

### Post by stimpsonjcat on 2006-06-20
I think that your solution will work. you could also use unison, which is two-way so it doesn't matter on which computer you download your mail first (and it has a GUI interface, unison-gtk). I used to do it that way with kmail some time ago. let us know how it went.

---

### Post by Enigmatic on 2006-06-30
Neat, it works nicely! The only thing I'm wondering about is how to change the permissions of the synced files. The ones that are copied to the machine are all owned by root by default. Is there a parameter to set that I've overlooked?

---

### Post by Enigmatic on 2006-07-05
Does anyone know which files should be synced? I see ev-summary, .cmeta, .ibex.index and .ibex.data. I also see some with no extension.

---

