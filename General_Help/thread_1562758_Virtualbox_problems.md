---
title: "Virtualbox problems"
date: 2010-08-28
forum: General Help
---

### Post by DeMus on 2010-08-28
Hi,
I use Ultimate Edition 10.04-64 bits. I know it is based on Lucid, but there are differences. What I understand about it also in the used kernel.
I try to use Virtualbox so I can experiment with another OS, in this case Mac OSX.
I get the message as is shown in the attached picture and I have no idea what so ever what it is and what to do about it.

Some info:

uname -a
Linux Ultimate-64 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux

What do I need to, in plain English, so I can use Virtualbox?

---

### Post by DeMus on 2010-08-28
I think I found it with a little help of my friend Google.
I found a forum where somebody said this:
```
Try disabling kvm module...
"modprobe -r kvm_intel" with root privileges.
```
This worked for me...
I don't know yet what consequences it has, but so far things are running.

Edit: Maybe somebody can explain to me what I did, cause I have no idea. I would like to know.

---

