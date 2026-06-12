---
title: "input output error"
date: 2009-09-12
forum: General Help
---

### Post by texas.chef94 on 2009-09-12
I re-installed 9.04 from a live CD that has served me well in past. This is a 32 bit unit and the version is likewise.
The update was quite large (FYI) and when attempting to open a program I receive a error msg "error launching app, failed to execute child process /usr/bin/grome-apt-install" (input output error)
If the solution involves adding entries into file system please be very specific in the how to or point me to a solution resource

Thank you

---

### Post by khelben1979 on 2009-09-12
Does this affect all the applications you're trying to open? If not, specify which one.

---

### Post by texas.chef94 on 2009-09-12
> **khelben1979 said:**
> Does this affect all the applications you're trying to open? If not, specify which one.

Thank you for the quick response. I tried it on Firebox and Evolution and received the error so I thought I would reboot slow a lot of dev/dsa sector errors. So impatiently powered off, rebooted to debian sent the forum post.
Booted back again into ubuntu no error messages, but get this I had to log into the forum to answer this as I could not be redirected in g-mail. So strange things happening. At 77 years old it does not take much to set me off:P
Thanks again and advise if you have what could or might be going on

---

### Post by khelben1979 on 2009-09-12
> **texas.chef94 said:**
> At 77 years old it does not take much to set me off:P

It's probably better for the health to be using Linux than Windows in your age. :popcorn:

In any case, if you decide to go for a new installation of Ubuntu, then installing from a LiveDVD will give you much more software for a start where everything is supposed to work correctly. [Here you a link for it]("http://www.ubuntu.com/getubuntu/downloadmirrors#dvd") in case you're interested.

---

### Post by paradigm2 on 2009-09-12
> **texas.chef94 said:**
> Thank you for the quick response. I tried it on Firebox and Evolution and received the error so I thought I would reboot slow a lot of dev/dsa sector errors. So impatiently powered off, rebooted to debian sent the forum post.
Booted back again into ubuntu no error messages, but get this I had to log into the forum to answer this as I could not be redirected in g-mail. So strange things happening. At 77 years old it does not take much to set me off:P
Thanks again and advise if you have what could or might be going on

I would first run a memory check using the ubuntu LiveCD and selecting the memory check.

Then once you boot up go to a terminal and type:

```

sudo touch /forcefsck
sudo shutdown -r now

```

This will reboot and force a check of the filesystem.  

Even if it appears to be working ok now, it might nto have checked your filesystem,

---

