---
title: "sudo broken by me ?"
date: 2009-06-26
forum: General Help
---

### Post by Alf Stockton on 2009-06-26
I inadvertently did a 'sudo chown -R alf:root /home/..' and now if I try 'sudo chown -R adrian:root /home/adrian' the message I get is 'sudo: must be setuid root'.
Please tell me what I have broken and better yet, how do I fix it.:confused:

---

### Post by ad_267 on 2009-06-26
/home/.. Means the parent directory of /home, ie the root directory, /.

So you've made yourself the owner of the whole filesystem. I think you're pretty stuffed really. I'd just boot from a Live CD, recover all the data you need then reinstall.

---

### Post by Soul-Sing on 2009-06-26
recovery mode

```
ls -l /home/<yourname>
```

```
chown root:root /home/<yourname>sudo
```
```
chmod 4755 /home/<yourname>sudo
```

typ: ```
reboot
```

(could be /home or /home/<yourname> not sure)

---

### Post by Alf Stockton on 2009-06-26
I do not understand your
```

chwon root:root /home/<yourname>sudo

```
as there is no chwon......typo?
and /home/alfsudo does not exist. Please explain.

and if I try 
```

chmod 4755 /home/alf sudo // note the space

```
chmod: cannot access `sudo': No such file or directory

---

### Post by Soul-Sing on 2009-06-26
> **Alf Stockton said:**
> I do not understand your
```

chown root:root /home/<yourname>sudo

```
as there is no chwon......typo?
and /home/alfsudo does not exist. Please explain.

and if I try 
```

chmod 4755 /home/alf sudo // note the space

```
chmod: cannot access `sudo': No such file or directory

correction above in my post...typo
try: /home/sudo
or: /home/alf/sudo

---

### Post by ad_267 on 2009-06-26
I'm not sure either what leoquant is trying do do there, there is no /home/sudo file or /home/alf/sudo. But I don't think it will help you if you really did execute "sudo chown -R alf:root /home/.." because like I said, ".." means the parent directory. 

Try running "ls /home/.." yourself to see what I mean.

You could try "chown -R root:root /" and then "chown -R alf:alf /home/alf" but there are a lot of other system daemons and applications that have other users and have to own different files throughout the file system. Like I said it's probably easier to reinstall.

---

### Post by Alf Stockton on 2009-06-26
Sorry but you have lost me again.
What do you suggest I do with /home ????

---

### Post by Soul-Sing on 2009-06-26
recovery mode

Code:

```
ls -l /home/alf
```

Code:

```
chown root:root /home/alf/sudo
```

Code:

```
chmod 4755 /home/alf/sudo
```

typ:
Code:

reboot

(could be /home/sudo or /home/alf/sudo not sure)

---

### Post by ad_267 on 2009-06-26
I think maybe what leoquant means is this:

```
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
```

That would fix your problem of not being able to run sudo, but there will likely be heaps of other stuff messed up.

---

### Post by Soul-Sing on 2009-06-26
> **ad_267 said:**
> I think maybe what leoquant means is this:

```
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
```

That would fix your problem of not being able to run sudo, but there will likely be heaps of other stuff messed up.

Yes, probl....I tried to figure out if it was possible to "recover"/solve it. It isn't daily stuff this. Pfff.

---

