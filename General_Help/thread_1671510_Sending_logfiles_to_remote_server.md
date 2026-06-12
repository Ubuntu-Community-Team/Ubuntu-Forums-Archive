---
title: "Sending logfiles to remote server"
date: 2011-01-20
forum: General Help
---

### Post by woot06 on 2011-01-20
My central log collector A for various devices is running on ubuntu 9.10. I want to:

1) Configure logfiles to be sent to remote server B via A's syslog server
2) Make it a cronjob that runs at prescribed time

But problem is, I am not sure how to do (1). The files are located in /logs/server/xxxx.log and /logs/network/zzzz.log

Any reference is much appreciated!

---

### Post by ysangkok on 2011-05-19
You can use "scp". It will work if the receiving server has an SSH server running. You need to any authentication method other than passphrase.

---

