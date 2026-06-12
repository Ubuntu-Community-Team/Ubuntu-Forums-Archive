---
title: "Custom App Launcher: code note working, why?"
date: 2010-01-19
forum: General Help
---

### Post by ripeart on 2010-01-19
Hi,

If in a terminal I run:

/usr/local/bin/speedometer -tx wlan0 -rx wlan0

It runs fine. It is an application that runs inside the current terminal session.

However when I put that command into a custom launcher applet assigned as a 'Application in Terminal', nothing happens. Things I've tried:

as Application in Terminal: gksu /usr/local/bin/speedometer -tx wlan0 -rx wlan0
as Application: gnome-terminal  /usr/local/bin/speedometer -tx wlan0 -rx wlan0

Any clues?

---

### Post by Cabs21 on 2010-01-19
did you give it proper permissions?

```
chmod +x Path/to/file/in/question.file
```

or am i reading your question wrong.

---

### Post by ripeart on 2010-01-19
Arrg!! I should have thought of that, it worked. Seems like a lot of things that can go wrong are permissions related.  Thanks!

OH btw, is there any security risk associated with chmodding it to 777?

Also, I don't understand why I would have to do this as I was logged in as root when creating and trying to launch it. Could this mean that 'root' didnt have permission to execute?

---

### Post by michy99 on 2010-01-19
When you create a script (which is just a text file) it does not have executable permission until you make it so. This is true for root as well as any other user.

---

### Post by lykwydchykyn on 2010-01-19
> **ripeart said:**
> Arrg!! I should have thought of that, it worked. Seems like a lot of things that can go wrong are permissions related.  Thanks!

OH btw, is there any security risk associated with chmodding it to 777?

Yes, don't do that.  755 should be adequate (and make sure root is the owner).  You don't want to make an executable script world-writeable, especially if you're going to run it as root.

---

### Post by ripeart on 2010-01-19
> **lykwydchykyn said:**
> Yes, don't do that.  755 should be adequate (and make sure root is the owner).  You don't want to make an executable script world-writeable, especially if you're going to run it as root.

Thank you for that, duly noted and changed. Is this because an attacker could modify this script to do other potentially harmful operations?

---

### Post by lykwydchykyn on 2010-01-19
> **ripeart said:**
> Thank you for that, duly noted and changed. Is this because an attacker could modify this script to do other potentially harmful operations?

Exactly.  If it's 777 anyone obtaining shell access to the system can modify it to do pretty much anything.  Granted, they'd have to first obtain shell access and identify the file.  But it's not hard to imagine a script searching for writable files in your $PATH to inject malicious code into.

---

