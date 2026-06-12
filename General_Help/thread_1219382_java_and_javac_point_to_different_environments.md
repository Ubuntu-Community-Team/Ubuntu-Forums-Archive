---
title: "java and javac point to different environments"
date: 2009-07-21
forum: General Help
---

### Post by RonNYC on 2009-07-21
HI. I'm confused.

While java on my system uses 1.6.0_0, javac uses Eclipse Java Compiler 0.894_R34x, 3.4.2. Now, in Eclipse, Eclipse itself uses 1.6, so what gives?

Any help is always greatly appreciated.

RON

---

### Post by Rob_H on 2009-07-21
So you're running javac from the command line and it's invoking the Eclipse compiler? What do you see when you type the following:

```
sudo update-alternatives --display javac
```

You will probably see it pointing to the Eclipse compiler, but hopefully the Sun compiler will be listed as an alternative. To switch it, use:

```
sudo update-alternatives --config javac
```

Then follow the prompt.

---

### Post by Rob_H on 2009-07-21
And if you don't see the Sun compiler listed, install the **sun-java6-jdk** package from the repos. Maybe you only installed the JRE.

---

### Post by RonNYC on 2009-07-21
Thank you, thank you. That worked!

---

