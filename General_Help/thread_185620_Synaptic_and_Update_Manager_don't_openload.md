---
title: "Synaptic and Update Manager don't open/load"
date: 2006-06-01
forum: General Help
---

### Post by rodrigo666 on 2006-06-01
Greetings.

Since the last boot, my Synaptic Package Manager and my Update Manager don't open.

When I click on it's icons to open it, I see on the bar a message saying something like "Iniciating Software" that lasts about five seconds and then nothing. It gets closed and my Synaptic or my Update Manager don't get open.

What happened? Everything else seems fine and load properly.
I'm running Dapper Drake beta and can't update it to the new version that is about to be released.

---

### Post by mlind on 2006-06-01
Check that your /etc/apt/sources.list is populated
(you may use [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) to generate new one)

If command
```

sudo update-manager

```
gives any warnings (other than apt "API not stable yet").

Also, try if *sudo apt-get update* works normally.

---

### Post by rodrigo666 on 2006-06-01
I tried "sudo apt-get update" and "sudo update-manager", both got me this message:

unable to lookup Pemtium750 via gethostbyname()

Maybe someone (I) messed up with my config?

---

### Post by mlind on 2006-06-01
was that /etc/apt/sources.list file okay?

does /etc/hostname contain the name of your system ?

and /etc/hosts look similar to
127.0.0.1 localhost localhost.localdomain *yoursystem name*

---

### Post by robbot5706 on 2006-06-01
The same thing is happening to me. I can't open software properties, and software manager doesn't check for updates.

---

### Post by rodrigo666 on 2006-06-02
Well, I had to re-install Ubuntu.

Now it's working fine.

---

