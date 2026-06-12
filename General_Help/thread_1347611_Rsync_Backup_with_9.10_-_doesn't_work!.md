---
title: "Rsync Backup with 9.10 - doesn't work!"
date: 2009-12-06
forum: General Help
---

### Post by Quarkrad on 2009-12-06
I use to have (on Ubuntu 9.04) a very useful backup script that run so certain folders were backed up when I shut down my PC.  I had an rsync script in etc/init.d/ that I amended with the command **sudo update-rc.d script.sh start 03 0 6 .**  I have now migrated (with a clean install) to 9.10 and set up rsync the same as before - now when I run the sudo update ... command above I get [B]update-rc.d: warning: /etc/init.d/gadmin-rsync-backup.sh missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>[/B]
I have looked at the wiki but as a newbie it is difficult to see the wood for the trees.  How can I get this to work?

---

### Post by Quarkrad on 2009-12-06
any help?

---

### Post by pbrane on 2009-12-06
Not sure how you're using rsync. I have a script to backup my home directory using rsync and it works fine on 9.10. When I run **lsb_release** I get *No LSB modules are available.*. I'm not sure why you get that error. But rsync does work.

Kinda sounds like the init script policy has changed since 9.04. Have you read [http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts) ?

---

### Post by Quarkrad on 2009-12-07
Thanks for the reply.  Actually I owe you an apology.  I read through the link you sent me and decided to do simple test before I got 'stuck in'.  The same message can up re the script but I carried on and restarted my PC.  It worked ..... despite the message.  The message is 9.10 specific but it seems not effect the running of the scripts -once again, thanks.

---

### Post by eumetaxas on 2009-12-07
why don't toy try Grsyn - a qui for rsync?
works perfectly for me under karmic. 
If you are a newbie will take off the cmdline stuff

---

