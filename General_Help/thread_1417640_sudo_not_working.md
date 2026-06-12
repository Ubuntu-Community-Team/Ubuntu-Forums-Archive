---
title: "sudo not working"
date: 2010-02-27
forum: General Help
---

### Post by trozamon on 2010-02-27
Ubuntu won't let me use the sudo command in terminal.  If I try, sudo: must be setuid root pops up.  Also, if I try any tasks that require permission, the authentication box pops up and then disappears within one second.  I can't do anything anymore.  What do I do?

---

### Post by cjhabs on 2010-02-27
My guess is that the permissions on /usr/bin/ssudo are wrong and you no longer have the set uid bit. It should be:
-rwsr-xr-x
user and group are root.
You will have to change this from a live cd.

---

### Post by trozamon on 2010-02-27
I'm sorry; I'm still a newbie.  Please explain a little more in-depth.
Thanks.

---

### Post by cjhabs on 2010-02-27
sudo is a special program that allows execution of programs as the root user. To do this, it must have special permissions set that allow it to run as the root user.
Do:
ls -l /usr/bin/sudo
and post the result here.

---

### Post by trozamon on 2010-02-28
It says:

---s--x--x 2 alec users 123504 2010-02-25 18:22 /usr/bin/sudo

alec is my username.  "/usr/bin/sudo" is highlighted with red.

---

### Post by 3rdalbum on 2010-02-28
> **trozamon said:**
> It says:

---s--x--x 2 alec users 123504 2010-02-25 18:22 /usr/bin/sudo

alec is my username.  "/usr/bin/sudo" is highlighted with red.

Uh oh... sudo is owned by you.

You didn't, uh, 'chown' the whole filesystem so that all the files are owned by you?

What you'll need to do is boot up in recovery mode. From the GRUB boot menu, choose the Ubuntu entry that has "Recovery Mode" in the name. This will give you a command-line as root, I think (been a few years since I've used it).

These two commands might fix it:

```
chown root:root /usr/bin/sudo
chmod 655 /usr/bin/sudo
```

The first makes 'sudo' owned by both the user 'root' and the group 'root'. The second sets the exact permissions that sudo has on my computer, including the "setuid" flag. Setuid means that the program will be run with the file owner's permissions, not the permissions of the user who runs it. The file owner will be root.

---

### Post by Richard1979 on 2010-02-28
chmod u+s /usr/bin/sudo

---

### Post by trozamon on 2010-02-28
neither of these worked.

Im also unable to install drivers:the box for my password comes up for less than a second, then disappears.

---

### Post by cjhabs on 2010-02-28
What are the permissions on sudo now?

---

### Post by trozamon on 2010-03-01
it now says:

-rw-r-xr-x 2 root root 123504 2010-02-25 18:22 /usr/bin/sudo

/usr/bin/sudo is in green now.

---

### Post by nothingspecial on 2010-03-01
> **3rdalbum said:**
> 

You didn't, uh, 'chown' the whole filesystem so that all the files are owned by you?


I think this question is worth repeating.

---

### Post by sisco311 on 2010-03-01
> **trozamon said:**
> it now says:

-rw-r-xr-x 2 root root 123504 2010-02-25 18:22 /usr/bin/sudo

/usr/bin/sudo is in green now.

```
chmod 4755 /usr/bin/sudo
```

> **nothingspecial said:**
> I think this question is worth repeating.

+1

@OP: What's the output of```
ls -al {/usr,}/{s,}bin
```

---

### Post by cjhabs on 2010-03-01
I think you missed a step:
chmod u+s /usr/bin/sudo
this will set the setuid bit - you _need_ that.
Permissions should be:
-rwsr-xr-x 2 root root 143736 2010-02-25 18:27 /usr/bin/sudo
You are missing the "s" for the owner.

---

### Post by trozamon on 2010-03-01
to all of you:THANKS!!!!!!!!
 
for some reason, sudo now works. thank you.
 
However, I want to update some drivers. when i try to do that, the box to authenticate the action pops up and disappears after half a second.
ls -l /usr/bin/sudo yields:
-rwSr-xr-x 2 root root 123504.
 
what is wrong?

---

