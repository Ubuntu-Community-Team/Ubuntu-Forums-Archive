---
title: "Missing Log Entries"
date: 2010-09-20
forum: General Help
---

### Post by s0rc3r3r on 2010-09-20
Hello There

I am using UBUNTU Karmic Koala 9 .10 . Recently I have noticed certain errors with my LOG Files.

My Log files are just logging the events for that particular day.All the logs of the previous days are lost.

It happens to almost all categories of log.Every log just shows one particular days log.
I have not done any changes to any settings on this machine as Ubuntu on my laptop is very stable and totally hiccup free.
Previously, the log file viewer used to show logged information from over a week or so.but..now every other days log files just vanishes.

I am just concerned 

1)Is it because of any rogue script that is deleting the previous log files.
2)Has my machine is getting compromised in anyway as I am using it extensively for Internet.[ I have the normal Firewall enabled already]

With regard to this I have a few questions

1)Is it Ubuntu's default behavior?Does it back up the old log files everyday?

2)If it is not the way Ubuntu treats Log files.How can I correct this?

3)Does apt-get clean or apt-get autoclean delete log files?

:confused::confused:
I have searched Google for past 3 days for a possible solution to this problem without yielding much result.

Thanks in advance,

Ps:If this is not the correct section for this type of query please bear with me.

---

### Post by s0rc3r3r on 2010-09-20
bump
:(

---

### Post by s0rc3r3r on 2010-09-20
errr...
Bump...again!!:confused:

---

### Post by Gunman1982 on 2010-09-20
What logs are you talking about? If you are refering to those under /var/log they are normally packaged bei the syslog deamon. But afaik that should only happen when the files reach a specific size.

---

### Post by Rubi1200 on 2010-09-20
See here:
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

Scroll down to the section about log rotation.

---

### Post by s0rc3r3r on 2010-09-21
> **Rubi1200 said:**
> See here:
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

Scroll down to the section about log rotation.

Thank you! 
That was what I was looking for.

---

### Post by Rubi1200 on 2010-09-21
You are more than welcome :)

Please mark this thread Solved using the Thread Tools near the top of the page.

Thanks.

---

