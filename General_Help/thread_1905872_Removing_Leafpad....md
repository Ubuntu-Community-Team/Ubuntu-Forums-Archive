---
title: "Removing Leafpad..."
date: 2012-01-07
forum: General Help
---

### Post by dRounse on 2012-01-07
I just installed Lubuntu on a family members laptop, I love Lubuntu but I dont love leafpad or xpad and a few other programs and usually I can delete them but for some reason I cant delete them without removing lubuntu-desktop. Is there anyway to remove them without removing lubuntu-desktop? If not its fine.

---

### Post by MoreOrLess on 2012-01-07
lubuntu-desktop is a metapackage (an "empty" package that depends on other packages) incorporating all of the packages that Ubuntu deems necessary for a complete lxde desktop environment. Since leafpad is one of those packages, removing it automatically removes lubuntu-desktop. This is expected behavior and nothing to worry about. Go ahead and remove it.

---

### Post by bluexrider on 2012-01-07
according to [this]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=11595165") 




**lubuntu-desktop**: The LXDE desktop environment, and all the software distributed with Lubuntu

if the **lubuntu-desktop** is removed will it break the system?

---

### Post by MoreOrLess on 2012-01-07
No, it won't remove any software except leafpad. I guess it could also affect upgrading. If lubuntu-desktop depends on new packages in the upgraded version of Ubuntu, they won't be automatically installed. IIRC, upgrading usually reinstalls the desktop package though.

---

### Post by wildmanne39 on 2012-01-07
Hi, if it says it will remove the desktop that will leave you with only a command line to work from plus you need leafpad for editing files when necessary.
Thanks

---

### Post by bluexrider on 2012-01-07
> **wildmanne39 said:**
> Hi, if it says it will remove the desktop that will leave you with only a command line to work from plus you need leafpad for editing files when necessary.
Thanks
+1 that is what I thought

---

### Post by dRounse on 2012-01-08
> **wildmanne39 said:**
> Hi, if it says it will remove the desktop that will leave you with only a command line to work from plus you need leafpad for editing files when necessary.
Thanks

I prefer gedit...

---

### Post by whatthefunk on 2012-01-08
> **wildmanne39 said:**
> Hi, if it says it will remove the desktop that will leave you with only a command line to work from plus you need leafpad for editing files when necessary.
Thanks

No.  As said above, lubuntu-desktop is a metapackage.  Proceed with the removal...it will only remove the program you wish to remove.  Ive done this a thousand times and not once has my desktop actually disappeared.

Also, you can edit files with a command line text editor like nano.

---

### Post by Dennis N on 2012-01-08
Leafpad is such a tiny package, why not just ignore it and use what you prefer?

---

### Post by Elfy on 2012-01-08
> **dRounse said:**
> I prefer gedit...If you are going to install gedit you might better to install it from a termina with --no-install-recommends unless you want the recommended packages as well. 

```
sudo apt-get install gedit --no-install-recommends
```

> **whatthefunk said:**
> No.  As said above, lubuntu-desktop is a metapackage.  Proceed with the removal...it will only remove the program you wish to remove.  Ive done this a thousand times and not once has my desktop actually disappeared.+1

---

