---
title: "Unable to safely disabling/removing ARCHIVES in Thunderbird"
date: 2012-10-06
forum: General Help
---

### Post by manolomanolo on 2012-10-06
Hi to all,
I'm experiencing quota problems with my GoogleApps email account configured as IMAP on Thunderbird. Let's call it X-OLD account. In brief, X-OLD account is about to reach the quota limit (10.1 GB) but I'm not able to make room. Please read the following detail. Thanks.

**PREFACE**
I access to my X-OLD email account through Thunderbird (IMAP) on my Kubuntu. The quota limit mostly rests around 96% (actually varying between 96% and 97%) despite I have been moving/removing tons (yes, tons!!!) of mails, with and without attachments.
In detail, a huge quantity of emails have been removed, other huge quantity has been moved to another (almost new and empty) GoogleApps email account, also configured as IMAP on Thunderbird. let's call it Y-NEW. It is curious to note that because of the folder-moving operation the Y-NEW account passed from almost 1% full to around 35% full... while the X-OLD account has not decreased by the same percentage, sometimes even increased its filled quota percentage.

So, I thought that a good idea was removing/disabling that annoying "Archives" folder created by Thunderbird automatically, because despite i go on moving/removing emails from my Inbox folders, the Archives folder still contains the moved/removed emails. That makes me think that actually the Archives folder prevents emails being really removed on the server. At the moment, that seems to be the only cause for the quota problem.

**MY PROBLEM**
However, my problem is (as stated on the object of this thread) that I cannot safely disabling/removing this folder/function. As far as I can see, this folder/function is automatically created by TB and it contains all sort of emails (Inbox, outbox, drafts, trashed) and it is huge space consuming.
Examples of behaviour of the function/folder. Suppose you have an email both stored into Inbox and Archives:
[LIST]removing that email from Inbox **does not** remove it from Archives[/LIST]
[LIST]removing a mail from Archives **does** remove it from Inbox[/LIST]

What can I do?
Thanks.

Kubuntu 12.04
Thunderbird 15.0.1


PD: thunderbird support does not reply :( The same problem has been also reported there
[https://getsatisfaction.com/mozilla_messaging/topics/unable_to_safely_disabling_removing_archives_in_thunderbird?rfm=1]("https://getsatisfaction.com/mozilla_messaging/topics/unable_to_safely_disabling_removing_archives_in_thunderbird?rfm=1")
[http://forums.mozillazine.org/viewtopic.php?f=31&t=2566277]("http://forums.mozillazine.org/viewtopic.php?f=31&t=2566277")

---

