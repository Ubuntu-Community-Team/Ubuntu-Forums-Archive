---
title: "Ubuntu Version?"
date: 2011-03-27
forum: General Help
---

### Post by galacticaboy on 2011-03-27
How do I figure out what version of Ubuntu I am running, I know I have Ubuntu 10.10, but I want to know if I have Ubuntu 10.10.2 if there is such a version. How do I figure that out?
David

---

### Post by goldaryn on 2011-03-27
To find out which version you are running:

```
lsb_release -a
```

and which kernel:

```
uname -a
```

---

### Post by idoitprone on 2011-03-27
[https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

```
lsb_release -a
```

to check kernel, 32 or 64 bit

```
uname -a
```

Edit: lol I was 1 second too slow and i got the same answer as that guy lol

---

### Post by galacticaboy on 2011-03-27
That worked but I know there is another .X after the 10.10 such as 10.04.2... does Ubuntu 10.10 have that as well? I am just curious.

---

### Post by goldaryn on 2011-03-27
or if you fancy a change try this

```
cat /etc/issue
```

---

### Post by coffeecat on 2011-03-27
> **galacticaboy said:**
>  I know I have Ubuntu 10.10, but I want to know if I have Ubuntu 10.10.2 if there is such a version.

There never will  be a 10.10.2. The point releases only apply to LTS versions. The most recent LTS, Lucid, is currently at 10.04.2. A 10.04.3 live CD (and alternate CD, I guess) will be made available in July (I believe) and current 10.04 installations will be 10.04.3 if fully updated then. 10.10 will always be just 10.10.

---

### Post by kolmad on 2011-03-27
> **coffeecat said:**
> There never will  be a 10.10.2. The point releases only apply to LTS versions. The most recent LTS, Lucid, is currently at 10.04.2. A 10.04.3 live CD (and alternate CD, I guess) will be made available in July (I believe) and current 10.04 installations will be 10.04.3 if fully updated then. 10.10 will always be just 10.10.
he is correct

---

### Post by galacticaboy on 2011-03-27
> **coffeecat said:**
> There never will  be a 10.10.2. The point releases only apply to LTS versions. The most recent LTS, Lucid, is currently at 10.04.2. A 10.04.3 live CD (and alternate CD, I guess) will be made available in July (I believe) and current 10.04 installations will be 10.04.3 if fully updated then. 10.10 will always be just 10.10.

Ahh okay I get it now. Thanks for satisfying my curiosity!
David

---

