---
title: "How do you get/set permissions"
date: 2009-10-20
forum: General Help
---

### Post by hswaters on 2009-10-20
I am new to Ubuntu having just installed it.  I know that when you install windows the first person to enter their name has administrative powers.  This does not seem to be the case with Ubuntu.  I find that I cannot change from one folder to he other because I keep getting te message "permission denied".  What do I have to do to get permission move around from folder to folder?

---

### Post by shaon3343 on 2009-10-20
go to System==> adminstration==> User and groups

I think you can solve your probs by modifying the user priviliges of your current account.

---

### Post by The Cog on 2009-10-20
This should explain:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mcduck on 2009-10-20
> **hswaters said:**
> I am new to Ubuntu having just installed it.  I know that when you install windows the first person to enter their name has administrative powers.  This does not seem to be the case with Ubuntu.  I find that I cannot change from one folder to he other because I keep getting te message "permission denied".  What do I have to do to get permission move around from folder to folder?

The first user created in Ubuntu has administrative permissions. But the thing here is that the user doesn't run with full admin privileges all the time, but instead has the ability to gain those privileges temporarily, by asking for them and confirming with his password. In command-line this is done by using the "sudo" command.

The link that The Cog posted above will explain this in greater detail.

---

### Post by hswaters on 2009-10-21
Thanks for the help.  I will give it a try.

---

