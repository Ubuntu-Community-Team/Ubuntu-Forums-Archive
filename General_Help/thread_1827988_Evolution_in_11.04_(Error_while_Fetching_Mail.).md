---
title: "Evolution in 11.04 (Error while Fetching Mail.)"
date: 2011-08-18
forum: General Help
---

### Post by baiki on 2011-08-18
Hello,

Bit of a background. Two weeks ago I installed Ubuntu 11.04 64bit and used Evolution as mail client. Worked fine for a while till I couldn't sync my mails anymore. Error message: "Error while Fetching Mail. Connection timed out"
5 minutes later I installed ThunderBird. Worked like a charm. It's hard to change to TB because I use Evolution since 2-3 years and never had one problem. OK, however I wiped the disk on my computer again and installed Ubuntu 11.04 32bit. I restored my Evolution backup (really nice feature) and was happy... for only two days. Same problem again. Guess what, I installed TB again... my POP3 does work but Evolution can not get or send mails again. It seems it is not the Internetline since TB works like a charm. If I click Send/Receive nothing happens on my Internet line. Looks like Evolution 2.32.2 is even not trying to do a thing. 

What can I do?

---

### Post by strider22 on 2011-08-21
I can confirm the problem. I get error "failed at message 1/xx"
Evolution downloads the pop summary... the total number of unread messages goes up properly.
I can send.

I have verified my settings on Yahoo and Evolution. No changes made permanently just saved but it still fails to retrieve.

I also deleted about a thousand old emails in case it was a space issue. Still no. Reboots have no effect.

My problems started on 2011.08.20 (possibly 19) Because 19 is one month from the forced user interface upgrade I allowed the upgrade but still no.

---

### Post by asasoft on 2011-09-04
I see this in lucid too.

---

### Post by baiki on 2011-09-04
Hello again,

Well, finally I figured why my Evolution was "silent". I changed in Chrome (Web browser) the proxy server settings. Once I deactivated those settings again (Direct Internet connection), Evolution was able again to sync mails properly.

Cheers

---

### Post by asasoft on 2011-09-05
Two diferents problems here, yours @[baiki]("http://ubuntuforums.org/member.php?u=294914") solved, others and me seems to be related to evolution and yahoo pop mail. Maybe some authority certificate problem?

---

