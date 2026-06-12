---
title: "I get strange error, package broken, but I don't know the name of the package."
date: 2009-11-26
forum: General Help
---

### Post by looop on 2009-11-26
First...
Hey everyone I'm new to Ubuntu.
and I use Ubuntu 9.10
Second - sorry for the long topic

Third:
I have a problem with a installation of Wine.
I get this error message
"Could not apply changes!
Fix broken packages first."
I don't get any name on the package, so how the #"@!= do I fix this error?
I read this thread:[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=947124&page=2 ]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=947124&page=2")
But when I don't know the name of the package how can I then fix it ?

---

### Post by Gonchos on 2009-11-26
You can check broken packages in System > Administration > Synaptic Package Manager

Add a filter, and look for any broken packages.

---

### Post by looop on 2009-11-26
> **Gonchos said:**
> You can check broken packages in System > Administration > Synaptic Package Manager

Add a filter, and look for any broken packages.

I'll try that and return with the result

---

### Post by looop on 2009-11-27
> **looop said:**
> I'll try that and return with the result
I can't find any broken package, what can I do to fix it then ?

---

### Post by Zorael on 2009-11-27
Hmm.
```
$ sudo dpkg --configure -a
$ sudo aptitude install -f
```

---

