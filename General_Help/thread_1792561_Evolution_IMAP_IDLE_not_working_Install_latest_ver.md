---
title: "Evolution IMAP IDLE not working? Install latest version?"
date: 2011-06-28
forum: General Help
---

### Post by dpatel on 2011-06-28
Hi All -

I am using Ubuntu 10.04.

I always liked Evolution as a potential email client. But one issue that I needed was for Evolution to automatically update the server (so if I mark a message as unread, it reflects at the server without having to wait for the 'synchronise every X minutes' to kick in).

My email is with GMail.

I understand Evolution implemented IMAP IDLE as of 2.30. So I tried this by using a PPA (ppa:jacob/evo230) to update. The update worked and I changed my email to IMAP+ and even checked the “Use idle if the server supports it”. But no auto sync occurs!

Any ideas? Or can someone give me some detailed instructions of how to get the latest version of Evolution on to by Ubuntu 10.04?

Thanks!!

---

### Post by mcduck on 2011-06-28
I don't really think IMAP IDLE is the feature you are looking for, as that works for the *other direction* (telling the server that it can send mail to client at any time instead of waiting for the client to sync).

Perhaps the "Quick Resync" option does what you want?

---

### Post by dpatel on 2011-06-28
I don't remember seeing quick sync. Is that in newer versions only? I'm using 2.28.

---

### Post by mcduck on 2011-06-28
It should appear in Receiving Options, right above the IDLE option, when receiving server type is set to IMAP+.

Of course it's possible it's not there on older versions, I'm using 2.32.2 (as that's what comes with Ubuntu 11.04).

---

