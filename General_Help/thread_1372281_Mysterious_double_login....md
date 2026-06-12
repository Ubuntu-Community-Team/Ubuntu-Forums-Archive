---
title: "Mysterious double login..."
date: 2010-01-04
forum: General Help
---

### Post by cj13579 on 2010-01-04
Hi all, I was wondering if you could help me. Although there are multiple accounts to this machine I am the only one who uses it and it is set to auto-login to "chris" on boot. However, it seems I have logged in twice.

```
chris@qserver:~$ who
chris    tty7         2010-01-03 22:35 (:0)
chris    pts/0        2010-01-04 13:47 (:0.0)
```

I don't think that this is an issue but it would be interesting to know how/why this has happened.

Many thanks in advance.

---

### Post by Saiko Berry on 2010-01-04
Someone seems to be connecting to you remotely from telnet? Thats a psuedo user account created from an outside connection.

You can kill it by finding its PID and doing a kill -9 PID I believe.

ps fax

---

### Post by cj13579 on 2010-01-04
Ah, I see. Am I right in thinking that is a local network connection? becuase when I connect from work for example in the brackets at the end I get a host IP etc etc.

---

### Post by imbjr on 2010-01-04
There's very likely nothing wrong. For example, here's my current who:

```

imbjr@pc:~$ who
imbjr    tty7         2010-01-04 10:28 (:0)
imbjr    pts/0        2010-01-04 10:29 (:0.0)
imbjr    pts/1        2010-01-04 11:23 (:0.0)
imbjr    pts/2        2010-01-04 12:24 (:0.0)
imbjr    pts/3        2010-01-04 15:53 (:0.0)

```

I'm logged in via gdm and I have 4 terminal sessions open currently. That's why there are 5 of me listed.

---

### Post by Saiko Berry on 2010-01-04
> **cj13579 said:**
> Ah, I see. Am I right in thinking that is a local network connection? becuase when I connect from work for example in the brackets at the end I get a host IP etc etc.

Yep. Nothing to worry about. But if you want to get rid of it just follow the steps to kill it via ID.

---

### Post by cj13579 on 2010-01-04
Many thanks for the explanations both. I'll mark as solved!

---

