---
title: "Evolution Tasks quit unexpectedly"
date: 2011-07-27
forum: General Help
---

### Post by mobius129a on 2011-07-27
Hi,

I'm having problems with Tasks in Evolution. Sometimes (not all the time), when I double-click on a task to edits its description, I get the following:

> The Evolution Tasks have quit unexpectedly. Your tasks will not be available until Evolution is restarted.Restarting does not necessarily solve the problem. I can't definitively say that there is any thing that may be co-occurring with this phenomenon. 

TIA.

---

### Post by mobius129a on 2011-07-28
Bump

---

### Post by bakegoodz on 2011-07-28
Are you connecting to a Exchange 2007 or higher server? If so Evolution uses Samba 4's Active Directory support which is still pretty experimental. Though its Exchange 2007 support get better with every version, it has problems only occasionally for me, though I just use mail and calendar.

---

### Post by mobius129a on 2011-07-30
No, I don't think so. My tasks are all stored locally and not on a remote server. How can I check?

---

### Post by mobius129a on 2011-11-26
Just in case anybody has experienced this issue, from what I can understand the reason for this phenomenon has something to do with the polling of relevant imap servers by the email client. This polling probably causes some sort of conflict with access to Tasks. My reasoning for this comes from the fact that I have reduced the ***Check for new mail*** time to about 30 minutes for all my accounts, which is okay for me. The result is that I haven't any >  The Evolution Tasks have quit unexpectedly. Your tasks will not be available until Evolution is restarted.                       incidences lately.

I probably won't file this as a bug unless somebody else can replicate the issue (I may after all be doing something wrong).

---

### Post by dcstar on 2011-11-26
> **mobius129a said:**
> Just in case anybody has experienced this issue, from what I can understand the reason for this phenomenon has something to do with the polling of relevant imap servers by the email client. This polling probably causes some sort of conflict with access to Tasks. My reasoning for this comes from the fact that I have reduced the ***Check for new mail*** time to about 30 minutes for all my accounts, which is okay for me. The result is that I haven't any  incidences lately.

I probably won't file this as a bug unless somebody else can replicate the issue (I may after all be doing something wrong).

Quite possible that there is a database locking bug when both functions are run at the same time, but the 10.04 version of Evolution is way out of date now and unless it also occurs in the current version I doubt that the Evolution maintainers would take action on it even if you put in a bug report.

If you want to try it on a 11.10 system and it still occurs then it would certainly be worth putting in a bug report.

---

### Post by mobius129a on 2011-11-27
@dcstar: you're right. I tried it on an 11.04 with a Check for new mail time of 5 minutes and there was no problem; it was evolution version 3.x.x. The version I was using on 10.04 was evolution 2.28.3. It must have been sorted out.

---

