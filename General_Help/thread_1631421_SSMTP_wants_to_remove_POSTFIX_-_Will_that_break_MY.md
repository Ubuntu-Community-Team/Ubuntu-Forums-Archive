---
title: "SSMTP wants to remove POSTFIX - Will that break MYSQL?"
date: 2010-11-26
forum: General Help
---

### Post by bluelamp999 on 2010-11-26
Hello friends,

I want to install SSMTP to (hopefully!) simplify sending MDADM notifications via Gmail.

On issuing the command...

```
sudo apt-get install ssmtp
```

I'm informed that...

```
The following packages will be REMOVED:
  postfix
The following NEW packages will be installed:
  ssmtp

```

However, I believe that MYSQL (which I need for my Squeezebox) depends on POSTFIX.

So can I install SSMTP without removing POSTFIX?

Will removing POSTFIX actually break MYSQL?

Any help gratefully received...

Thanks

BTW, this is on Ubuntu Server 10.10 64 bit

---

### Post by bluelamp999 on 2010-11-27
Ever so gentle... *bump*

---

### Post by gmargo on 2010-11-27
mysql does not depend on postfix.  You can test this on the command line by trying to remove it (the -s says just show what would happen):
```

aptitude -s -V purge postfix

```ssmtp should provide the same interfaces as postfix, since they are both marked as "Provides: mail-transport-agent". So it should be fine to let ssmtp replace postfix.

But the real question is why - why do you think postfix can't send something that ssmtp can?  Isn't it just configured to send through your ISP?

---

### Post by bluelamp999 on 2010-11-29
Firstly, many thanks for replying.

I'm at work right now so can't test the removal of postfix but I'll report back later on how I get on...

> **gmargo said:**
> But the real question is why - why do you think postfix can't send something that ssmtp can?  Isn't it just configured to send through your ISP?

The answer here is that I've read that postfix is (apparently) quite complicated to set up. sSMTP is (again, apparently!) much easier to configure.

I only want to use it to send out MDADM RAID notifications via Gmail's SMTP service from my NAS box running Ubuntu Server.

Thanks again...

---

### Post by bluelamp999 on 2010-11-29
I can confirm that removing postfix has no effect on MYSQL in 10.10 server.

sSMTP now working MDADM to send notifications - cool!

---

