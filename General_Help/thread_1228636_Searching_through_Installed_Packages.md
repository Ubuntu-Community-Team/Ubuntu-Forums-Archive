---
title: "Searching through Installed Packages"
date: 2009-08-01
forum: General Help
---

### Post by Buce on 2009-08-01
So, I know that 'apt-cache search' will search for packages that exist in the repositories. Is there a command that will search for packages installed on your computer?

For anyone who's used Arch, I'm basically trying to find 'pacman -Qs' (and -Qi, if possible) functionality in apt.

---

### Post by TuckLive on 2009-08-01
I haven't tried this command, but you can try

```
dpkg --get-selections
```

I found it here:

[http://www.howtogeek.com/howto/linux/show-the-list-of-installed-packages-on-ubuntu-or-debian/]("http://www.howtogeek.com/howto/linux/show-the-list-of-installed-packages-on-ubuntu-or-debian/")

---

### Post by Buce on 2009-08-01
Hm. I was hoping there'd be something that would output the same info that 'apt-cache search' does, but I suppose I can just use the output of dpkg with apt-cache to get the result I want. Thanks!

---

