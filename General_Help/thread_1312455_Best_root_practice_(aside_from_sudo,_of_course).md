---
title: "Best root practice (aside from sudo, of course)"
date: 2009-11-03
forum: General Help
---

### Post by Jestersage on 2009-11-03
For those that do use the root account (instead of just su/sudo), do you guys put a password in (and thus make recovery console-root login require password) or leave it password-less (so one cannot login through your normal login)?

---

### Post by hal8000 on 2009-11-03
There's plenty about not creating a root account on ubuntu.

If you need to type lots of root commands then
sudo su
(and normal password will give you root access at a terminal)


sudo passwd
allows you to set a password forn the root account, though with the added security flaws and thers plenty of reasons for not doing this, hope that helps.

---

### Post by anaconda on 2009-11-03
Password-less root accout can be quite dangerous..

So if you want to make a root accout I recommend you use one with a password.

And Yes there are valid reasons to have a separate root account, but the ubuntu way is to prefer sudo.

---

### Post by Jestersage on 2009-11-03
> **hal8000 said:**
> There's plenty about not creating a root account on ubuntu.

If you need to type lots of root commands then
sudo su
(and normal password will give you root access at a terminal)


sudo passwd
allows you to set a password forn the root account, though with the added security flaws and thers plenty of reasons for not doing this, hope that helps.

No, I already figure out how to enable it. It's just that currently, with the login windows settings, it seems either I have a passwordless root login that is good for recovery console only, or a password-ed root for true root login.

---

### Post by fluffman86 on 2009-11-03
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

^^ All you need to know about root on Ubuntu.

---

### Post by Old *ix Geek on 2009-11-03
> **Jestersage said:**
> For those that do use the root account (instead of just su/sudo), do you guys put a password in (and thus make recovery console-root login require password) or leave it password-less (so one cannot login through your normal login)?I would NEVER, under any circumstances, leave a root account enabled but without a password.

I ALWAYS enable root--I 'grew up' so to speak with UNIX in the '80s, with the superuser/regular user model, and the RESPECT that goes along with being root, and after almost 25 years I'm not about to change--but I rarely log in with it.

It's not an either/or thing--you can have a root account and still use su and/or sudo.

My caveat and advice to anyone who wants to log in as root and piddle around is this: If you royally screw things up--and it's very possible [likely?] that you will--don't whine about it. That's been my personal motto for 20+ years. I've always accepted full responsibility for any damage or problems I might cause while logged in as root. Luckily, in all this time, I've only done one REALLY bone-headed thing that necessitated a reinstall of the OS. :oops:  (Technically, it wasn't NECESSARY, but practically speaking it was.)  The point being, if you screw up while logged in as root, be a wo/man about it, suck it up, and get down to business fixing things.

---

### Post by alphaniner on 2009-11-03
> **hal8000 said:**
> If you need to type lots of root commands then
sudo su


I used **sudo su** for a long time with no side effects, but the official *right way* is to use **sudo -i**.  It does the same thing, but some environment variables are different.

---

