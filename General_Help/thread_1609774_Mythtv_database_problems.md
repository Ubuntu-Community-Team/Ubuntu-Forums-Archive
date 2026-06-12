---
title: "Mythtv database problems"
date: 2010-10-30
forum: General Help
---

### Post by Brasil on 2010-10-30
Hi all, I've been having some real issues with mythtv's database.
Recordedseek became corrupted and couldn't be fixed no matter what I tried, so I went in, truncated the table and rebuilt it with mythcommflag. I also did some myisamchk repairs on a couple of other tables (settings and eit_cache). Now myisamchk tells me all the tables are fine. But when I restart the database I'll get an error like:
 ERROR 126 (HY000) at line 1: Incorrect key file for table '/tmp/#sql_2506_0.MYI'; try to repair it

In terms of the effect, I have lost all my recordings. Listings seems fine (although it has crashed a couple of times, I think I've fixed whatever was wrong), recording schedules seems fine, but even though there is stuff due to record upcoming recordings is empty. Mysqlcheck isn't showing any problems, I'm at a loss as to where to go from here.

---

### Post by gslug79 on 2010-10-30
Hello, I don't have an answer for you, but you may get more responses if you post in the [Mythbuntu]("http://ubuntuforums.org/forumdisplay.php?f=301") forum.

Cheers,
Kevin

---

### Post by Brasil on 2010-10-31
> **gslug79 said:**
> Hello, I don't have an answer for you, but you may get more responses if you post in the [Mythbuntu]("http://ubuntuforums.org/forumdisplay.php?f=301") forum.

Cheers,
Kevin

Thank you very much Kevin. I'll try that.

---

