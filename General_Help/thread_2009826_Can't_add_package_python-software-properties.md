---
title: "Can't add package python-software-properties"
date: 2012-06-25
forum: General Help
---

### Post by LifeWithoutWindows on 2012-06-25
When I enter
```
sudo apt-get install python-software-properties
```
Into my Ubuntu Server 12.04 (Physical Computer, not a VM), it reports:
```
Package python-software-properties is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted or is only available form another source

E: Package 'python-software-properties' has no installation candidate
```

What do I do? I've checked the Machine's Internet Connection. It works fine.

---

### Post by LifeWithoutWindows on 2012-06-25
[UPDATE]
It might be that my apt is not properly configured, as I tried to install unzip [sudo apt-get install unzip]. How would I fix my apt?

---

### Post by drmrgd on 2012-06-25
What happens when you run:

```
sudo apt-get update
```

Does it query the repositories you have set without problem, or do you get an error?  Please post the output here.

---

### Post by LifeWithoutWindows on 2012-06-25
> **drmrgd said:**
> What happens when you run:

```
sudo apt-get update
```

Does it query the repositories you have set without problem, or do you get an error?  Please post the output here.

It can't connect to the websites (us.archive.ubuntu.com or security.ubuntu.com)

The wget works fine however :-?

---

### Post by LifeWithoutWindows on 2012-06-26
I'm going to go for a reinstall and see if that fixes it.

---

