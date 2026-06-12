---
title: "Where does &quot;echo&quot; output from crontab job go?"
date: 2010-08-31
forum: General Help
---

### Post by pstein on 2010-08-31
Assume I start in a cronjob a batch script for user karl123.
This batch script contains some 
 
Echo "....."
 
statements.
 
Where does this output go?
I assume its a log file. Which logfile exactly?
 
Peter

---

### Post by Grenage on 2010-08-31
As far as I am aware, echo merely prints the text/variable to the screen, unless it's followed by another command that writes it to a file. Example:

```
echo PIE

echo PIE > log
```

---

### Post by limestone on 2010-08-31
As [Grenage]("http://ubuntuforums.org/member.php?u=263074") said. Echo just prints the string directley on the screen like print or cout.

---

### Post by gmargo on 2010-08-31
Output from a **cron** script is emailed to you, as detailed in the **cron** man page.  If you don't have a mail transfer agent installed, then it goes into the bit bucket.

Try this: watch your /var/log/syslog file when your script runs.  Here's the message I get on 10.04 Lucid without an MTA installed, which is cron attempting to email but failing: ".....CRON[pid]: (userid) MAIL (mailed 83 bytes of output but got status 0x0001#012)".

---

