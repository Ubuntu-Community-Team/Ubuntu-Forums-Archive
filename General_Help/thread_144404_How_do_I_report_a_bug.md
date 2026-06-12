---
title: "How do I report a bug?"
date: 2006-03-14
forum: General Help
---

### Post by mvaniersel on 2006-03-14
Ok, this is probably a stupid question, but what is the procedure for reporting bugs? 

I found this: [https://wiki.ubuntu.com/ReportingBugs?action=show&redirect=BugReports](https://wiki.ubuntu.com/ReportingBugs?action=show&redirect=BugReports) and this: [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

But what it doesn't tell me:

Does it make sense to report bugs for Breezy or only for Dapper?
Can I expect a response?
Does adding comments help getting the bug fixed?
When is a bug a bug in ubuntu and when is it a bug in the application itself?

---

### Post by Xian on 2006-03-14
[QUOTE=mvaniersel]Does it make sense to report bugs for Breezy or only for Dapper?[/quote]

Both, since each are currently and officially supported.

> Can I expect a response?

That depends. Some bugs do not require a verbose response.

> Does adding comments help getting the bug fixed?

Yes. The more you can explain about the problem the better.

> When is a bug a bug in ubuntu and when is it a bug in the application itself?

If it is an official ubuntu package (from the main repositories) then you should generally file the bug with Ubuntu, and then let the devs determine if the issue needs to be sent upstream.

---

### Post by az on 2006-03-14
[QUOTE=mvaniersel]
Does it make sense to report bugs for Breezy or only for Dapper?
Can I expect a response?
Does adding comments help getting the bug fixed?
When is a bug a bug in ubuntu and when is it a bug in the application itself?[/QUOTE]

Good questions!

If you are running breezy and find a bug, you don't need to install Dapper to see if it's fixed.  Just look first to see if the problem has already been reported.  If the fix also applies to breezy, you may have to ask for it to be done sometimes.

Yes, you should get a response.

You need to report your bug in a way that is compelling and accurate.  For exapmple, avoid useless comments like saying that you think this bug should be fixed before release - that is often not under the control of the person who will respond to you.

Launchpad is working on great technology so that not only the bugs get reported upstream, but the fixes too!  Stay tuned!  (You report a bug in ubuntu and the fix goes to slackware, redhat, mandriva, etc... as well as ubuntu)

---

### Post by mvaniersel on 2006-03-15
Thanks for the answers

> 
Launchpad is working on great technology so that not only the bugs get reported upstream, but the fixes too! Stay tuned! (You report a bug in ubuntu and the fix goes to slackware, redhat, mandriva, etc... as well as ubuntu)

sounds like that is very complicated in practice.

This is the bug in question: [https://launchpad.net/distros/ubuntu/+source/util-linux/+bug/27714](https://launchpad.net/distros/ubuntu/+source/util-linux/+bug/27714). It's a problem with the R statistical package.

I've only added a comment, perhaps a bit light but the original report really says it all, the bug just seems to be neglected. It says it is still unconfirmed. I'm going to post to the R mailinglist now to see if they can shed some light on this.

---

