---
title: "lock accounts after few login attempts (PAM,faillog)"
date: 2011-03-06
forum: General Help
---

### Post by zerothink on 2011-03-06
Hi,

I am using ubuntu 10.10. I would like to configure ubuntu authentication so that after few unsuccessful attempts the account gets disabled. By authentication I mean GDM login, console login, locked screen login, sudo, su. Even better would be if I can disable this rule for root account.

Rationale: I am using full disk encryption, and I enabled root password with really hard password as a last resort. If I can get this this disabling to work I can use very short user password and still have higher real-world security than without it using middle-sized user password.

I thought this is quite simple change of PAM configuration, I googled few threads and howtos like [1)]("http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/"),[2)]("http://www.linuxquestions.org/questions/linux-security-4/pam-pam_tally-and-locking-out-users-after-3-failed-login-attempts-in-rhel5-624257/"), [3)]("http://swik.net/Ubuntu/Planet+Ubuntu/Bodhi.Zazen:+Ubuntu+how+to+faillog/d078x"), [4)]("http://ubuntuforums.org/showthread.php?t=1024263") but they does not work for me.

I suppose I am not first one trying to achieve this - if am I right, could someone please post which changes to PAM configuration are necessary ?

---

