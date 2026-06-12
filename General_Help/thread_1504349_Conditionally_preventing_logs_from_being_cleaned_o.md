---
title: "Conditionally preventing logs from being cleaned out."
date: 2010-06-07
forum: General Help
---

### Post by jwbrase on 2010-06-07
I'm trying to track down a rather annoying crash, and have noticed certain patterns in the log files associated with said crash. I've noticed that the system logs automatically clean themselves out at intervals of between 1 and 5 days, depending on the log. Is there any way to automatically prevent a log from being cleaned out if it contains certain messages (IE, an error that conforms to a given regexp), or to divert said messages to a log file that doesn't get cleaned out? I'd like to see if similar events to the crash in question are happening without causing any user-noticeable problems, but it's generally only the crash that reminds me to check the logs, and it generally happens between once every two weeks and once a month.

---

