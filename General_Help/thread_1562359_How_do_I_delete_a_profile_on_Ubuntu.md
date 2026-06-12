---
title: "How do I delete a profile on Ubuntu"
date: 2010-08-27
forum: General Help
---

### Post by Poltergiest on 2010-08-27
How do I delete a profile on Ubuntu 10.04. A friend of mine was over and he added a profile on my computer and now sudo doesn't work, and on top of that when I go to update my comp it never prompts me for my password and just restarts the Update Manager.

Please Help 

Sad and confused *Poltergiest*

---

### Post by akoskm on 2010-08-27
> **Poltergiest said:**
> How do I delete a profile on Ubuntu 10.04. A friend of mine was over and he added a profile on my computer and now sudo doesn't work, and on top of that when I go to update my comp it never prompts me for my password and just restarts the Update Manager.

Please Help 

Sad and confused *Poltergiest*

Hi!
You can delete Profiles under System > Administration > Users and Groups.,
What do you mean by "sudo doesn't work", it won't accept your password?
Hope this help.

---

### Post by Poltergiest on 2010-08-27
Okay it didn't help like I thought it would but thank you for the info and when I go into Terminal and type "sudo apt-get install updates it says sudo: /etc/sudoers is mode 0666, should be 0440
sudo: no valid sudoers sources found, quitting"

---

### Post by noex869 on 2010-08-27
sounds like it has the wrong permissions I would say try chmoding it but you would have to be sudo to do that.

---

### Post by akoskm on 2010-08-27
Of course, you need root access to chmod /etc.
I googled the terms /etc/sudoers is mode 0666, should be 0440, but the posts what I found usually ended either with /bump or with reinstalling the whole system.

---

### Post by pbrane on 2010-08-27
When you say "a friend added a profile" do you mean he/she created a new user? That shouldn't have affected your user account. Are you using your original user login?

This post is old but may help you.
[http://ubuntuforums.org/showthread.php?t=162867]("http://ubuntuforums.org/showthread.php?t=162867")

Basically your user account should be a member of 'adm' group. If you type ***groups*** in a terminal you should see something like
```

<your user name> **adm** dialout cdrom plugdev lpadmin admin sambashare

```
if the **adm** group is not present then thats your problem.

---

### Post by spjackson on 2010-08-27
> **Poltergiest said:**
> Okay it didn't help like I thought it would but thank you for the info and when I go into Terminal and type "sudo apt-get install updates it says sudo: /etc/sudoers is mode 0666, should be 0440
sudo: no valid sudoers sources found, quitting"
This needs to be corrected in order for sudo to work, and anything else that needs root access, such as Update Manager. You need root permission to correct it with
```
chmod 0440 /etc/sudoers
```In order to get root permission, you need to reboot and select recovery mode from the grub menu, then drop to a root shell. Then you will be able to run the above command.

However, this hasn't occurred purely as a result of adding a new user. Something else has been done, and I would be concerned about what else is broken.

A reinstall is often the quickest and most reliable way to fix file ownership and permission screw-ups in system directories.

---

