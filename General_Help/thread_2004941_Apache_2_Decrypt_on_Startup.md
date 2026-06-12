---
title: "Apache 2 Decrypt on Startup"
date: 2012-06-16
forum: General Help
---

### Post by trixt.er on 2012-06-16
Hey guys (and gals),
I just installed some memory into my Ubuntu server and am having some startup issues. After I type in my user name and password I get the following:

Apache needs to decrypt your SSL Keys for "server name and port" (RSA)Please enter passphrase:

Where server name and port are my own. I have never seen this before. I tried typing in the passphrase but nothing happened. I also tried the following:

apt-get --purge remove apache2
I have checked the package and sure enough it's removed. Why is it still prompting?

I toke drastic measures and deleted the /etc/init.d/apache2 dir.

Now after I log in the screen goes back to the login screen!

I tried a few other things:
Edited /etc/kde4/kdm/kdmrc  to allow root login and I hide the root user (myself).

I can get into the shell by hitting ctrl-alt-f1.

After reinstalling apache2 it just hangs there. If I remove apache2 I get a flickering terminal, some commands issued, and it just returns to the login page.

---

