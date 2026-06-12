---
title: "shell scripts - updatedb -    locate"
date: 2010-04-11
forum: General Help
---

### Post by Silvernail on 2010-04-11
I have some shell scripts that I am sourcing and putting in /usr/bin.
What do I  need to do to get them recognized by 'updatedb'   with a description of what they do that 'locate' 'apropos' can display?
TIA
Dave

---

### Post by Silvernail on 2010-04-16
Is there a better thread to place this question in?  Some one has to know the answer to this.

---

### Post by gmargo on 2010-04-17
I'm confused by your question - locate and apropos are not related, except in the sense that they both work from databases created by another tool run periodically by cron.

**locate(1)** uses the database created by **updatedb( 8 )**, updated daily by the cron script /etc/cron.daily/mlocate.

**apropos(1)** uses the database created by **mandb( 8 )**, updated daily by the cron script /etc/cron.daily/man-db (also updated weekly.)

If you want **apropos(1)** to display something about your shell scripts, then you need to provide man pages for those shell scripts.

---

### Post by Silvernail on 2010-04-17
This is the information I was seeking. I now know what I need to do. I think.

Thanks

---

