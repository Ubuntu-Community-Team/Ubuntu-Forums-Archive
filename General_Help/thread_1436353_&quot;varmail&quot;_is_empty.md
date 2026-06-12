---
title: "&quot;/var/mail/&quot; is empty"
date: 2010-03-22
forum: General Help
---

### Post by rhill on 2010-03-22
New to Linux.

According to this post, [http://ubuntuforums.org/archive/index.php/t-7321.html](http://ubuntuforums.org/archive/index.php/t-7321.html), there should be a file named "root" in "/var/mail/". However, when I look into "/var/mail/", there is nothing.

How do I setup a mailbox in order for root to receive mails from various system-wide tasks?

I am running Ubuntu Lucid Lynx Alpha 3 amd64 + all updates.

---

### Post by bobcollard on 2010-03-22
> **rhill said:**
> New to Linux.

According to this post, [http://ubuntuforums.org/archive/index.php/t-7321.html](http://ubuntuforums.org/archive/index.php/t-7321.html), there should be a file named "root" in "/var/mail/". However, when I look into "/var/mail/", there is nothing.

How do I setup a mailbox in order for root to receive mails from various system-wide tasks?

I am running Ubuntu Lucid Lynx Alpha 3 amd64 + all updates.
Read it again, it tells you how to set up the file in this part:
cd /var/mail
sudo cp root username
sudo chown username username
sudo chgrp username mail

---

### Post by rhill on 2010-03-23
> **bobcollard said:**
> Read it again, it tells you how to set up the file in this part:
cd /var/mail
sudo cp root username
sudo chown username username
sudo chgrp username mail

This tells me to copy "root" to [username], which is pointless if there is no "root" in the first place. My question was and still is, why is there no "root" in this particular folder, and how is it first created.

---

### Post by dcstar on 2010-03-23
> **rhill said:**
> New to Linux.

According to this post, [http://ubuntuforums.org/archive/index.php/t-7321.html](http://ubuntuforums.org/archive/index.php/t-7321.html), there should be a file named "root" in "/var/mail/". However, when I look into "/var/mail/", there is nothing.

How do I setup a mailbox in order for root to receive mails from various system-wide tasks?

I am running Ubuntu Lucid Lynx Alpha 3 amd64 + all updates.

[LIST=1]
[*]There is only a file called "root" in there if there is a mail message for root.
[*]You are using a development release of Ubuntu, **all** questions are only to be posted in the development forum.
[/LIST]

---

### Post by rhill on 2010-03-23
> **dcstar said:**
> 
There is only a file called "root" in there if there is a mail message for root.


Ah I see, thanks, this makes sense now.

> **dcstar said:**
> 
You  are using a development release of Ubuntu, **all** questions are  only to be posted in the development forum.


Sorry, I wasn't aware of that rule. Hope they won't mind such naive questions over there :?.

---

