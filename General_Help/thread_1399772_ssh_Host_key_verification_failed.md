---
title: "ssh Host key verification failed"
date: 2010-02-06
forum: General Help
---

### Post by rnerwein on 2010-02-06
hello everybody
i have a problem with ssh. i'am running:
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
kernel: 2.6.31-16-generic
pc and laptop are connected via switch. hard wired and static ip
on ubuntu side is a wlan running connected to the internet

on my laptop: i am running:
Distributor ID:    SuSE
Description:    SuSE Linux 9.0 (i586)
Release:    9.0
Codename:    n/a
kernel: 2.4.21-99-default ( year 2004 )

on unbuntu side i use: SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
on suse side i use: SSH-1.99-OpenSSH_3.7.1p2
both sides are using: Protocol 2 and ServerKeyBits 768

and now my problem ( i try evering thing i know - google and so on - now i give up - no idea, all i found wasn't my problem)
i can connect from ubuntu to suse using ssh without a problem (no password ..)
but when i try to connect from suse to ubuntu i always get: [COLOR=Red]Host key verification failed[/COLOR]
and nothing else. no hint about middle man attack or so. no change to answer -> save the new key - go !
the permissions of  ~/ssh my both sides are id_rsa.pubcorrect i think ( drwx------) and the permissions of : authorized_key, id_rsa, known_hosts are all - -rw------- 1 ( not linked or so ).

any idea ???
ciao

---

### Post by efflandt on 2010-02-06
The correct directory for your personal ssh settings is **~/.ssh** (leading dot for hidden directory), so not sure if you made a typo here, or wrong directory there.

---

### Post by rnerwein on 2010-02-06
> **efflandt said:**
> The correct directory for your personal ssh settings is **~/.ssh** (leading dot for hidden directory), so not sure if you made a typo here, or wrong directory there.

hi
thanks for the replay. i solved the problem by my one. the .ssh was correct. the probelm was the permissions of known_hosts:
-rw-------    1 richi    trusted       403 2010-02-06 12:11 known_hosts
i changed it to:
-rwxrwxrwx    1 richi    trusted       403 2010-02-06 12:11 known_hosts

and it works - god thanks. i already changed it back to: -rw-r--r-- and it still works.
on both sides my login is "richi" but the groups are different. but wat's are names.
i always told my students: names are reek and sonic ( computers needs numbers).
what i want to say the user and group id's are different.
-- the error ist mostely between the ears ----
but thanks for the reply
ciao
where can i mark this post "SOLVED" ?

---

