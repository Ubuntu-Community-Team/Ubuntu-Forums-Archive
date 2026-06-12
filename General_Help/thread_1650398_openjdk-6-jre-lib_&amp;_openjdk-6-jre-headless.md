---
title: "openjdk-6-jre-lib &amp; openjdk-6-jre-headless"
date: 2010-12-21
forum: General Help
---

### Post by Gav1991 on 2010-12-21
I want to install openjdk-6-jre-lib and it says dependency on openjdk-6-jre-headless.
and when I want to install openjdk-6-jre-headless it says dependency on openjdk-6-jre-lib.
How can I ryn them together?
I'm using Maverick and both files are .deb

---

### Post by sikander3786 on 2010-12-21
From Applications > Accessories > Terminal, post the output of these commands.

```
sudo apt-get update && sudo apt-get install openjdk-6-jre
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

While posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read.

---

### Post by Gav1991 on 2010-12-21
My system can't use internet!!!!!!!!!!!!!

I want to install openjdk-6-jre with .deb files.

I have          openjdk-6-jre-lib.deb      &    openjdk-6-jre-headless.deb      and want to install them.

---

### Post by sikander3786 on 2010-12-21
> My system can't use internet!!!!!!!!!!!!!

You didn't mention that in your first post.

There is a dpkg command from the Terminal that lets you install all the packages in the directory thus solving the dependency issues. I am unable to locate it at the moment. Please wait for some one else to jump in.

Or, try installing openjdk-6-jre-lib first. Then openjdk-6-jre-headless and then openjdk-6-jre-lib in the reverse order as the dependencies appear ;-)

---

### Post by Gav1991 on 2010-12-21
How Can I install all .deb files in a directory?

---

### Post by matt_symes on 2010-12-21
Hi

You could try dpkg with the --ignore-depends flag on one of the packages.

```
man dpkg
```

Kind regards

---

### Post by Gav1991 on 2010-12-21
what do you mean to flag it? Is it like this:
```
sudo dpkg --ignore-depends -i <package name>.deb
```

---

### Post by matt_symes on 2010-12-21
Hi

> **Gav1991 said:**
> what do you mean to flag it? Is it like this:
```
sudo dpkg --ignore-depends -i <package name>.deb
```

I think its more along the lines of

```
sudo dpkg -i --ignore-depends=<package name>.deb <package name>.deb
``` 

I am not 100% sure of this (as its an option i don't use). Maybe someone here will know for certain.

From the manual

> --ignore-depends=package,... Ignore  dependency-checking for specified packages (actually, checking is performed, but only warnings about conflicts are given, nothing else).

Kind regards

---

