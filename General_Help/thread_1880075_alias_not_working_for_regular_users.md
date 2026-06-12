---
title: "alias not working for regular users"
date: 2011-11-12
forum: General Help
---

### Post by K-Jtan on 2011-11-12
Hi,

I just created a new user on my server at home so my girl friend could use it to do some backups. Currently, we are accessing it through ssh. when I logged in has her, I did a quick "ls" command and the results were all the same colour. I found it strange since I see different colours when I log in with my account.

Then I though, oh, maybe the alias are not there ... so I typed "alias" and it returned me nothing. So I added a couple alias that would be useful for her by using 

```
alias ls='ls --color=auto'
```etc.

Then everything seems to be working. I did a log out, then relog in and the alias were gone again. After that, I did a quick search on the web and I found a second solution that tells me to add them in ~/.bashrc I when to do that and what a suprise, the alias are there but not working.

Could someone help me figure this out ?

p.-s. using Ubuntu 11.10 "for home" (not the server version)

---

### Post by llamabr on 2011-11-12
After you put them in .bashrc you have to log out again, or else run bash again.  Log out and back in, and let us know if it's still not working.

---

### Post by K-Jtan on 2011-11-13
> **llamabr said:**
> After you put them in .bashrc you have to log out again, or else run bash again.  Log out and back in, and let us know if it's still not working.

how I just found the problem, thanks for your comment. it just flashed at me that the account wasn't using bash. it was using sh.

I just run this from the administrator account

```
chsh -s /bin/bash username
```

hope this will help someone else

---

### Post by dodo3773 on 2011-11-13
> **llamabr said:**
> After you put them in .bashrc you have to log out again, or else run bash again.  Log out and back in, and let us know if it's still not working.

source ~/.bashrc

Wouldn't that still work in a server environment?

---

