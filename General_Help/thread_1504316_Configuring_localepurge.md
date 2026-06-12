---
title: "Configuring localepurge"
date: 2010-06-07
forum: General Help
---

### Post by humorse_42 on 2010-06-07
Hey everyone, 
I was wondering how to configure localepurge in ubuntu 10.04. I didnt choose anything other than the default settings. A message came up that says i choose to not keep any locals, is this really what i want to do? I am asking because i dont want to do anything that will crash my computer or ruin it. I appreciate the advice. Thank you

---

### Post by dcstar on 2010-06-08
> **humorse_42 said:**
> Hey everyone, 
I was wondering how to configure localepurge in ubuntu 10.04. I didnt choose anything other than the default settings. A message came up that says i choose to not keep any locals, is this really what i want to do? I am asking because i dont want to do anything that will crash my computer or ruin it. I appreciate the advice. Thank you

```
sudo dpkg-reconfigure localepurge
```

Select the Locales you want to keep on your system, the rest will be removed when a package is updated or you manually run the command:

```
sudo localepurge
```

---

