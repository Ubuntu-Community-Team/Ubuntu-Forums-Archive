---
title: "Cannot find library"
date: 2009-12-25
forum: General Help
---

### Post by ardakshalkar on 2009-12-25
I have installed simspark.
And when I try to execute it shows following error
ardak@ardak-laptop:~/simspark/build$ simspark
simspark: error while loading shared libraries: libspark.so.0: cannot open shared object file: No such file or directory

But I have found following file in /usr/lib/simspark
What can I do

---

### Post by mc4man on 2009-12-25
run 
```
sudo ldconfig
```

---

### Post by ardakshalkar on 2009-12-25
> **mc4man said:**
> run 
```
sudo ldconfig
```

It does take no difference
:(

---

### Post by taurus on 2009-12-25
How did you install simspark?

```
ls -la /usr/lib/simspark
```

---

### Post by ardakshalkar on 2009-12-26
> **taurus said:**
> How did you install simspark?

```
ls -la /usr/lib/simspark
```

I installed with synaptic packager

---

### Post by taurus on 2009-12-26
Is that from a third party repo?

What happens if you run this command from a terminal?

```
ldd simspark
```

p.s.  Looks to me like you've built it from the display of your prompt!

---

### Post by ardakshalkar on 2009-12-26
> **taurus said:**
> Is that from a third party repo?

What happens if you run this command from a terminal?

```
ldd simspark
```

p.s.  Looks to me like you've built it from the display of your prompt!
It displays
ldd: ./simspark: not regular file
Yes I installed from third party repo

---

### Post by taurus on 2009-12-26
```
file simspark
```
Which repo did you add?

---

### Post by ardakshalkar on 2009-12-26
> **taurus said:**
> ```
file simspark
```
Which repo did you add?

I followed instructions from 
[http://robocup.allafiha.com/](http://robocup.allafiha.com/)

---

### Post by taurus on 2009-12-26
> **ardakshalkar said:**
> I followed instructions from 
[http://robocup.allafiha.com/](http://robocup.allafiha.com/)

That site has a typo, simsaprk!

[http://simspark.sourceforge.net/wiki/index.php/Installation_on_Linux#Ubuntu](http://simspark.sourceforge.net/wiki/index.php/Installation_on_Linux#Ubuntu)

---

### Post by ardakshalkar on 2009-12-26
I corrected it to simspark

---

