---
title: "I Broke most/all file permissions"
date: 2010-07-26
forum: General Help
---

### Post by Gawayn on 2010-07-26
Hi all,

Let me start off by saying I'm a complete moron.

Now that that's out of the way, I ran:
```
chmod o-rwx -R /* 
```

It seemed like a good thing to do at the time...
I was attempting to move in a direction where all users were restricted to their workspaces, but still had access to some/most command-line programs. I planned on running things like chmod o+rx -r /bin shortly after the first command...

In any event, I'd like to know if there is a reasonable way to "reset" permissions or fix permissions to be what they should so that other users can run commands like "ls".

***UPDATE:

I've now got other users' abilities to run commands fixed, my SVN is working, web services seem good.

I've got everything sort-of working again. All I need now is a good guide for improving security, jailing users (which I haven't been able to get to work), and the like.

Thanks,

-Gawayn

---

