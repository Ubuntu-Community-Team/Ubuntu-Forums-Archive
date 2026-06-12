---
title: "apt-cache show"
date: 2012-05-31
forum: General Help
---

### Post by orrymr on 2012-05-31
I'm a bit confused by the output of apt-cache show.
I've used Netbeans as an example, and the lines I'm not sure about are the following:

```

Installed-Size: 1918
Size: 897978

```
I'm guessing that size refers to the size of the package, and installed-size, well, the size after installation.
My first guess was that "Size" was listed in kb, so the package is roughly 897mb, but I'm not sure about "Installed-Size". Is this listed in mb?

I took cowsaw as another example:
```

Installed-Size: 280
Size: 19904

```
If I'm right about the units of measurement, then the installed cowsay is 280mb, while the package is roughly 19mb... This seems a bit large?

(As an aside - why aren't the units of measurement listed? What use is this otherwise?)

---

