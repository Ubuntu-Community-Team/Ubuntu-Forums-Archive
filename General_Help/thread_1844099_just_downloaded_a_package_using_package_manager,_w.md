---
title: "just downloaded a package using package manager, where is it?"
date: 2011-09-14
forum: General Help
---

### Post by dan0804smith on 2011-09-14
just downloaded firefox from the package manager.  where is it, using lubuntu natty

---

### Post by papibe on 2011-09-14
Synaptic Package Manager?

If so, you did more than download it, you installed it. Look for Firefox in the menus.

Does that help?
Regards.

---

### Post by haqking on 2011-09-14
> **dan0804smith said:**
> just downloaded firefox from the package manager.  where is it, using lubuntu natty

/var/cache/apt

however you probably installed it so

```
whereis appname
```finds all instances

```
which appname
```shows which version by default

---

### Post by dan0804smith on 2011-09-14
> **haqking said:**
> /var/cache/apt

however you probably installed it so

```
whereis appname
```finds all instances

```
which appname
```shows which version by default

  that worked it said it was in /usr/bin/firefox /etc/firefox /usr/share/man/man1/firefox.1.gz

i types that into the file bar, but it wasnt found

---

### Post by haqking on 2011-09-14
> **dan0804smith said:**
> that worked it said it was in /usr/bin/firefox /etc/firefox /usr/share/man/man1/firefox.1.gz

i types that into the file bar, but it wasnt found


firefox.gz is a compressed file and that one is in the man page directory

can you type just **firefox** from the terminal.

if its installed correctly it should launch

---

### Post by kerry_s on 2011-09-14
Should be in the menu under Internet.

---

