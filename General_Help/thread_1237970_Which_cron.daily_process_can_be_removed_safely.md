---
title: "Which cron.daily process can be removed safely?"
date: 2009-08-12
forum: General Help
---

### Post by Tuvok41 on 2009-08-12
I am trying to clean up the cron.daily process as I think I do have too many. Could anyone tell me which of those I could remove safely and which I should keep and also if any that are present should not be there at all?
[LIST]
[*]0anacron
[*]apt
[*]debtags
[*]logrotate
[*]samba
[*]tripwire
[*]5snort
[*]aptitude
[*]exim4-base
[*]man-db
[*]slocate
[*]apache2
[*]bsdmainutils
[*]find
[*]mlocate
[*]standard
[*]apport
[*]chkrootkit
[*]find.notslocate.dpkg-new
[*]rkhunter
[*]sysklogd
[/LIST]

I have removed samba server is it normal it is still running samba daily?
I never use locate, I read this we could remove safely, what about the rest?
Thanks in advance for the help.

---

### Post by fluffman86 on 2009-08-12
you can remove apache2 unless you're running your own webserver.

---

### Post by Tuvok41 on 2009-08-12
Thx for the response but although my server is not running, I intend to set it up real soon. I guess I could put it inside cron.monthly until I do start it.

Anything else?

---

### Post by Tuvok41 on 2009-08-12
Since I am not using locate and hardly ever using search, how do I move the files from cron.daily to cron.monthly within the terminal. I have never had to move files yet with the terminal and I dont know the commands?

---

### Post by Tuvok41 on 2009-08-14
Can anyone help me? Please...

---

### Post by Tuvok41 on 2009-08-16
Please, pretty please, help someone?

---

### Post by Tuvok41 on 2009-08-18
> **Tuvok41 said:**
> Please, pretty please, help someone?
Is there anyone willing to give a hand?

---

