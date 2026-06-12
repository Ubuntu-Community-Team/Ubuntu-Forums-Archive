---
title: "gksu prompts for administrative password"
date: 2011-04-19
forum: General Help
---

### Post by apollothethird on 2011-04-19
Can someone advise me how to fix the problem that is happening with gksu.  It prompts me for the administrative password.  I don't (for advised security reasons) have a password associated with the root account.

The sudo works fine and accepts my sudo password.  Gksu fails with "incorect password... try again." error.

This is a new install of the Ubuntu Server 10.10 x64 Maverick edition.

Thanks in advance for any suggestions or comments.

By the way, I have Ubuntu working on 4 machines in my shop.  This is the first time I have experienced this problem.  It'll probably eventually go away on its own, but I'm really curious as to why this is happening and what I could do to immediately resolve the issue.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by sanderd17 on 2011-04-19
are you sure it's not a keyboard layout, or a numpad on-off problem?

Can you try to type your pwd without numpad and trying the different layouts you have installed?

---

### Post by ~Plue on 2011-04-19
gksu is probably set to use su instead of sudo.
if that is the case here, you could run *gksu-properties* and change the authentication mode to sudo

---

### Post by apollothethird on 2011-04-19
> **sanderd17 said:**
> are you sure it's not a keyboard layout, or a numpad on-off problem?

Can you try to type your pwd without numpad and trying the different layouts you have installed?

Thanks for the prompt diagnosis.  If it were a keyboard layout problem the sudo would also fail.


> **~Plue said:**
> gksu is probably set to use su instead of sudo.
if that is the case here, you could run *gksu-properties* and change the authentication mode to sudo

That was it.  I knew it would be something simple.  I had actually installed the Ubuntu server 3 times on the same computer and Ubuntu on 6 other computer in my network, please a few virtualbox experiments.  I also have Ubuntu installed on 3 USB drives formated to ext4 like a normal hard drive.  In all the times I'm surprised that this only happened in this instance, but glad to learn of the simple remedy.

Thanks!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by DrIdiot on 2011-04-28
I'm having the same issue.  I think Ubuntu previously used gksudo to launch programs such as Synaptic (from the main menu), which works fine.  But now it uses gksu, and when I type my password (not root password, my own) it doesn't accept it.

I tried:

1) sudo in command line; works
2) launching Synaptic using gksudo; works
3) launching Synaptic using gksu; doesn't work
4) changing gksu-properties as described above; the changes aren't kept (i.e. when I change the method from su to sudo, close it, and open it again, it's back to su)

Other than just setting the root password to my own, does anyone know how to fix this?

---

### Post by ~Plue on 2011-04-29
> **DrIdiot said:**
> 
4) changing gksu-properties as described above; the changes aren't kept (i.e. when I change the method from su to sudo, close it, and open it again, it's back to su)

run *sudo rm -r ~/.gconf/apps/gksu* (in case its a permission problem thats preventing the changes from bieng saved)
then as the normal user, try changing gksu-properties again

-good luck

---

### Post by sanderd17 on 2011-04-29
How can this be? for me, gksudo points to gksu, could you execute the next 3 commands?

```

which gksudo
which gksu
ls -al /usr/bin/gksu*

```

and give us the output?

My output looks as following:

```
sander@sander-narwhal:~$ which gksudo
/usr/bin/gksudo
sander@sander-narwhal:~$ which gksu
/usr/bin/gksu
sander@sander-narwhal:~$ ls -al /usr/bin/gksu*
-rwxr-xr-x 1 root root 22584 2011-02-23 16:22 /usr/bin/gksu
lrwxrwxrwx 1 root root     4 2011-04-29 09:05 /usr/bin/gksudo -> gksu
-rwxr-xr-x 1 root root  9688 2010-12-16 17:53 /usr/bin/gksu-properties
```

so you see gksudo is pointing to gksu.

---

