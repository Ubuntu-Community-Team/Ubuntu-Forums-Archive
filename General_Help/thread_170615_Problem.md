---
title: "Problem"
date: 2006-05-04
forum: General Help
---

### Post by whataboutbob85 on 2006-05-04
I just installed ubuntu linux on my computer and have been getting used to it. I have run into a slight problem though. I created my root password and then a normal account. I started up my computer and logged onto my account and it said I had possible updates to download. I clicked on the icon and it prompted me for my password. I entered the password for my normal account I was logged in as and nothing happened. I clicked on the icon a second time and nothing happened. I then rebooted the computer and logged back in again. I clicked on the icon again and when it prompted me for my password I entered the password for the root account. A message box popped up that told me I entered an improper password for the root account. I have no idea what to do because that is the correct password I entered for the root account and it doesn't seem to work. So right now I cannot currently change anything on the computer because I don't have access to the administrator account. Any help would be appreciated. Thanks.

---

### Post by aysiu on 2006-05-04
If you created a user *and* a root account, you did an expert install.

You don't appear to be an expert, so I would encourage you to do a regular install in the future.

For now, though, you may want to take a look at this document. It may help.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by neouser99 on 2006-05-04
you created a root password during the ubuntu installation?? (answered a second before me, and i guess it does let you do this in expert) unless there is an option that i missed when i installed, you can't do that.

the GUIs use gksudo, so when it asks for your password it is for the password that is currently logged in. as for nothing happened, i can't really say much if there weren't any errors. you can trying launching Synaptic or any other admin tools and see if gksudo is working there, otherwise something got hosed.

-neo

---

### Post by nanotube on 2006-05-04
since you installed in expert mode... that means your regular user is not added into the sudoers file (to allow it to run stuff as root).
can you post the output of the following command:
```
cat /etc/group |grep adm
```
and, as root
```
cat /etc/sudoers
```
and we will try to fix you up.

---

### Post by JoeMetal on 2006-05-05
Also, try going to the terminal and typing ```
sudo passwd root
```  That might let you change your root password.

---

