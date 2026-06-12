---
title: "Number lock"
date: 2009-12-30
forum: General Help
---

### Post by w1ll1am on 2009-12-30
I have just installed Ubuntu 9.10 and I use to have Ubuntu 9.04 and i had it set so Number lock was on during start up and now i can not get it to work in Ubuntu 9.10 i have numlockx installed and when i try to edit  /etc/gdm/Init/Default in command line i get this message.


** ERROR **: Failed to setresgid to `gdm'
aborting...
Aborted
initctl: Rejected send message, 1 matched rules; type="method_call", sender=":1.70" (uid=1000 pid=1952 comm="initctl) interface="com.ubuntu.Upstart0_6" member="EmitEvent" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

Or if i try to edit it I get this message

william@william-desktop:~$ edit  /etc/gdm/Init/Default
Warning: unknown mime-type for "/etc/gdm/Init/Default" -- using "application/octet-stream"
Error: no write permission for file "/etc/gdm/Init/Default"

Any help would be nice thanks.

---

### Post by w1ll1am on 2010-01-02
Well I found out what was wrong. i went to the link below if anyone needs to know.

Ubuntu Rocks!

[http://myubuntublog.wordpress.com/2009/05/20/jaunty-enabling-num-lock-at-boot-after-login/](http://myubuntublog.wordpress.com/2009/05/20/jaunty-enabling-num-lock-at-boot-after-login/)

---

### Post by ITCons on 2010-01-20
Hmmmm.... weird... what does the NUM LOCK have to do with xsplash???

Can you maybe post some additional info so it is also useful for others? ;)

Wow, that would be really cool...

Also, I posted the problem to the relevant bug on:

[https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/474712](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/474712)

and

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/434786](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/434786)

Seems that even the suggested diff did not correct the problem when rebuilding the package from sources.
If we can get this resolved, we would really make a contribution to ubuntu! ;)

We can be heroes...!

---

