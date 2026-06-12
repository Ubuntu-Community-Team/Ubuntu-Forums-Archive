---
title: "Disabling password protectection for recovery mode"
date: 2011-10-06
forum: General Help
---

### Post by community on 2011-10-06
I recently set the root password by the command

sudo passwd root

And now it asks for the password whenever I get into the recovery mode options.I need to disable the root password protection to the recovery mode.So I used the command 

sudo passwd -l root

And it displays 'Password information expiry changed'.
But now also it asks for the root pasword while taking the recovery mode and my current root password doesn't work now.What is the real problem?

---

### Post by dino99 on 2011-10-06
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

