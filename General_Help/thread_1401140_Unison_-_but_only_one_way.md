---
title: "Unison - but only one way"
date: 2010-02-07
forum: General Help
---

### Post by GabrielWolff on 2010-02-07
I want to merge a few /home directories of different laptops I have.

For this purpose I copied one of them to an external hard drive, then looking for changes with Unison. I assumed I'd find an option to add files *only to the external HDD*, without changing the other one.

But nope, I didn't...

Does anyone know how to do that using Unison or anything else?

So what I need is a program that will find any file that does not exist in one tree, adding it from the other, but not doing the same the other way around...

---

### Post by alienprdkt on 2010-05-10
Did you ever get this resolved?

Could create an smb share of your home directory and mount it to each server to a location like: /mounts/home
then you could bind that directory to your current home directory

mount --bind /mounts/home/ /home

this solution should work

---

