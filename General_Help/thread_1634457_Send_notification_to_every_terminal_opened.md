---
title: "Send notification to every terminal opened?"
date: 2010-11-30
forum: General Help
---

### Post by hd21cn on 2010-11-30
I am using pine as email client for a while, and I noticed that if I got a new email, all terminal opened will show a notification if you type any command.

I just wondering is there any tool/command I can customize my own notification like this and work combine with crontab?

I search google for a little bit, no useful clue so far?

Any one has any idea?

Thanks!

---

### Post by DaithiF on 2010-11-30
```
echo "some message" | wall

```

---

### Post by hd21cn on 2010-12-07
> **DaithiF said:**
> ```
echo "some message" | wall

```

Thanks for your reply, but the wall thing is kind of over powered, it sends to all terminal opened(I know, it's my words), even those ssh to another server or those terminal with vi opened.

Is anything like windows system tray balloon notifications?

---

### Post by matt_symes on 2010-12-07
Hi

I am a bit confused here. What exactly do you want to do and why?

I think we need some background information.

Kind  regards

---

