---
title: "BASH Scripting"
date: 2011-03-21
forum: General Help
---

### Post by slagatho7 on 2011-03-21
Trying to write basic BASH script for mounting iso's with ease.
I want to know how to tell the script to prompt me for input for directories for the iso location and mount point.
Have tried using "read" command but to no avail.
    I tend to be pretty slow when it comes to this stuff and I am sure that the solution to this is *ridiculously *simple, but I would appreciate the help.

---

### Post by HermanAB on 2011-03-21
You mean something like this?

#! /bin/bash
echo Example: mntiso filename.iso
mkdir /mnt/iso
mount -o loop %1 /mnt/iso

---

### Post by m_duck on 2011-03-21
> **HermanAB said:**
> You mean something like this?

#! /bin/bash
echo Example: mntiso filename.iso
mkdir /mnt/iso
mount -o loop **$**1 /mnt/iso

Typo?

---

### Post by sisco311 on 2011-03-21
> **HermanAB said:**
> You mean something like this?

#! /bin/bash
echo Example: mntiso filename.iso
mkdir /mnt/iso
mount -o loop "$1" /mnt/iso

> **m_duck said:**
> Typo?

Typo? :)

---

### Post by m_duck on 2011-03-21
Sisco wins :p

---

### Post by btindie on 2011-03-21
It's easier to pass them as arguments to the script instead of prompting the user for them as you get tab completion so you don't need to type the complete filename. Here's a simple script that'll do what you want:
```
#!/bin/sh

if [ $# -ne 2 ]; then
  echo "Usage: ${0##*/} [iso file] [mount point]"
  exit 1
fi

[ -d $2 ] || mkdir $2

sudo mount -t iso9660 -o loop,ro $1 $2
```

---

