---
title: "Mail"
date: 2009-10-19
forum: General Help
---

### Post by airplanes18 on 2009-10-19
hey, i was wondering if there is any easy way to set up the mail clients. i have no idea why id have to do this myself and why it isnt pre-done, but okay. what do i do? i picked my domain, i just need servers. no  idea. mail nub. help

---

### Post by Giblet5 on 2009-10-19
I use dovecot-postfix. It provides smtp, pop3, and imap services. It's fast, small and it works. Easy to configure.

You can also use Scalix for free if you have 1-10 users and want to service Outlook's and Evolution's more advanced collaborative features.

---

### Post by Giblet5 on 2009-10-19
> **airplanes18 said:**
> hey, i was wondering if there is any easy way to set up the mail clients. i have no idea why id have to do this myself and why it isnt pre-done, but okay. what do i do? i picked my domain, i just need servers. no  idea. mail nub. help

How in the world could software automatically set up your email accounts? What would that code look like?

```
for i in usernames
  addemailconfig $i@hotmail.com password "12345" pop3
  addemailconfig $i@gmail.com password "12345" pop3
  addemailconfig $i@pizzaporn.net password "12345" pop3
```

Do you have an idea of why you have to do it yourself yet?

---

### Post by airplanes18 on 2009-10-19
well, i mean like gmail. u just make one. i dont understande the server thing. retarded to me. makes zero sense. PS nice double post

all i get is a box in the terminal i cant do anything with.

---

### Post by Giblet5 on 2009-10-19
> **airplanes18 said:**
> well, i mean like gmail. u just make one. i dont understande the server thing. retarded to me. makes zero sense. PS nice double post

Email is complicated regardless of how you, personally, see it.

Many Unix-like OSes were shipped with sendmail configured in a generic way that was usually wrong. HP/UX, Solaris, AIX, UNIX... They all come with sendmail listening on port 25 for connections that only nefarious basement weasels will ever test. Hardly anyone knew it was there, fewer used it, but it left an exploitable port open on the network and a few people got burned by it. Full disk drives, buffer-overrun attacks, etc.

So now, you install it if you want it, and it's pretty darned easy too.

But there is no email server that can be correctly installed automatically. Where do admin messages go? How do you filter spam? Decisions decisions and they can't be automated in any way but the wrong way.

---

### Post by airplanes18 on 2009-10-19
all i want is a custom email domain. this is like outlook express, only not boring. just as stupid to set up, but not boring. any i can latch onto?

---

