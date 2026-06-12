---
title: "Equivalent of winver in Ubuntu"
date: 2012-05-05
forum: General Help
---

### Post by deepaknet on 2012-05-05
Dear Ubuntu Team,

We have an app called 'winver' in Windows which indicates the version of the operating system and service pack etc. What is the equivalent of this tool in Ubuntu? Would it also indicate what desktop session (lubuntu etc) we are using?

---

### Post by Quatrix on 2012-05-05
[https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

lsb_release -a
uname -a

---

### Post by deepaknet on 2012-05-05
Thank you for the two commands. The following are the output from my computer.

For lsb_release the first message seems to be showing some error. Can you help enlighten on the same please?


lavanyadeepak@lavanyadeepak:~$ uname -a
Linux lavanyadeepak 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 athlon i386 GNU/Linux
lavanyadeepak@lavanyadeepak:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise

---

### Post by Cheesemill on 2012-05-05
> **deepaknet said:**
> For lsb_release the first message seems to be showing some error. Can you help enlighten on the same please?

It's not an error, just information about your system.
It simply means you don't have any of the lsb-* packages installed.

---

### Post by deepaknet on 2012-05-05
What is that 'LSB'? Is there  a manpage or help manual on that topic?

---

### Post by Irihapeti on 2012-05-05
Try:

```
lsb_release -rd
```

It runs on a standard Ubuntu install, even if "lsb_release" on its own doesn't work.

---

### Post by Habitual on 2012-05-05
> **deepaknet said:**
> What is that 'LSB'? Is there  a manpage or help manual on that topic?

Terminal > 
```
man lsb-release
```

---

### Post by deepaknet on 2012-05-05
I have tried it and since it didn't work so only asked in the forum:


lavanyadeepak@lavanyadeepak:~$ man lsb-release
No manual entry for lsb-release

---

### Post by hawkmage on 2012-05-05
You may want to try this:
```
man lsb_release
```

lsb_release is the command
lsb-release is a file in /etc

---

### Post by deepaknet on 2012-05-05
Thank you hawkimage. That worked.

---

