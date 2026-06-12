---
title: "help me please with permissions problems"
date: 2006-03-07
forum: General Help
---

### Post by brickbat on 2006-03-07
Hi, I made a big mistake and now my system is unusable.

I set permissions to my whole /usr directory and all subdirectories 777.  Now I cannot sudo anything and su doesn't work by default. Anything requiring root access doesn't work anymore. 

Can someone please tell me what to do to fix this?

---

### Post by aysiu on 2006-03-07
If you can't *sudo* anything, that could be a problem.

Can you boot into recovery mode? Do you have a live CD?

If you can boot into recovery mode, you should be root. At that point, type ```
chmod -R 755 /usr
```

If you have a live CD, you can mount your drive as root and change the permissions there.

---

### Post by brickbat on 2006-03-07
thanks. i did it but it is still not working.

---

### Post by rfruth on 2006-03-07
So you are able to gain root & run chmod ?

---

### Post by brickbat on 2006-03-07
yes but when i go into my own login, it wont let me sudo or update or run a root terminal.

---

### Post by rfruth on 2006-03-07
does "sudo -s" work ?

---

### Post by brickbat on 2006-03-07
This is the error I get;

sudo: must be setuid root

---

### Post by rfruth on 2006-03-07
So how do you gain root access, recovery mode or using a live CD ?  Why does this remind me of pulling hens teeth ?  Spill it, I may not have the answer but someone else may if enough details are supplied.

---

### Post by brickbat on 2006-03-07
recovery mode. i didn't have a live cd so i tried the recovery mode first and it worked.

---

### Post by The Warlock on 2006-03-07
You need to make /usr/bin/sudo setuid root, because that's how it works. I don't remember how off the top of my head, though. Sorry.

---

### Post by brickbat on 2006-03-08
It didn't work.  I'm going to have to reinstall I think.  I'm also getting an error that Hal didn't start and another error that dbus needs hal

The command for setuid root is

chmod 4111 /usr/bin/sudo

---

