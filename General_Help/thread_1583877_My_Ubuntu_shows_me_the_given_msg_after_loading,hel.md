---
title: "My Ubuntu shows me the given msg after loading,help"
date: 2010-09-28
forum: General Help
---

### Post by tajiknomi on 2010-09-28
[SIZE=2][I]Last time my Pc was automatically shutdown due to problem in light,now when i turn it on,it shows me the given message after ubuntu loads,

**[SIZE=3]No init found,try passing inti=bootarg[/SIZE]**

what can i do now..?it don't take it to my login=screen....

i will be greatful if some1 help me to get out of this

thanks
[/I][/SIZE]

---

### Post by cariboo on 2010-09-28
Try running fsck from the live cd. Boot from the Live Cd and once at the desktop, open a terminal and type:

```
sudo fsck -y /dev/sdX
```

where /dev/sdX is the partition you have Ubuntu installed on.

BTW this isn't a security question, so moved to General Help.

---

### Post by tajiknomi on 2010-09-28
[I][SIZE=2]sorry 4 posting my post here....but plz tell me about this ? what this means..?

i means the "fsck",what this means?
[/SIZE][/I]

---

### Post by madmax75 on 2010-09-28
> **tajiknomi said:**
> [I][SIZE=2]
i means the "fsck",what this means?
[/SIZE][/I]

File systems check.

---

