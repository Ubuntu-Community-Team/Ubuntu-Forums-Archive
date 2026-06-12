---
title: "Cant Remove a Users Directory In Ubuntu Server 9.04"
date: 2009-12-25
forum: General Help
---

### Post by husskii on 2009-12-25
Hi I have just removed a user account off my server but I found that the directory folder is still in the home directory.
Ive tried the command 
```
rm /home/<user>
```
hoping it would delete his folder but with no success, also Google doesn't help much, I have done a more then 1 search, hoping that someone may of posted a how to but came up empty handed :(
has anyone got any idea on how I can accomplish this task....

Thanks 
Huss :)

---

### Post by taurus on 2009-12-25
You have to recursively remove all the subdirectories in there first.

```
rm -rf /home/<username>
```
Just be real careful with the -rf options.

---

### Post by dcstar on 2009-12-27
> **taurus said:**
> You have to recursively remove all the subdirectories in there first.

```
rm -rf /home/<username>
```
Just be real careful with the -rf options.
This might have a better chance of working:
```
sudo rm -rf /home/<username>
```

---

### Post by husskii on 2009-12-28
thank guys ill give it a try :)

---

### Post by husskii on 2010-01-06
worked like a charm, thank you :)

---

