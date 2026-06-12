---
title: "Run gksu without a password possible?"
date: 2010-04-25
forum: General Help
---

### Post by Gen2ly on 2010-04-25
Hello,

I'd like to be able to run gksu (i.e. the default windowed authentication) without a password.  I tried to find this on the wiki and here on the forums but wasn't able to find anything (if I missed it please point me to the relevant thread/page.  I've allowed 'sudo' to run without a password:

```
<username> ALL=NOPASSWD: ALL
```

for my username but this has no effect on 'gksu'.  As I am the only user on my machine and I have to enter a password on login, I feel pretty safe.  Could someone help me on how to do this?

---

### Post by lisati on 2010-04-25
I'd advise against it, because of the potential for security-related problems.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kerry_s on 2010-04-26
> **Gen2ly said:**
> Hello,

I'd like to be able to run gksu (i.e. the default windowed authentication) without a password.  I tried to find this on the wiki and here on the forums but wasn't able to find anything (if I missed it please point me to the relevant thread/page.  I've allowed 'sudo' to run without a password:

```
<username> ALL=NOPASSWD: ALL
```

for my username but this has no effect on 'gksu'.  As I am the only user on my machine and I have to enter a password on login, I feel pretty safe.  Could someone help me on how to do this?

thats right but you should just allow for the programs you want.
also don't forget some things are done by policy kit so sudoers will have no effect.

---

### Post by Gen2ly on 2010-04-27
OK, I don't get it :).  I'm guessing that Ubuntu uses gksudo since the root account is disabled, is this correct?  I've tried kerry_s suggestion to add the programs I need (synaptics) right now with no luck (the authentification window still pops up):

```
username ALL=NOPASSWD: /usr/sbin/synaptics
```

lisati, if you don't mind elaborating, why is this considered insecure?  As I see it, I will still have my machine protected by the GDM password so I only have to watch it when I leave it alone and other people are around.  Is this correct?  Sorry for the beginner's questions but would be grateful if for any who choose to do so. :)

P.S. Currently using Lucid beta 2.

---

