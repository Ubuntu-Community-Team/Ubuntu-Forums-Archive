---
title: "ugh ms core fonts"
date: 2009-11-25
forum: General Help
---

### Post by tons-of-funs on 2009-11-25
there seems to be some hang up with the ms core fonts and its hindering me from properly installing just about anything, i cant install wine or flash plugin and its very annoying anyone experiencing the same problem or have a fix for this? google does not seem to get that i have a problem with this and show websites with viable solutions.

---

### Post by harfa on 2009-11-25
what error leads you to believe ms core fonts are interfering with anything, and you shouldn't be too surprised that the google search engine cannot read your mind. it can only go off your search terms and if they are as vague as your post, it won't be going far...

---

### Post by Mr. Devil on 2009-11-25
How to fix .. what ? Please post a little bit more information about what's happening there ( errors ).

---

### Post by coffeecat on 2009-11-25
A lot of people seem to be affected by this issue. It's something to do with DNS resolution of the Sourceforge server which serves up the actual font files.

Have a look at post #1 of this thread:

[http://ubuntuforums.org/showthread.php?t=1317661&highlight=ttf-mscorefonts](http://ubuntuforums.org/showthread.php?t=1317661&highlight=ttf-mscorefonts)

It's also made it as a bug report:

[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

See post #21 for an alternative fix.

---

### Post by tons-of-funs on 2009-11-25
> **harfa said:**
> what error leads you to believe ms core fonts are interfering with anything, and you shouldn't be too surprised that the google search engine cannot read your mind. it can only go off your search terms and if they are as vague as your post, it won't be going far...
you must not use google very often, if you type in anything very specific you will either get no answers (looking for all of your words in an exact match) or you will get a bunch of answers all containg a word or so of what you searched,cheers

---

### Post by tons-of-funs on 2009-11-25
> **coffeecat said:**
> A lot of people seem to be affected by this issue. It's something to do with DNS resolution of the Sourceforge server which serves up the actual font files.

Have a look at post #1 of this thread:

[http://ubuntuforums.org/showthread.php?t=1317661&highlight=ttf-mscorefonts](http://ubuntuforums.org/showthread.php?t=1317661&highlight=ttf-mscorefonts)

It's also made it as a bug report:

[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

See post #21 for an alternative fix.
thank you for understanding the problem i am having. i will try your work around and let you know how it worked

---

### Post by wojox on 2009-11-25
```

sudo gedit /etc/hosts

```

Add:
```

216.34.181.59 downloads.sourceforge.net
212.219.56.167 kent.dl.sourceforge.net

```

---

### Post by tons-of-funs on 2009-11-25
ok this is the error message i have and still am getting ```
E: ttf-mscorefonts-installer: subprocess installed post-installation script returned error exit status 1
```

---

### Post by tons-of-funs on 2009-11-25
> **wojox said:**
> ```

sudo gedit /etc/hosts

```Add:
```

216.34.181.59 downloads.sourceforge.net
212.219.56.167 kent.dl.sourceforge.net

```
at the bottom, top or anywhere?

---

### Post by wojox on 2009-11-25
Right under 127.0.0.1

---

### Post by tons-of-funs on 2009-11-25
after i did that i still get the error

---

### Post by wojox on 2009-11-25
Here's a few more:

```

213.203.218.122 mesh.dl.sourceforge.net
208.122.28.29 voxel.dl.sourceforge.net
212.219.56.167 sunet.dl.sourceforge.net
213.203.218.122 sunet.dl.sourceforge.net
208.122.28.29 sunet.dl.sourceforge.net

```

---

