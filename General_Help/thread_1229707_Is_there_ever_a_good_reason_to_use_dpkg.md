---
title: "Is there ever a good reason to use dpkg?"
date: 2009-08-02
forum: General Help
---

### Post by sincityharley on 2009-08-02
I am learning about Ubuntu today and reading through some source material. I am currently reading about dpkg and all its uses. My question is why would anyone use dpkg when Ubuntu has the Add/Remove programs and the built in package manager? Just curious. Thanks

---

### Post by LinuxRules1 on 2009-08-02
If some packages get corrupted or don't install correctly there is no way to fix that with a UI. usually you have to type in the code below to fix that.

```

sudo dpkg --configure -a

```

that is one reason why people use dpkg

---

### Post by pastalavista on 2009-08-02
Believe it or not, there are many, many more apps available to run in Ubuntu that aren't in the repositories. If you ever compile one of them, you will need dpkg to install it.

---

### Post by nikhilbhardwaj on 2009-08-02
> **pastalavista said:**
> If you ever compile one of them, you will need dpkg to install it.
if you compile you dont need dpkg
if you download a .deb then you do

---

### Post by cariboo on 2009-08-02
If you use checkinstall when compiling from source, it creates a .deb, you then will need to use dpkg to install it.

---

### Post by ron3090 on 2009-08-02
Or, if your computer has no access to the internet and you need to manually install .debs.

---

### Post by pastalavista on 2009-08-02
I thought, when you compile a package for Ubuntu (Debian), you would be creating a .deb package.. or else apt couldn't keep tabs on it for updates. Just like compiling for Red Hat would create a RPM package. Of course, I'm still new at this.

---

### Post by oldos2er on 2009-08-02
> **sincityharley said:**
> My question is why would anyone use dpkg when Ubuntu has the Add/Remove programs and the built in package manager? 

 Convenience, simplicity, speed.

---

### Post by SuperSonic4 on 2009-08-02
Isn't Synpatic a front-end to dpkg ;)

---

### Post by sincityharley on 2009-08-02
Is Synaptic front end for dpkg? Also is the Add/Remove a front end for apt-get?

---

### Post by CatKiller on 2009-08-02
Synaptic is a front-end for APT, which started as a front-end for dpkg.

As to why you'd use dpkg directly, there are some things for which dpkg is the best tool for the job; installing an already-downloaded group of files, re-configuring a single package, reading or writing the package state of a bunch of packages in one go, that kind of thing. Command-line jobs where you want flexibility more than anything else.

---

