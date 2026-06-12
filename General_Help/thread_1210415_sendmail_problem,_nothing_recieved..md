---
title: "sendmail problem, nothing recieved."
date: 2009-07-11
forum: General Help
---

### Post by RobOrr on 2009-07-11
Hi all,
 I've been fiddling with sendmail, following the frequent posts about problems with it on the forum and trying to fix my LAMP setup. my home computer is currently being used as the server for php practice. I am not experienced with Apache or php. 

I have installed sendmail from the repository.
Here's the output of my mail log when I use the sendmail function:
```

Jul 11 17:14:59 rob-desktop sendmail[15683]: n6BGEPBk015683: from=rob, size=100, class=0, nrcpts=1, msgid=<200907111614.n6BGEPBk015683@rob-desktop.home>, relay=rob@localhost
Jul 11 17:14:59 rob-desktop sm-mta[15684]: n6BGExNm015684: from=<rob@rob-desktop.home>, size=325, class=0, nrcpts=1, msgid=<200907111614.n6BGEPBk015683@rob-desktop.home>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Jul 11 17:14:59 rob-desktop sendmail[15683]: n6BGEPBk015683: to=robgorr@googlemail.com, ctladdr=rob (1000/1000), delay=00:00:34, xdelay=00:00:00, mailer=relay, pri=30100, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (n6BGExNm015684 Message accepted for delivery)

```

As far as I can tell Message accepted for delivery means everything is good, however the mail address I'm sending to (a googlemail account) has nothing received, and nothing in the junk/spam folders.

Thanks for your time.

---

