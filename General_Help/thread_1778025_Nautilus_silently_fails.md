---
title: "Nautilus silently fails"
date: 2011-06-08
forum: General Help
---

### Post by Philop on 2011-06-08
Hello great people of this community,

I am using Ubuntu Natty 11.04 and am experiencing problems with Nautilus. At random, it seems, it will close itself silently. E.g. if I open nautilus, and browse to my documents, I can leave that nautilus window open, and after a couple of seconds it will *poof* dissapear.

I really wouldn't know how to troubleshoot this. Could anyone point me in a direction on how to solve this issue?

Thanks!

---

### Post by jerrrys on 2011-06-08
have you just tried reloading nautilus and see if you can get lucky?

---

### Post by Philop on 2011-06-08
Yep. Did all kind of things. Even deleting the .recently-used file.
It all doesn't help. 

I guess the problem lies somewhere in the configuration of nautilus. What (configuration) files does nautilus use which are located in my home folder??

---

### Post by jerrrys on 2011-06-08
Im not familiar with 11o4, but in gnome i think i would be tempted to reinstall gdm

---

### Post by TeoBigusGeekus on 2011-06-08
Open nautilus from terminal with
```
nautilus
```
and see if you get any error messages after it crashes.

---

### Post by Philop on 2011-06-09
Tried that. Never seen one message!

---

### Post by Philop on 2011-06-26
Bump!

---

### Post by TeoBigusGeekus on 2011-06-26
Try this: after a crash, ctrl+alt+F1 to go to tty1. See if you get any error messages there (ctrl+alt+F7 to go back to tty7 - graphical session).

---

### Post by Dave_L on 2011-06-26
> **Philop said:**
> What (configuration) files does nautilus use which are located in my home folder??

In Ubuntu 10.04, the configuration is accessed by:

```
gconf-editor
```

Then navigate to apps >> nautilus

These settings are actually located in ~/.gconf/apps/nautilus

---

### Post by Philop on 2011-07-04
> **TeoBigusGeekus said:**
> Try this: after a crash, ctrl+alt+F1 to go to tty1. See if you get any error messages there (ctrl+alt+F7 to go back to tty7 - graphical session).

Nope. No error messages whatsoever.

BUT I can now easily reproduce the error and found a message in syslog:

```
Jul  4 09:37:31 Lorena kernel: [15175.194310] nautilus[9051]: segfault at 18 ip 00000000004ae344 sp 00007fff7deb8440 error 4 in nautilus[400000+1dd000]
Jul  4 09:37:50 Lorena kernel: [15193.974484] nautilus[9569]: segfault at 18 ip 00000000004ae344 sp 00007fff29e98f30 error 4 in nautilus[400000+1dd000]
Jul  4 09:39:07 Lorena kernel: [15270.887938] nautilus[9986]: segfault at 18 ip 00000000004ae344 sp 00007fff5c3d69e0 error 4 in nautilus[400000+1dd000]
Jul  4 09:41:12 Lorena kernel: [15395.748133] nautilus[11269]: segfault at 18 ip 00000000004ae344 sp 00007fffdfadf980 error 4 in nautilus[400000+1dd000]
```

So when nautilus fails I get a segfault? Is this helpfull?

---

### Post by Philop on 2011-07-06
Bump :/

---

