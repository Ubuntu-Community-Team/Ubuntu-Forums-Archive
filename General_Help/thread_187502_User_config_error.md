---
title: "User config error"
date: 2006-06-03
forum: General Help
---

### Post by arnor on 2006-06-03
Hi,
I just upgrade my ubuntu an di got some "problems" with my system users, each time i connect myself as someone i got this :
[HTML]
erreur de configuration - élément « QUOTAS_ENAB » inconnu (avertissez l'administrateur)
erreur de configuration - élément « NOLOGIN_STR » inconnu (avertissez l'administrateur)
erreur de configuration - élément « ENV_HZ » inconnu (avertissez l'administrateur)
erreur de configuration - élément « CHFN_AUTH » inconnu (avertissez l'administrateur)
erreur de configuration - élément « CLOSE_SESSIONS » inconnu (avertissez l'administrateur)
[/HTML]
any idees? 
thanks for your answer,
arnor
ps : thx for this new Ubuntu... ;-)

---

### Post by blackjack6.21.91 on 2006-06-03
The error you gave us seems to be in a foreign language.  If you translated it the people here may be of more use.  If we don't know what's wrong, its gonna be pretty hard to fix it.

---

### Post by arnor on 2006-06-03
ups sorry my apologizes: 
[HTML]erreur de configuration - élément « QUOTAS_ENAB » inconnu (avertissez l'administrateur)
erreur de configuration - élément « NOLOGIN_STR » inconnu (avertissez l'administrateur)
erreur de configuration - élément « ENV_HZ » inconnu (avertissez l'administrateur)
erreur de configuration - élément « CHFN_AUTH » inconnu (avertissez l'administrateur)
erreur de configuration - élément « CLOSE_SESSIONS » inconnu (avertissez l'administrateur)[/HTML]
Its french...
it mean "config error - element « QUOTAS_ENAB » unknown ( ask admin )
etc... ;-)

---

### Post by arnor on 2006-06-03
i check the adduser.config ... but did not find all the errors he is complaining about ...

---

### Post by emperor on 2006-06-03
I have the same problem on the 2 machines I have done a "dist-upgrade" on: Here is the error in "English":

configuration error - unknown item 'QUOTAS_ENAB' (notify administrator)
configuration error - unknown item 'NOLOGIN_STR' (notify administrator)
configuration error - unknown item 'ENV_HZ' (notify administrator)
configuration error - unknown item 'CHFN_AUTH' (notify administrator)
configuration error - unknown item 'CLOSE_SESSIONS' (notify administrator)

---

### Post by arnor on 2006-06-03
I also did a dist-upgrade and i got those messages, i search a bit but i didn't find the solution... did you? :-k 
arnor

---

### Post by kurbacik on 2006-06-03
Here's the solution if someone should need it: The problem is caused by upgrading package login. apt-get for some reason doesn't remove FAIL_DELAY etc. from /etc/login.defs even though they are not needed anymore (and may not exist in that file). If you manually comment out those lines, everything should work.

---

### Post by kurbacik on 2006-06-03
[QUOTE=kurbacik]Here's the solution if someone should need it: The problem is caused by upgrading package login. apt-get for some reason doesn't remove FAIL_DELAY etc. from /etc/login.defs even though they are not needed anymore (and may not exist in that file). If you manually comment out those lines, everything should work.[/QUOTE]

Sorry, I was too quick in my answer. I still have the same problem.

---

### Post by kurbacik on 2006-06-03
There is a solution, although it's more like a workaround: in /etc/login.defs you can just simply comment out all references ('QUOTAS_ENAB', 'NOLOGIN_STR', 'ENV_HZ', 'CHFN_AUTH', 'CLOSE_SESSIONS') to the above variables. This is the solution of a Debian newsgroup ([http://lists.debian.org/debian-user/2005/10/msg00587.html](http://lists.debian.org/debian-user/2005/10/msg00587.html))

---

### Post by arnor on 2006-06-03
thanks a lot,
i commented all the unknown stuff and he is now happy again...lol
arno

---

### Post by emperor on 2006-06-03
[quote=kurbacik]There is a solution, although it's more like a workaround: in /etc/login.defs you can just simply comment out all references ('QUOTAS_ENAB', 'NOLOGIN_STR', 'ENV_HZ', 'CHFN_AUTH', 'CLOSE_SESSIONS') to the above variables. This is the solution of a Debian newsgroup ([http://lists.debian.org/debian-user/2005/10/msg00587.html]("http://lists.debian.org/debian-user/2005/10/msg00587.html"))[/quote]

The dist-upgrade includes a new login.def file that apparently we did not select to replace during the upgrade process. So, here is another solution to fix the login error problem:

sudo cp /etc/login.defs.dpkg-dist /etc/login.defs

---

