---
title: "motd permission problem"
date: 2010-02-12
forum: General Help
---

### Post by mtphr on 2010-02-12
hi.
i want the motd to update every 30 mins with random lines from a file, with crontab. but the problem is, i can't write to motd cuz of permission problems.

say i have a file /home/mtphr/motd_list

$ shuf -n1 /home/mtphr/motd_list > /etc/motd
says Permission denied.

when i sudo the same command, i still get permission denied?

but (with root previlages) i can edit /etc/motd , how come i can't redirect shuf's output?

---

### Post by gordintoronto on 2010-02-12
On my system, etc/motd is not a file, it's a link.  The actual file is /var/run/motd

---

### Post by mtphr on 2010-02-14
yeah you're right. same here. but it doesn't matter. still permission denied...

---

