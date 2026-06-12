---
title: "Installing 2.6.35-22.33 on Lucid"
date: 2010-10-10
forum: General Help
---

### Post by xjesse on 2010-10-10
Hi, I tried out Meerkat this morning and I was impressed. It seems this new kernel fixes all of my Intel Graphic problems I've been having. However, I'd like to stick with 10.04 being that it's LTS. I'd like to upgrade Lucid's current kernel version to the one which ships with Meerkat. 

Easiest possible way to do this?

Thanks. :)

---

### Post by andrewthomas on 2010-10-10
go to [http://packages.ubuntu.com/maverick/linux-image](http://packages.ubuntu.com/maverick/linux-image)
 
 
go to the bottom of the page at
 
 Packages providing linux-image and pick the package for your arch.
 
 
Download it and then
 
```
 
sudo dpkg -i /path/to/file

```

---

### Post by xjesse on 2010-10-10
> **andrewthomas said:**
> go to [http://packages.ubuntu.com/maverick/linux-image](http://packages.ubuntu.com/maverick/linux-image)
 
 
go to the bottom of the page at
 
 Packages providing linux-image and pick the package for your arch.
 
 
Download it and then
 
```
 
sudo dpkg -i /path/to/file

```

That did it. Thank you! :P

---

### Post by andrewthomas on 2010-10-10
You're welcome.

---

