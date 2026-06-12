---
title: "Issue with APT claiming package is installed when it's not"
date: 2011-09-27
forum: General Help
---

### Post by M1GEO on 2011-09-27
Hi all.

I have an odd issue that I've never encountered before in the last 8 years of my using Debian-based distros.

For some reason, APT seems to have it in it's head that a program (in this case, FFMPEG) is installed, but it's not.  I have all of the -dev libraries for libav* because I was writing software using them, but never had the ffmpeg package installed.  Now when I come to use ffmpeg for something on the commandline, I get the following:

```
$ ffmpeg
The program 'ffmpeg' is currently not installed.  You can install it by typing:
sudo apt-get install ffmpeg
```

But the usual install via APT gives the following:

```
$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ffmpeg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

If anyone can help with this, I would greatly appreciate it.

Kind Regards :)

---

### Post by matt_symes on 2011-09-27
Hi

This one seems a bit odd. Can we get the output of

```
dpkg -l | grep ffmpeg
```

to see what dpkg thinks.

Kind regards

---

### Post by M1GEO on 2011-09-27
Not to worry.  I've fixed it.  For the record, using APT to "uninstall" the package and then reinstalling fixed the issue.

---

