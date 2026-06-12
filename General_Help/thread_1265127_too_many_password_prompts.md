---
title: "too many password prompts"
date: 2009-09-13
forum: General Help
---

### Post by RFXCasey on 2009-09-13
I have a pretty long password for both root and user. Is there any why to cut down on constantly having to enter my password when in user mode? I have heard logging in as root is not safe.

---

### Post by rocket16 on 2009-09-13
You can grant your user account additional rights and other privileges. To do this, go to System->Administration->Users and Groups. Now, select your account, and grant it additional rights.

---

### Post by rocket16 on 2009-09-13
Another solution, though unsafe, is to make a shorter password. But even if you make it in GUI, it will take 6 chars minimum. To make the passwords shorter than 6 characters, just hear to trerminal, and type "sudo passwd name" where name is your account. Then the password can be anything. You can give short but strong passwords for your user. For example, 7532 is such a password. This is uncommon, since it is the reverse of the prime numbers from 1 to 10.

---

### Post by RFXCasey on 2009-09-13
The only rights I see are really lame ones like allow use floppy. They are all checked. Where do I find the detailed right? The closest thing I see to anything worth a crap is enable access to external storage device.

---

### Post by amac777 on 2009-09-13
Why do you constantly have to enter your password? (What are you doing that requires the password)?

---

### Post by DeMus on 2009-09-13
> **RFXCasey said:**
> I have a pretty long password for both root and user. Is there any why to cut down on constantly having to enter my password when in user mode? I have heard logging in as root is not safe.

Try using one of the Windows versions. No need to type your password there. You're administrator all the time.
But you know what happens when running a Windows OS? It crashes a lot.
So Linux is different: you are user and only when needed you type the password to become "root". This way things don't crash because it is much more safe to work this way.

So, when you don't want to type your password "all the time" skip to Windows. But be prepared to keep re-installing.

---

### Post by MelDJ on 2009-09-13
to perform administrative tasks, you must be root. but you should not run as root as it is a security hazard. so, to do the tasks, you have to ask root for permission by typing the password. this lets you do the task. its like vista but more more more safer

---

### Post by akakingess on 2009-09-13
> **RFXCasey said:**
> The only rights I see are really lame ones like allow use floppy. They are all checked. Where do I find the detailed right? The closest thing I see to anything worth a crap is enable access to external storage device.
It may not be the fact that you need to use the floppy, but just 'mounting' additional drives, media, etc. are protected to keep anything that you don't want attached being put onto or mounted into the system. Seems silly, but there is a method to the madness.

---

### Post by DeMus on 2009-09-13
> **MelDJ said:**
> to perform administrative tasks, you must be root. but you should not run as root as it is a security hazard. so, to do the tasks, you have to ask root for permission by typing the password. this lets you do the task. its like vista but more more more safer

Don't compare Linux safety with Vista please. In Vista the only thing you need to do is one extra mouse-click. As if that is safe. Plus, it can be switched off easily because Windows users don't like it. They want to have an unsafe OS. Well, let them have it. We have Linux!

---

### Post by jocko on 2009-09-13
> **RFXCasey said:**
> I have a pretty long password for both root and user. Is there any why to cut down on constantly having to enter my password when in user mode? I have heard logging in as root is not safe.
What do you do with your computer that constantly requires you to enter your password?

---

### Post by RFXCasey on 2009-09-14
I'm setting up an apache and sftp server among other things.

---

### Post by amac777 on 2009-09-14
Well, once you get your servers setup, you shouldn't need to enter your password in normal usage.

See the forum policy on root logins thread for some examples that you may find helpful:

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by earthpigg on 2009-09-14
hi,

type this, and enter your password once.

```
sudo su
```

you are now in a root terminal, and can run all the commands you want without being prompted for your password.

keep in mind, of course, that you are in a root terminal. 

the root terminal assumes you are God and incapable of any error.

any typos made here can completely ruin your system.

any mis-clicks in apps launched from this terminal can completely ruin your system.

---

### Post by RFXCasey on 2009-09-15
Thanks, I have a lot to learn.

---

