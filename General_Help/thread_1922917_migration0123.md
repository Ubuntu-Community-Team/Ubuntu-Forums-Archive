---
title: "migration/0/1/2/3"
date: 2012-02-09
forum: General Help
---

### Post by kamaradski on 2012-02-09
Hi All,

I recently added a new laptop to my computer-collection, packing the new second generation i3 core.

I installed Xubuntu and normal ubuntu both 11.10. meanwhile i removed ubuntu and left only xubuntu on the machine,

On both installations i am experiencing high energy and CPU use primarily due to the processes "migration/x".  I found out that these are used for internal CPU load balancing, and should only be active when needed, correct?

However i'm booting the pc, and in 10min these processes are going wild. 

normal computer use, little browsing or skype, nothing fancy, almost clean install.

```

root        11  0.0  0.0      0     0 ?        S    20:02   0:00 [migration/2]
root        14 78.5  0.0      0     0 ?        S    20:02 123:58 [migration/3]
root         7 86.3  0.0      0     0 ?        S    20:02 136:15 [migration/1]
root         6 89.5  0.0      0     0 ?        S    20:02 141:26 [migration/0]

```

Items checked:
- killed several user processes in the hope to find something that triggers these events, no-luck
- checked memory and hard-drive with memtest and spinrite, no errors.

as i'm still relative new to linux (only 2 years combined) i could use some suggestions on how to troubleshoot this. 

KR
Kamaradski

---

