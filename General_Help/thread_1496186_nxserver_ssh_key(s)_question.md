---
title: "nxserver: ssh key(s) question"
date: 2010-05-29
forum: General Help
---

### Post by tony_k on 2010-05-29
based on some previous posts, i feel like i'm sharing the pain of attempting to setup nxserver appropriately.

i have read a decent amount of documentation and forum postings, and burned several hours on trying different things and i have a fundamental question:

when i start a client session am i logging in with:

(a) a user id known as "nx"

(b) the user id i punch into the client session panel (e.g. "user123")

(c) both "nx" and "user123"

follow on questions are:

(1) it seems like i'm supposed to provide the ssh key for the "nx" user in the client session panel, if that's the case, should it be finding the key for "user123" by convention?

(2) will it even try to use ssh keys for "user123"?

reason i'm asking is that i was able to connect successfully using password authentication for "user123", but when i set:

```
PasswordAuthentication no
```

in sshd_config at the server, i could no longer log on successfully.

(3) i should be able to connect with PasswordAuthentication turned off right?

the odd thing is that i can successfully:

```
ssh user123@myserver
```

from the command line using ssh keys (i get love with no password)...

i'm using windows xp at the client with cygwin/ssh,
and lucid at the server...

any insight appreciated, thanks!

---

### Post by DagMan on 2010-05-29
Yeah it appears that nx uses its own ssh keys and it uses the user you want to log in as through password authentication.  It isn't ideal.  You can go to the trouble of setting up differant nx keys than the default ones, but its sort of a pointless security measure when you need to have your ssh server accepting passwords.  The best it does is encrypts the login I guess.

---

### Post by alxgomz on 2010-05-29
the nx user is used to build up an ssh connection through wich the X authentication AND remote desktop traffic will be sent, this is not few things.
so when you start a new session, youlog inwith:

- nx to ssh server
- user123 to an X session

Buliding new ssh keys as a replacement of default nx ones is not a pain at all... All you need to do is build a key and put it in the right place in nx's homedir.
your user123 does not NEED to have any ssh key setup in order to connect to nxserver.

question1: no it shouldn't: think about it like tunneelling a vnc session in an SSH tunnel... users may be different.

question2: as i said nxserver never NEEDS an ssh key in order to setup an X session for a user (it only needs it in order to build an encrypted channel)

question3: if you disable passwd authentication, you can't, of course, no longer login usoing passwords... but ns does not REQUIRE the passwd authentication to be disabled.

@DagMan
ssh keys is far from pointless! Its the only way to establish SSH encrypted connection to the server with a system user which doesn't have passwd...

---

### Post by DagMan on 2010-05-29
Most people who know better would like to run their ssh server with password authentication turned off and you can't do that if you want to use nxserver.  That isn't ideal, as I said, and it makes the ssh of nx pointless, in that respect, as I said - and not in the respect that you said.

---

### Post by alxgomz on 2010-05-29
In that respect you're right, I thought you meant ssh keys was useless.

---

