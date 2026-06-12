---
title: "Can I use File Manager as root"
date: 2009-12-17
forum: General Help
---

### Post by swb_mct on 2009-12-17
(Current Ubuntu Server w/ Gnome added) 
Not being too sharp in the Linux command line, I just spent 2 hours organizing the directories and files for a web site.  It would have taken about 2 minutes if I could run the File Manager GUI as root.  Can that be done ?   thanks

---

### Post by cormano on 2009-12-17
try gksu nautilus.
You might have to install gksu first if installing gnome didnt enforce its installation.
Less pretty way would be sudo nautilus from a terminal.

---

### Post by northern lights on 2009-12-17
```
gksu nautilus
```will do what you want. However, I'd strongly advise against getting into the habit of using nautilus that way regularly.

Websites do not necessarily need to reside in */var/www/* anyhow. You can point your apache2 to any folder, also inside /home.

Further you could have done the rearranging in /home, then copied the finalized arrangement once.

---

### Post by northern lights on 2009-12-17
> **cormano said:**
> try gksu nautilus.
Please enclose code in code tags (hash/pound button above)

> **cormano said:**
> You might have to install gksu first if installing gnome didnt enforce its installation.It's pre-installed.

> **cormano said:**
> Less pretty way would be sudo nautilus from a terminal.Not only less pretty, but dangerous. Please never suggest to start a graphical app with *sudo*.
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by cormano on 2009-12-17
> **northern lights said:**
> Please enclose code in code tags (hash/pound button above)

It's pre-installed.

Not only less pretty, but dangerous. Please never suggest to start a graphical app with *sudo*.
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

Point 1. Ok
Point 2. I wasn't sure, and i'm still not, since he is using the server install with gnome manually added.
Point 3. Didn't know that, point taken.

---

### Post by cj13579 on 2009-12-17
If you put your pages in a folder called public_html in your home directory you can access your pages using:

```
http://ipaddress/~username/
```

Obviously replacing "username" with the username of the person's home directory you want to acces.

Also note that the "~" character is important!

---

### Post by laceration on 2009-12-17
Install the package nautilus-gksu.  You will then be able to r-click a folder + open it with "open as administrator".  This will do exactly what you are asking for.
As already suggested, putting your web files in home is the way to go.

---

