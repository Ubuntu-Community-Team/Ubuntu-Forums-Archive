---
title: "The sudo command without asking for password"
date: 2011-11-19
forum: General Help
---

### Post by radu992 on 2011-11-19
How can I set to all the users except for one in a group to have the right to use the sudo command without asking them the password in order to change the owner or the group to any file in the system? I think this might work with chown or chmod but I don't figure it out how it should work. Please help me.:)

---

### Post by MG&amp;TL on 2011-11-19
The whole point of the sudo command is that it allows a normal user to be root temporarily without being root themselves. 

On other systems than Ubuntu, they have a root account, or something like:

```
su
```

. I think the best thing you could do is make sure everyone is allowed to use sudo, and then let them use their own passwords.

---

### Post by dandnsmith on 2011-11-19
Look at the sudoers man page - should give the info required.

---

### Post by radu992 on 2011-11-19
I know it isn't very safe what I want to do but I have to do this. I don't want that some users to use their passwords when they use the sudo command.

---

### Post by Lampi on 2011-11-19
ubuntu for some reason recommends
```
sudo -s
```
to change user to root

... can't tell you the difference to a simple "su"

---

### Post by Elfy on 2011-11-19
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by lswb on 2011-11-19
> **radu992 said:**
> I know it isn't very safe what I want to do but I have to do this. I don't want that some users to use their passwords when they use the sudo command.

Have you considered all the ramifications of allowing all users to chown and chmod files without really having admin authority? It wouldn't be too far from just giving them full sudo rights anyway. For instance, a user could chown & chmod a system (or other user's) executable file or script such that he could delete it, then replace it with a malicious file of his own with the same name, then chown & chmod it back to normal. Just imagine for what could be done with password programs and utilities like gpg.

---

### Post by efflandt on 2011-11-19
File permissions of directories and files themselves determine whether a particular group or others can create, read, modify, or delete files in that directory.

However, if it is a mounted non-Linux file system, it may not have a method to keep track of directory or file ownership or permissions (like FAT32), so then it may depend upon mount options or fstab entry.

Be VERY cautious about changing ownership or permissions of system directories or files, because that can break your system.

---

### Post by MG&amp;TL on 2011-11-19
Is it possible to have multiple user logged in as root simultaneously? In which case that could be a solution.

---

### Post by Elfy on 2011-11-20
> **MG&TL said:**
> Is it possible to have multiple user logged in as root simultaneously? In which case that could be a solution.

No idea - but any help to get the OP logging in as root will cause the thread to get closed.

> **Our "line in the sand" is with tutorials or posts that show people how to LOG IN to a graphical desktop (gnome, KDE, etc) as root. This is completely inappropriate and unnecessary.**

---

### Post by MG&amp;TL on 2011-11-20
> **forestpiskie said:**
> No idea - but any help to get the OP logging in as root will cause the thread to get closed.

Obviously wasn't going to, if he asked I was going to point him to the rootsudo link. :)

---

### Post by Raweed on 2011-11-20
I am the only user on my laptop and no one else ever goes on it, how do I get sudo to stop asking me for a password?

---

### Post by Elfy on 2011-11-20
> **Raweed said:**
> I am the only user on my laptop and no one else ever goes on it, how do I get sudo to stop asking me for a password?

Read the links given earlier in the thread, though I would have to wonder why you need to remove it - I rarely have to give my password to the system.

---

### Post by Raweed on 2011-11-20
> **forestpiskie said:**
> Read the links given earlier in the thread, though I would have to wonder why you need to remove it - I rarely have to give my password to the system.

I'm new linux user so was just wondering how you would do it for learnings sake :)

---

### Post by Elfy on 2011-11-20
I'm afraid that I'm not going to help you do something that I don't agree with. 

There are other people in this thread - wait and see if one of them will do so :)

---

### Post by Lars Noodén on 2011-11-20
> **radu992 said:**
> How can I set to all the users except for one in a group to have the right to use the sudo command without asking them the password in order to change the owner or the group to any file in the system? I think this might work with chown or chmod but I don't figure it out how it should work. Please help me.:)

Allowing users to chown + chmod arbitrary files would be creating a backdoor into root access.  All they have to do is make a script that calls bash and then chown it and SUID.  

What problem are you really trying to solve?

---

