---
title: "how do you know what verison you are on?"
date: 2009-08-08
forum: General Help
---

### Post by beanco on 2009-08-08
This is a very simple question...

but I am dense and cannot figure out how to tell what version of Ubuntu I am on..

A friend/co-worker up graded me from feisty to Hardy, i think, and that is what I want to find out...

Robi

---

### Post by credobyte on 2009-08-08
System / About Ubuntu :)

---

### Post by beanco on 2009-08-08
> **credobyte said:**
> System / About Ubuntu :)

in systems all I have is

preferences

administration

help and support
gnome

quite


which is why i have no idea how to figure out what version this is... what to do? command line?

robi

---

### Post by credobyte on 2009-08-08
Then check this article: [http://ubuntu-tutorials.com/2007/01/27/how-to-find-your-ubuntu-or-kernel-version/](http://ubuntu-tutorials.com/2007/01/27/how-to-find-your-ubuntu-or-kernel-version/)

---

### Post by drs305 on 2009-08-08
System, Administration, System Monitor > System tab.

Or you can run these from the terminal:
```

lsb_release -a && uname -r

```

---

### Post by beanco on 2009-08-08
as I suspected I am on Hardy...

thanks

now why do i not have that option you listed in the system menue?

and now I have to figure out how to get vlc...

robi

---

### Post by Disident on 2009-08-08
to see distro version:
cat /etc/*-release

and to see kernel version:
cat /proc/version

---

### Post by Disident on 2009-08-08
> **beanco said:**
> ... how to get vlc...

robi

# aptitude install vlc
(or apt-get instad of aptitude)

---

### Post by Disident on 2009-08-08
And btw any particular reason he upgraded you to Hardy and not to Jaunty?

---

### Post by beanco on 2009-08-09
> **Disident said:**
> And btw any particular reason he upgraded you to Hardy and not to Jaunty?

he said it is better to take little steps rather than big leaps....

and htanks for the command. i will try it out.

robi

---

### Post by Disident on 2009-08-09
But Jaunty is also stable version, that's why I asked, and with newer repositories, so maybe it'll be better. It mostly depands on kernel and hardware support, but still I think Jaunty has it better than Hardy. And GNOME from Hardy to Jaunty hasn't changed that much (as Kubuntu Hardy - Jaunty which changed from KDE3 to KDE4).
But if you're satisfied with it it's good then :)

---

### Post by beanco on 2009-08-09
well i have only been on it for a few days an dhave not really used it much.

maybe I will just upgrade myself to jaunty....


robi

---

