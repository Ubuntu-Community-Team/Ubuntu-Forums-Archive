---
title: "Dansguardian not filtering https"
date: 2012-01-17
forum: General Help
---

### Post by RyanGT on 2012-01-17
To reduce the amount of time I waste on the internet, I would like to block [https://www.facebook.com](https://www.facebook.com) on my laptop.  I have facebook.com as a bannedsite in dansguardian, and the site is blocked as long as I don't put https in front of it.  It seems that dansguardian is not filtering https sites.  How do I fix this?

Thanks,

Ryan

---

### Post by SeijiSensei on 2012-01-17
Short answer, it can't.  [Longer answer here]("http://ubuntuforums.org/showpost.php?p=11618372&postcount=2").

The easiest way to disable a site is to add an entry in /etc/hosts that points the hostname to a non-working address or to the localhost address 127.0.0.1.

---

### Post by RyanGT on 2012-01-17
Thanks for your quick, clear, and accurate reply.  I have asked this question at least once before and I don't think I got a good answer.  I added these two lines to /etc/hosts and rebooted:

127.0.1.1	facebook.com
127.0.1.1	[www.facebook.com](www.facebook.com)

I don't know if I need both of them or not, but the solution is working perfectly.  I can still get to [https://mail.google.com](https://mail.google.com) and one other https site from my school, but facebook is shut down.

Thank you very much!

Ryan

---

