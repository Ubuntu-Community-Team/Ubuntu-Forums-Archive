---
title: "How long does Ubuntu Karmic &quot;remember&quot; the sudo password?"
date: 2009-11-22
forum: General Help
---

### Post by allanlewis on 2009-11-22
I've noticed that if I run a command that requires root access and provide the "sudo" password, the system seems to remember this for a period of time, i.e. if I run another "sudo" command within a few minutes, I don't need to type my password. Also, graphical programs seem to run on a different timer.

Where are these settings made, and are they user-configurable?

---

### Post by fluffman86 on 2009-11-22
I believe the default is about 15 minutes.

see [https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout) and [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more.

---

### Post by NoaHall on 2009-11-22
> **fluffman86 said:**
> I believe the default is about 15 minutes.

see [https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout) and [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more.

Yes, it's 15 minutes. If you want to stay permanently logged in, use "sudo su" or "sudo -i"

---

