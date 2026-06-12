---
title: "squirrelmail inbox is always empty"
date: 2011-04-23
forum: General Help
---

### Post by stunet on 2011-04-23
Hi,

after fighting to get squirrelmail to work, I'm now stuck on it to read my mailbox.

I have postfix and dovecot installed and I can access my mail by another solution, but not squirrelmail.

a little about how its setup.

this is just a local setup, I'm only using it to test out my web software. it won't be used for outbound sending.

I can access my mailbox in webmin, but I'd prefer squirrelmail since I like their ui better (and not 100% sure if webmin's webmail accept html emails).

I'm new to setting up squirrelmail, if you need to see my config file for it, let me know. Also something worth pointing out, I can send mail through squirrelmail, but cant receive it(i sent out a test email and was able to read it from webmin.

I appreciate your help :)

---

### Post by stunet on 2011-04-24
don't ask me how but i got this working :o

the only thing i can think of that fixed this was disabling suhosin.session.encrypt

had to do that while trying another webmail and for laughs, tried squirrelmail to see both work now :D

if this bit of news helps anyone, that will make this all worth it :)

---

