---
title: "terminal reads &quot;I have no name!@host&quot;"
date: 2006-04-01
forum: General Help
---

### Post by bond00 on 2006-04-01
This never happened before, but all of sudden whenever I use the terminal for anything...SSH, bash, whatever, the lines start out with "I have no name!@host: ~$" instead of "username@host:~$"  This is very odd....has anyone seen this problem before and know how to fix it? Thanks....

---

### Post by 5-HT on 2006-04-01
What does 'echo $USER' return?
Also, could you post the output of $PS1?

---

### Post by Ian Maxwell on 2006-04-01
When that happened to me, it was because I had set /etc/passwd to be read-inaccessible to non-root users, thinking it would be more secure.

---

### Post by bond00 on 2006-04-01
[QUOTE=Ian Maxwell]When that happened to me, it was because I had set /etc/passwd to be read-inaccessible to non-root users, thinking it would be more secure.[/QUOTE]

That's what it was....I did the exact same thing because I also assumed it would be more secure. Thanks for the help!

---

### Post by lcg on 2006-04-02
[QUOTE=bond00]I did the exact same thing because I also assumed it would be more secure.[/QUOTE]
It isn't. Having /etc/passwd world-readable is not insecure because it does not contain any password hashes. However, /etc/shadow (which does contain these hashes) is indeed owned by root and mode 600.

The most information someone can get from your /etc/passwd is what usernames exist on a computer and their respective homes and shells. None of this is any kind of sensitive information.

HTH,
Lars

---

### Post by ajeetraina on 2008-05-26
> **5-HT said:**
> What does 'echo $USER' return?
Also, could you post the output of $PS1?

I am having the same problem and here is my outputs:

I have no name!@dicex:~$ echo $USER
vjs
I have no name!@dicex:~$ echo $PS1
${debian_chroot:+($debian_chroot)}\u@\h:\w\$
I have no name!@dicex:~$

---

### Post by coolparty on 2008-07-21
Install 'nscd'!

---

