---
title: "sshing with all sorts of random IP's"
date: 2010-04-17
forum: General Help
---

### Post by cong06 on 2010-04-17
I am working on a small area network, where machines pop in and out all the time.

So I ssh into  into a network address, let's say 10.42.43.14, and I work with it.
Then the computer gets replaced, and another computer gets the address 10.42.43.14.

On logging in, I get the warning:
```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
40:5e:f8:41:e1:61:17:e6:57:c2:94:15:5a:68:c3:5a.
Please contact your system administrator.
Add correct host key in /home/lari/.ssh/known_hosts to get rid of this message.
Offending key in /home/lari/.ssh/known_hosts:1
RSA host key for 10.42.43.14 has changed and you have requested strict checking.
Host key verification failed.

```
Is there anyway to disable this for local connections: say 10.42.43.X?
I could keep deleting the /home/lari/.ssh/known_hosts file, but I'd rather not... and fixing the error lines doesn't really seem to be an effective solution either.

I can't really make heads or tails of the "/etc/ssh/ssh_config" file...

---

### Post by dwarfolo on 2010-04-17
Have you tryed to disable *StrictHostKeyChecking*
 in ssh_config?

```
RSA host key for 10.42.43.14 has changed and you have requested strict checking.
```

```
ssh -o StrictHostKeyChecking=no user@server
```

---

