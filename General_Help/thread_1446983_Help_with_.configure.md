---
title: "Help with ./configure ?"
date: 2010-04-04
forum: General Help
---

### Post by PsychoDevon on 2010-04-04
Hello. I am trying to follow this tutorial below so that I can get Text to the right of icons on the GNOME desktop.

[http://pastebin.com/f3f29fcec](http://pastebin.com/f3f29fcec)

Everything so far has worked fine, except when I get to step 3 where I compile Nautilus.

When I try to run the command

./configure --prefix=/usr

It tells me

bash: ./configure: No such file or directory

What do I do here?

---

### Post by Naitsirhc Hsem on 2010-04-04
are you in the nautilus install directory, cd ~/nautilus-(version)/

---

### Post by PsychoDevon on 2010-04-04
> **Naitsirhc Hsem said:**
> are you in the nautilus install directory, cd ~/nautilus-(version)/


Aaaah...that was the problem.

I was one folder too deep into that directory.

It's always the simple mistakes that mess me up with long commands like these.

---

### Post by Naitsirhc Hsem on 2010-04-04
Thats fine, it happens to me all of the time

---

### Post by ibuclaw on 2010-04-04
Since you are downloading the debian source, why not create a package instead?

It's simple, instead of:
```

./configure
make
sudo make install

```
You instead run:
```

dpkg-buildpackage -rfakeroot

```
cd up a directory and install the .deb files needed.

Afterwards, it's a good idea to lock the package in synaptic to prevent it being upgraded.

Regards
Iain

---

### Post by PsychoDevon on 2010-04-04
Thank you, but I got the issue fixed.

However...


I finished it. And it did not work.

I had no errors at all in the directions. But nothing changed.

I don't suppose anyone could help me with this?

---

