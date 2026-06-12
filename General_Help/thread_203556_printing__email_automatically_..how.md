---
title: "printing  email automatically ..how???"
date: 2006-06-25
forum: General Help
---

### Post by bulldog885 on 2006-06-25
Hi,
I'm trying to figure out how I can print an email automatically that comes in and direct it to an IPP printer. For example, I want linux to grab from an account and print the weather email automatically with no human interaction. Any ideas?? thanks in advance.

---

### Post by scxtt on 2006-06-25
make a cron job? -- have it check /var/mail/$user every 10 minutes (or if you know when the email comes out, use that time) and then have it print the contents ... this would only work if your box can receive outside email to user accounts and you'd probably not want to print the headers (not hard to do) ...

---

### Post by dcstar on 2006-06-26
[QUOTE=bulldog885]Hi,
I'm trying to figure out how I can print an email automatically that comes in and direct it to an IPP printer. For example, I want linux to grab from an account and print the weather email automatically with no human interaction. Any ideas?? thanks in advance.[/QUOTE]
In Evolution you can set up a Filter to pipe an e-mail to an external program, so you may be able to set up something with that.

There may be a solution just a web search away.......

---

### Post by bulldog885 on 2006-06-26
Thanks for the replies... I have been looking at the posts on the web, I'm going to try a special feature of the network printer it see if it can handle the email itself.

---

