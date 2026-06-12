---
title: "sudo no longer asks me for my password"
date: 2006-04-29
forum: General Help
---

### Post by siennalizard on 2006-04-29
Sudo no longer asks me for my password. This is a little worrying...

I've checked my /etc/sudoers and it looks fine:

```

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

```

I've tried running sudo -K, closing shells and using new ones. Still I'm not getting asked for my password.

Any ideas?
Cheers,
J.

---

### Post by Bloch on 2006-04-29
sudo remembers your password for a while - I'm not sure how long, 5 minutes or so.
This means that you are asked for your password when using sudo the first time, and if you use it again within 5 minutes or so you will not be asked for the password.

It's convenient.

---

### Post by siennalizard on 2006-04-29
Solved the problem: I'd added myself to several groups manually in an attempt to solve another problem. In the process, I'd given myself _far_ too many group privileges, most importantly membership of the sudo group.

Really bad, that. [slaps wrist].

Cheers,
J.

---

