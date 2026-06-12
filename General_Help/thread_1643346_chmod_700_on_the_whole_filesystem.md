---
title: "chmod 700 on the whole filesystem"
date: 2010-12-11
forum: General Help
---

### Post by thode on 2010-12-11
Well I did something really stupid:
sudo chmod 700 -R /

Why? because it's late and I'm tired and somehow thought it was only on my current dir...

Is this somehow fixable? I don't get my usual loginscreen so I guess through an tty?

---

### Post by dcstar on 2010-12-11
> **thode said:**
> Well I did something really stupid:
sudo chmod 700 -R /

Why? because it's late and I'm tired and somehow thought it was only on my current dir...

Is this somehow fixable? I don't get my usual loginscreen so I guess through an tty?

You have hosed your system, boot off a Live CD and salvage your /home folder (if you want to keep it) and reinstall.

---

### Post by warfacegod on 2010-12-11
It *might* work if you chown everything back to root ownership and afterwards chown your /home to your username.

---

### Post by thode on 2010-12-12
Don't really need to salvage something. All important things are on my desktop pc and got a backup for the laptop, although a lot has changed since then so I'll try warfacegod's solution first as it will be a lot faster if successful.

Thx for the answers!

---

### Post by ivarn on 2010-12-12
just set everything but the home folder back to root permission. select all the folders, right click, preferences > permissions.

---

### Post by warfacegod on 2010-12-12
> **warfacegod said:**
> It *might* work if you chown everything back to root ownership and afterwards chown your /home to your username.

```
sudo chown -R root:root /
```

```
sudo chown -R username:usergroup /home/username
```

---

### Post by HermanAB on 2010-12-12
Howdy,

Enjoy your nice new freshly installed system...

If it will make you feel better, I did something like that about 15 years ago.  You only do it once.

---

### Post by jwbrase on 2010-12-12
I don't think it will work. Certain files require specific octal permissions, and your own user and root aren't the only two on the system. Certain programs have their own demo users. You could, in theory, restore all ownerships and permissions to their proper values manually, but a reinstall would be quicker and less frustrating.

---

### Post by SPr on 2010-12-12
nm.

Misread the OP.

---

### Post by wojox on 2010-12-12
+1 Reinstall 

Things like your directory /tmp and /opt is owned by root but most of the stuff inside is owed by you or root.

You'll go nuts trying to figure it all out and spend days doing it. ;)

---

### Post by Krytarik on 2010-12-12
Ok, I have to say some now (I followed this thread since yesterday).

**You don't have to touch the ownership of the files at all** (through chown), because you haven't changed them in the first place. You did "only" change the file permissions (through chmod).

If you want a quick temporary way to get inside your desktop, you could do
```
sudo chmod 777 -R /
```
**which brings of course a significant security risk.**

Thus I would also strongly recommend a fresh install after you have saved your files, which of course can also be done via a Live-CD/Install-CD.

---

### Post by jwbrase on 2010-12-13
> **Krytarik said:**
> Ok, I have to say some now (I followed this thread since yesterday).

**You don't have to touch the ownership of the files at all** (through chown), because you haven't changed them in the first place. You did "only" change the file permissions (through chmod).

If you want a quick temporary way to get inside your desktop, you could do
```
sudo chmod 777 -R /
```
**which brings of course a significant security risk.**

It doesn't just bring a security risk: Certain programs (like sshd, for instance) simply won't run if certain configuration files are world or group writable. Also, from looking at accounts of similar incidents on the web, it seems that setuid bits tend to get unset in such instances, which is going to wreak havoc itself. A fresh install is about all one can do...

---

### Post by warfacegod on 2010-12-13
> **Krytarik said:**
> Ok, I have to say some now (I followed this thread since yesterday).

**You don't have to touch the ownership of the files at all** (through chown), 

I didn't say it *would* work only that it *might*. I fully expect the only cure for this is a new install. However, trying a few things out first can't make things worse. (Aside from actually deleting OS files.)

---

### Post by Krytarik on 2010-12-13
> **jwbrase said:**
> It doesn't just bring a security risk: Certain programs (like sshd, for instance) simply won't run if certain configuration files are world or group writable. Also, from looking at accounts of similar incidents on the web, it seems that setuid bits tend to get unset in such instances, which is going to wreak havoc itself. A fresh install is about all one can do...
I just yet did a little research about the special permissions (sticky bit, suid, sgid) and the effect of issuing octal permissions to those: by issuing the command "sudo chmod 700 -R /" like thode did all special permissions get unset. Thus you are right, that even changing now to "777" maybe would not bring thode's system back to life.

---

