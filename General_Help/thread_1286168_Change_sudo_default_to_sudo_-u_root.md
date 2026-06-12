---
title: "Change sudo default to sudo -u root"
date: 2009-10-08
forum: General Help
---

### Post by reclimb on 2009-10-08
Hello, folks. This is my first post.
(Those who are in a rush may jump to the 3th par)
Around here we are used to openSUSE, and all computers need to be accessible to everyone, root access included in most cases. Every shared computer has at least 2 users: let's say, user all and user root. We have a list of some default passwords for these 2 users to try and every computer uses one of them. That's the way we do things here, though it seems to differ with ubuntu's user security. Our boss made a very fancy network security system, and we rely on it.

Though this is not in the security discussion, I'll defend our opinion: We, maybe a lot of people think that to guess a root password, say, 16 bytes longer, is hard enough for our security. Password leakage, intentionally or not, won't affect our servers and other sources of top secret data. I don't know a lot of root password in our lan.

So ...[SIZE=4] I want Sudo to ask for root password by default for all users[/SIZE].  Just want things to be uniform. Root user is already with password.
It must apply to the kdesu-like-x-dialogs sudo.

I could replace sudo in PATH for some script to call something like "/usr/bin/sudo -u root $args", but it doesn't seem the right or the best way to do it.

Thank you all.
Don't mind bad phrasing.

Almost forgot, i'm using Ubuntu 8.04

---

### Post by kerry_s on 2009-10-08
with sudo you do not need a root password & the user would use there login password. activating root cuts your system security by half, cause now only a single password needs to be cracked, instead of "user-name & password". thats just poor practice.

anyways, what you want can be done with visudo.
[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

---

### Post by sisco311 on 2009-10-08
**sudo:**

edit the sudoers files and add rootpw to the *Defaults* line.
(always edit the file with visudo)

**gksu:**

set the Authentication mode to su in *gksu-properties*

**policykit:**

replace the *<define_admin_auth group="admin"/>* line in */etc/PolicyKit/PolicyKit.conf* with *<define_admin_auth user="root"/>*.

or replace the content of the file with:
```
<config version="0.1">
</config>
```

---

### Post by Bachstelze on 2009-10-08
YOu can't change how sudo behaves by default without modifying the source. Use su, that's what it's for.

---

### Post by reclimb on 2009-10-08
Thank you, I though sudoers was only for exec permissions from each user. It's a good guide.
 It worked for sudo, but not for the config apps, that can still be unlocked with user password. What to do about them? 

As I said previously, it's at least unlikely factible to somene to crack our passwords. And it is impossible to do remotely, these computers are online under our godlike proxy. Even if someone were in the laboratory it would be fine, and our doors are locked. =)

Good, but not solved yet! I'll post my changes to suders later.
Bye!

--edit
Haha, submitted too late.
Ok, now gksu works, but the "Unlock" buttons still letting user password to unlock. 
--edit 2
[SIZE=7]SOLVED[/SIZE]
Missed "Group" to "User" in policykit.conf. Now it is like I want it. Thank you sisco311.

Ommiting system comments, here is my new visudo:
I added everything that were in my opensuse's visudo.

Defaults        always_set_home
Defaults        env_reset

Defaults        env_keep = "LANG LC_ADDRESS LC_CTYPE LC_COLLATE LC_IDENTIFICATION LC_MEASUREMENT LC_MESSAGES LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE LC_TIME LC_ALL LANGUAGE LINGUAS XDG_SESSION_COOKIE"

Defaults        targetpw
Runas_Alias     ROOT = root

ALL     ALL = (ALL) ALL
root    ALL=(ALL) ALL

---

