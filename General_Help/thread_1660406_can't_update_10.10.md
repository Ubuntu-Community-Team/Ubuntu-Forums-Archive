---
title: "can't update 10.10"
date: 2011-01-05
forum: General Help
---

### Post by Tadcrazio on 2011-01-05
the screen shot shows whats going on. Not sure what i have to do to correct it. Help would be appreciated.

---

### Post by NIN101 on 2011-01-05
There is some kind of error on line 59 in /etc/apt/sources.list. The Programm couldn't parse it because it isn't in the "right format". Post the sources.list if you wanna receive help.

---

### Post by Tadcrazio on 2011-01-05
> **NIN101 said:**
> There is some kind of error on line 59 in /etc/apt/sources.list. The Programm couldn't parse it because it isn't in the "right format". Post the sources.list if you wanna receive help.

My problem is I don't even know how to post the sources.list

---

### Post by happyhamster on 2011-01-05
Open a terminal (Applications-->Accessories-->Terminal), and type:
```

gedit /etc/apt/sources.list

```
That will open the file in your text editor.

---

### Post by Tadcrazio on 2011-01-05
looks like the problems revolves around Tor.. I tried installing it it, i didn't get far. and here is the result on line 59:



deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org)[ YOUR_DISTRO_VERSION] main

---

### Post by happyhamster on 2011-01-06
> **Tadcrazio said:**
> looks like the problems revolves around Tor.. I tried installing it it, i didn't get far. and here is the result on line 59:

deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org)[ YOUR_DISTRO_VERSION] main
Just put a # character in front of that line (it will turn into a comment, and will be ignored):
```

gksudo gedit /etc/apt/sources.list

```
And make that line look like:
```

# deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org)[ YOUR_DISTRO_VERSION] main

```
Save the file, and exit the text editor. Then run:
```

sudo apt-get update
sudo apt-get upgrade

```
Good luck.

---

