---
title: "Password reset on Ubuntu USB Install"
date: 2012-03-22
forum: General Help
---

### Post by 90civichb on 2012-03-22
I am sorry if I have posted this in the wrong section. Please forgive me.

I have a problem that I just can't seem to figure out. 

I was given a copy of ubuntu that is running on a bootable USB stick. Unfortunately, the person who gave me this USB installed copy gave me the wrong password for root. Everything they have told me to try has failed, and I cannot get root access on the installation.

If it were a basic installation, I would just reinstall and forget about it, but this particular installation has some tools on in that I cannot get access to otherwise.

The grub menu is set for a 0 timeout, so I can't see the menu to select recovery mode in order to change the password. Because it is a bootable USB stick, I also cannot figure out how to access the file system in order to manually copy, edit, and replace the shadow file with the password removed.

Does anyone have a solution to my problem? How can I get to recovery mode on a USB installation with a grub timeout of 0?

Any help would be greatly appreciated.

---

### Post by dave2001 on 2012-03-22
Just making sure.. have you tried holding the shift key down during boot to access the grub menu?

---

### Post by 90civichb on 2012-03-22
> **dave2001 said:**
> Just making sure.. have you tried holding the shift key down during boot to access the grub menu?

Absolutely. That brings me to the Ubuntu install menu, with no options for recovery or anything similar. If I press F6, I can see some advanced options (nothing for recovery).

Is there any trick from that menu to load the grub menu or some other method of recovery?

Thanks for the reply. I really want to get this figured out.

---

### Post by Cheesemill on 2012-03-22
> **90civichb said:**
> Unfortunately, the person who gave me this USB installed copy gave me the wrong password for root.

Ubuntu doesn't have a password for root, in fact logging in as root is disabled by default.
Instead have you tried using sudo?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dave2001 on 2012-03-22
Can you log in as a normal user? If so, and you really need root authority, then you can go into terminal and enter
```
sudo su
```and it will prompt you for YOUR password instead of the root password (which there shouldn't be anyway, Cheesemill is correct on that point). This command should give you root access that is more complete than using a sudo command. 

Please note that most tasks do not require this manner of root authority and simply using separate sudo commands is the preferred method.

---

### Post by Cheesemill on 2012-03-22
> **dave2001 said:**
> Can you log in as a normal user? If so, and you really need root authority, then you can go into terminal and enter
```
sudo su
```and it will prompt you for YOUR password instead of the root password (which there shouldn't be anyway, Cheesemill is correct on that point). This command should give you root access that is more complete than using a sudo command. 

Please note that most tasks do not require this manner of root authority and simply using separate sudo commands is the preferred method.
In fact you shouldn't really use 'sudo su' either, it can cause problems.
The preferred methd is to do:
```
sudo -i
```

---

