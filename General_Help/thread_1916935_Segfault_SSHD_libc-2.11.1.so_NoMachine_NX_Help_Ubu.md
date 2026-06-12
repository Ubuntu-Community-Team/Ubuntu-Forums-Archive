---
title: "Segfault SSHD libc-2.11.1.so NoMachine NX Help Ubuntu 10.04"
date: 2012-01-29
forum: General Help
---

### Post by own3mall on 2012-01-29
Hi All,

I've recently been receiving these error messages when I attempt to SSH into my machine using the NoMachine client.  I used to be able to get in just fine, prior to this week, but now I get the following message from my client when attempting to connect to the server:

```

Authentication failed for user xxx

```
[I]
I checked my server log, and I get the following messages whenever my client says the authentication failed for user xxx
[/I]
```

Jan 29 00:01:22 eric-desktop kernel: [ 2243.892563] sshd[7777]: segfault at befba590 ip 00478fea sp befba580 error 6 in libc-2.11.1.so[3d3000+153000]

```

I tried to remove libc-2.11.1.so from my system, but then nothing worked.  Any ideas as to what I should do?  I'm running Ubuntu 10.04.

---

### Post by own3mall on 2012-01-29
Anyone have any idea what I should try?

---

### Post by own3mall on 2012-02-10
I ended up trying some things, and I completely destroyed my server.  It  wouldn't respond to any command and wouldn't boot even into the  recovery mode.  So, I put my backup server into place, and it's been  running great ever since, until now.  It seems that if I begin an NX  session and run FireFTP through Firefox within that session, the next  time I try to remote in I will receive the segfault message.  I have no  idea what to do, and I don't want to risk destroying my backup server.   Any advice?

---

