---
title: "apt dependency problem"
date: 2006-04-05
forum: General Help
---

### Post by jstritar on 2006-04-05
I needed the libsane version in the Dapper repository b/c it supports a new scanner I got. I downloaded it from [http://packages.ubuntu.com/dapper/libs/libsane](http://packages.ubuntu.com/dapper/libs/libsane) and then tried to install it with "sudo dpkg -i <pkgname>.deb". It failed due to un-met dependencies (presumeably also Dapper packages), and now I can't do anything with apt. It gives these errors when I try to remove or install anything:

```
libsane is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libsane: Depends: libgphoto2-2 (>= 2.1.6-5.2ubuntu3) but 2.1.6-1ubuntu6.1 is to be installed
           Depends: libgphoto2-port0 (>= 2.1.6-5.2ubuntu3) but 2.1.6-1ubuntu6.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

How do I get rid of this new libsane and go back to breezy's?

Also, if anyone knows how to get the 1.0.17 sane backends the correct way... let me know!

---

### Post by jstritar on 2006-04-05
I found the following thread about setting up the LiDE 60... so I just need to figure out how to get this error gone then I'll be set.

[http://ubuntuforums.org/showthread.php?t=153933&highlight=libsane](http://ubuntuforums.org/showthread.php?t=153933&highlight=libsane)

---

### Post by SeanTater on 2006-04-05
Have you done like it says and tried "apt-get -f install" with no quotes?
If so, you need to enable the breezy-backports repository in /etc/apt/sources.list, then do

"apt-get remove libsane"

then

"apt-get install libsane"


If the seconds command has problems, you may have a problem. You will need to upgrade to dapper, or be content with you are..

---

### Post by jstritar on 2006-04-05
fixed... just installed all the dependencies

---

### Post by jstritar on 2006-04-05
Oh... I did the -f option while trying to install libsane. I see...

---

