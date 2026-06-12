---
title: "Win4Lin asks for root to install -- How?"
date: 2006-05-16
forum: General Help
---

### Post by Delphi123 on 2006-05-16
Dear friends:

Win4Linux 5.1.7 asks me to login as "root" in order to complete my installation. I recall from the past that this was done by actually logging into KDE as root. Well, there is no root in (K)Ubuntu. Only the user and his password. What is the solution, please? Confused. Please be as precise as possible. I would consider installing a deb package but only if it came from our Adeptor or or its repositories and was fully approved by KUbuntu. Otherwise, I would rather just install it with a workaround to this matter of "root". There has got to be a solution.

Would appreciate your help kindly.

Thank you.

Benjamin

---

### Post by bluevoodoo1 on 2006-05-16
Perhaps this might be of some assistance?

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by bluevoodoo1 on 2006-05-16
double post - delete.

---

### Post by Delphi123 on 2006-05-16
Dear Bluevoodoo1 and friends:

I printed out the full instructions for root login that you provided in your link and studied them carefully. I then tried to apply them step by step. The problem is that when you open the /etc/kde/kdmrc file and change "false" to "true" in line 246 you are then told that you do not have write permissions to SAVE it. So, I am stuck. In order to save it I need the root password. But that is the whole point. How do I change Kubuntu so that I can log in as root as in most other Linux distros. I love Kubuntu and would just like to make that change. I'd feel a lot more comfortable with having root login privileges and it would allow me more flexibility.

Thank you so much.

Benjamin

---

### Post by gitargr8 on 2006-05-16
You need to give your text editor super user persmissions.
Run
```
kdesu kate&
```
from the terminal and edit your file. You'll now be able to save it.

---

### Post by Delphi123 on 2006-05-17
Dear gitargr8 and friends:

I am having second thought about changing "false" to true" in the kdmrc file. First of all, I do NOT know the root password, so how will it help me to log in as "root" if I know only the username. How do I add a root password in order to make use of this feature.

Secondly, what are the consequences of having access to Kubuntu's root and password. I don't mean the usual warnings about running Linux as root. I am very familiar with this and have learned how to use root and user in other Linux distros. But this is the first distro I've encountered where there is no root at all or at least where it is hidden from all users. So, I'd rather not to mess with Ubuntu's file system, etc. if possible unless this is a real option available to those who wish to make use of it.

I'd appreciate a brief clarification. Better to be safe than sorry.

Thank you.

Benjamin

---

### Post by pclapham on 2007-04-18
Here's how I did it:  
sudo passwd //opens the password file; asks for your sudo password to change root password.   Insert the new root password.  Type it in again to confirm.  Done.

To get to the system as root, log on as normal, then in a terminal type su It will ask for the root password.  As su, you are superuser (i.e. root).

That's all there is to it.

---

