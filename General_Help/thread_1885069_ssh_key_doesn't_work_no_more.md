---
title: "ssh key doesn't work no more"
date: 2011-11-22
forum: General Help
---

### Post by F.G. on 2011-11-22
hi everybody,

i was playing with ssh last night. between a laptop with Ubuntu and a netbook with crunchbang. opening terminals in one from the other, ssh-ing back to the original machine, that kind of thing (i actually wound up fork-bombing my laptop from my netbook (sheer idiocy I know, these are the effects of red wine and computing)).

so now i can ssh my netbook from my laptop. if i try to ssh my laptop from my netbook or my laptop from itself i get:
```
bob@helios:~$ ssh 192.168.2.102
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
ae:15:b5:89:53:06:65:f0:2d:74:8c:eb:7b:77:3d:a1.
Please contact your system administrator.
Add correct host key in /home/bob/.ssh/known_hosts to get rid of this message.
Offending key in /home/bob/.ssh/known_hosts:2
RSA host key for 192.168.2.102 has changed and you have requested strict checking.
Host key verification failed.

```
however if i use a different interface (another wifi card) i can connect fine.

if anyone can give me any help understanding what is going on and why it is going on. i will be very grateful.  i should point out (as i imagine anyone reading this has guessed) that this is a learning exercise and is in no way urgent, or time sensitive.

thanks for any replies.

---

### Post by F.G. on 2011-11-22
_.·oOo·._     ...bump.

i realise it's quite early to bump this, particularly as it is not urgent. but i think it's about to get lost in the enormity of the general help section. i guess i should have posted somewhere more specific. perhaps one of the mods could move it somewhere more appropriate ('networking and wireless' maybe, although that's usually full of wifi related stuff or maybe 'security'? those guys know their stuff). thanks.

---

### Post by Hugh971 on 2011-11-22
Have you tried adding the key into /home/bob/.ssh/known_hosts as the message says?

---

### Post by F.G. on 2011-11-22
so, i just deleted the keys that were already in the file, so ssh would add it automatically as a new one. works fine now.

still, i have no idea why it changed, particularly for one interface and not the other (i was using both of them previously). or how to add a key manually.

---

