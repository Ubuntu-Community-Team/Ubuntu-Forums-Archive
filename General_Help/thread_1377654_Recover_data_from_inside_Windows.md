---
title: "Recover data from inside Windows"
date: 2010-01-10
forum: General Help
---

### Post by CEW11 on 2010-01-10
When I installed Ubuntu, it created a folder called 'ubuntu' on my hard drive. Is there a way to recover my data from this folder and use it with a newer version of ubuntu. I can't access Ubuntu on my computer. It boots straight into Windows.

---

### Post by Ugluk on 2010-01-10
Are you using Wubi install on Windows Vista?

---

### Post by CEW11 on 2010-01-10
> **Ugluk said:**
> Are you using Wubi install on Windows Vista?

I had windows vista, now using windows 7.
I think it is wubi

---

### Post by SecretCode on 2010-01-10
Did you originally have a boot up menu with Windows at the top and Ubuntu at the bottom? (Or something like that)

Windows 7 may have replaced your boot.ini list, but it looks like you did an upgrade of windows and the ubuntu installation is still there. It should be possible to fix the boot process so you can boot this installation again.

Haven't done this, but ... is there a file boot.ini in C:\ ? I'm not sure if windows 7 still uses it.

Also, can you post the contents of the ubuntu folder? 
```
dir C:\ubuntu
```
if that's where it is

---

### Post by CEW11 on 2010-01-11
Cant seem to find boot.ini

And in ubuntu is the following:
disks
docs 
install
winboot
curl_log.txt
metadl__log.txt

---

### Post by SecretCode on 2010-01-11
It looks like boot.ini is no longer used. See if you have a tool called "bcdedit" on your windows installation, or look on the net for something called "easybcd". Either should allow you to edit the list of operating systems shown at startup and add ubuntu. I'm not familiar with them, however.

---

### Post by mocoloco on 2010-01-11
I'll be doing a wubi install on a Win7 machine tomorrow or the next day.  I'll see about getting the boot info for you.

---

