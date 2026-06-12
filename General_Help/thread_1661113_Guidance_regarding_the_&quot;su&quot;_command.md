---
title: "Guidance regarding the &quot;su&quot; command"
date: 2011-01-06
forum: General Help
---

### Post by raghav.venky on 2011-01-06
I Installed Ubuntu 10.10 yesterday.

To set up my Internet, i have to do a "su" in the terminal.It asks for a password. I type the password for the only user i have on this OS but i get an "authentication failure".

Please help.

---

### Post by sisco311 on 2011-01-06
Welcome to the forums!

The root account password is locked, so you can't use su. You have to use sudo.
See: [uhelp]community/RootSudo[/uhelp]

You can use Network Manager to set up your Internet connection:
[uhelp]community/NetworkManager0.7[/uhelp]

---

### Post by Lism on 2011-01-06
Sorry for butting in but im curious,
 
Can you explain the difference between the two commands. And what the root account actually is? I've heard it reffered to as the "Superuser" and you shouldn't use it unless you know what your doing. Why is this?
 
Thanks.

---

### Post by raghav.venky on 2011-01-06
So how do i become the root?

---

### Post by cgroza on 2011-01-06
You put "sudo" in front of the command to execute it with root privileges. The "su" command means switch user and if nothing folows it, the default is root. By default the root account has no password so you can't login to it.

---

### Post by mcduck on 2011-01-06
> **raghav.venky said:**
> So how do i become the root?

Read the root/sudo document sisco331 linked for you.

(short answer is you don't become root, but you can use *sudo* to run commands as root when you need to)

---

### Post by raghav.venky on 2011-01-06
When i try to execute the command with sudo, i get "command not found"
But when i try it without sudo, i get "permission denied"

here's wat i'm trying to do:
[http://www.techenclave.com/open-source-and-linux/howto-holding-hand-walkthrough-setting-up-83728.html#post519991](http://www.techenclave.com/open-source-and-linux/howto-holding-hand-walkthrough-setting-up-83728.html#post519991)

---

### Post by mcduck on 2011-01-06
> **Lism said:**
> Sorry for butting in but im curious,
 
Can you explain the difference between the two commands. And what the root account actually is? I've heard it reffered to as the "Superuser" and you shouldn't use it unless you know what your doing. Why is this?
 
Thanks.

"su" switches to another user, while "sudo" executes a command as another user.

From ubuntu user's point of view the big difference is that su authenticates by asking for the *target user's password*, while sudo asks for *your own password* and then checks if your user has been given permissions to execute the task as target user. Since Ubutnu's security model disables the root account, it has no password and therefore you can't use "su" to switch to root.

(If you want to open a root session in a terminal, you can do that by running "sudo -i" instead of "su -")

..and the root account is the all-powerful user account on a Linux/Unix system. One that owns the system itself, and has the permissions to do anything. Including things that will break your system to completely unrecoverable state. There is very rarely any actual need for anybody to use root account directly, and never any reason to use it on desktop. So you shouldn't think of it as any type of power user account, anybody with any skills knows very well that they don't need to and shouldn't have such power all the time. ("minimum force required" is pretty much the base of security on Linux/Unix systems)

---

### Post by mcduck on 2011-01-06
> **raghav.venky said:**
> When i try to execute the command with sudo, i get "command not found"
But when i try it without sudo, i get "permission denied"

here's wat i'm trying to do:
[http://www.techenclave.com/open-source-and-linux/howto-holding-hand-walkthrough-setting-up-83728.html#post519991](http://www.techenclave.com/open-source-and-linux/howto-holding-hand-walkthrough-setting-up-83728.html#post519991)

The Network Manager should be able to handle PPPoE, have you tried it before trying to do this?

Anyway, you didn't actually tell what command you tried to run when you got those errors, but "command not found" means that either you mistyped a command, or you are trying to execute a file but aren't actually in the directory where the file is located.

"permission denied" would sound like trying to execute a file that hasn't been set to be executable.

Anyway, the guide you are following is quite old, and for a different Linux distribution.

---

### Post by Lism on 2011-01-06
> **mcduck said:**
> Since Ubutnu's security model disables the root account, it has no password and therefore you can't use "su" to switch to root.

Hmm.. I just used: 

```
sudo su root
``` and it worked, so in my limited ubuntu experience, the only thing stopping people from screwing your system is the password used to log on at system bootup.

---

### Post by sisco311 on 2011-01-06
> **Lism said:**
> Hmm.. I just used: 

```
sudo su root
``` and it worked, so in my limited ubuntu experience, the only thing stopping people from screwing your system is the password used to log on at system bootup.

By default, only users in the **admin** group are allowed to use sudo.

The preferred method for starting a root shell is:
```
sudo -i
```
To exit from the shell, run:
```
exit
```or press Ctrl+d.

**sudo su** works because root is allowed to use su without a password.

---

### Post by QLee on 2011-01-06
[QUOTE=Lism]Hmm.. I just used: 

```
sudo su root
``` and it worked, so in my limited ubuntu experience, the only thing stopping people from screwing your system is the password used to log on at system bootup.[/QUOTE]

OK, so what's your point?

Unless you are using biometric or other hardware authentication anyone sitting at the console with the sys admin's password can do what they want to a system. Because that's what the sudo user is, sys admin. A regular user doesn't have sudo-foo, only has rights assigned by someone with sudo rights. Pretty much like most secure, multi-user, operating systems.

---

### Post by Lism on 2011-01-06
I've only just started using linux, so please forgive my newbie questions.

I see now, you can assign user groups. I didn't see this before and thought any account could use the sudo or su command (which could potentially screw your machine.)

Thanks it's all good now.

---

