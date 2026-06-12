---
title: "32bit Java does not work, installed from repos"
date: 2009-09-28
forum: General Help
---

### Post by beastrace91 on 2009-09-28
So I have the latest version of Sun's Java JRE installed on my netbook which is running 32bit Ubuntu. It is installed via synaptic, how ever neither of my browsers (firefox 3.0 and the latest Google Chrome release) can see/use Java. When I go to a website that uses it I am greeted by a message that tells me I need to install Java.

I have already tried reinstalling via synaptic and it did not help in the slightest. Suggestions on other things I can try to get this working? I need it for school to use WebCT :/

Thanks,
~Jeff

---

### Post by credobyte on 2009-09-28
```
sudo apt-get install sun-java6-plugin

```

---

### Post by beastrace91 on 2009-09-28
That was it. They should really add that package to the ubuntu-restricted-extras, it is what I had used the first time to install Java.

Ahh well, alls well that ends well.

Thanks,
~Jeff

---

### Post by credobyte on 2009-09-28
ubuntu-restricted-extras in Jaunty contain only 64bit JRE .. how did you managed to get it on 32bit proc ? :-k

---

### Post by beastrace91 on 2009-09-28
No idea xD I just installed it and it was there... Perhaps it came from my medibuntu repos then? I loose track of which extra ones I have installed.

~Jeff

---

