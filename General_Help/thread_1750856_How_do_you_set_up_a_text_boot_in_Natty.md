---
title: "How do you set up a text boot in Natty?"
date: 2011-05-05
forum: General Help
---

### Post by akand074 on 2011-05-05
Hey guys, 

I used to edit grub from /etc/default/grub and change this line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quite splash"
```

to 

```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```

But after doing that now in Natty I still get a graphical boot, the Ubuntu logo just doesn't show anymore, but it isn't a text boot. Anyone know how to get this to work?

---

### Post by wilee-nilee on 2011-05-06
Did you run the update-grub

---

### Post by akand074 on 2011-05-06
> **wilee-nilee said:**
> Did you run the update-grub

Yes.................................. please tell me I did :/ I'll run it again if this works I've officially gone mad.

---

### Post by akand074 on 2011-05-06
Well that's that. I guess you can only run update-grub so many times before it just wipes itself from your memory.

---

### Post by akand074 on 2011-05-06
I unmarked this thread from solved because I actually logged in after a text boot on my laptop this time and it asked me for my keyring password again because it failed to unlock? or something (which never happened before) anyways I put in my password and it continued and everything loaded except Unity! Basically I had a fully working desktop except no top panel or side dock. Anyone have the same issue or know why this is happening so I can fix it?

EDIT: Marked as solved as this questions isn't relevant and the thread is dead, just found it in my subscriptions.

---

