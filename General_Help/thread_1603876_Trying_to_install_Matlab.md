---
title: "Trying to install Matlab"
date: 2010-10-23
forum: General Help
---

### Post by Kdar on 2010-10-23
I am trying to install Matlab on my computer.

When I type
```
sudo sh /home/armen/Downloads/Matlab.R2010b.UNIX/matu20Xb/install

```

I get this error, which stops installation right away:
```
eval: 1: /tmp/mathworks_29716/java/jre/glnxa64/jre/bin/java: Permission denied
```

What can I do? Is it some problem with Java?

---

### Post by psihokiller4 on 2010-10-23
don't know try:
```

sudo su

```password

and after that you're command without sudo

---

### Post by Kdar on 2010-10-23
still not. same error.

---

### Post by Kdar on 2010-10-23
Maybe it something to do with OpenJDK Java?

---

### Post by thameera on 2010-10-29
> **Kdar said:**
> Maybe it something to do with OpenJDK Java?

Yes, you'll have to install sun java for this. 10.10 doesn't have the repos so you'll have to add these sources and install sun java.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

---

### Post by behrouz.seyedi on 2011-04-21
this problem was solved in [http://ubuntuforums.org/showthread.php?t=1594188&page=2]("http://ubuntuforums.org/showpost.php?p=10654216&postcount=16")
:D

---

