---
title: "How to download Ubuntu source code?"
date: 2011-04-10
forum: General Help
---

### Post by pcbsdfhte on 2011-04-10
How to download Ubuntu Linux source code?

---

### Post by 3rdalbum on 2011-04-10
```
sudo apt-get source <packagename>
```

Goes into /usr/src, I believe.

---

### Post by jocko on 2011-04-10
> **3rdalbum said:**
> ```
sudo apt-get source <packagename>
```Goes into /usr/src, I believe.
Don't do it that way... You don't need sudo to download source code.

This is better:
```
apt-get source <packagename>
```
And it will put the source in the current directory, not /usr/src (which is why you don't need sudo)...

---

### Post by pcbsdfhte on 2011-04-10
> **jocko said:**
> Don't do it that way... You don't need sudo to download source code.

This is better:
```
apt-get source <packagename>
```
And it will put the source in the current directory, not /usr/src (which is why you don't need sudo)...

How to get Maverick Meerkat(Ubuntu 10.10) source code?
I typed 
apt-get source Maverick Meerkat
but it doesn't work.

---

### Post by neotifa on 2011-04-10
Linux Kernel:
```
http://www.kernel.org/

```
And about other packages, search their websites

---

### Post by marin123 on 2011-04-10
> **pcbsdfhte said:**
> How to get Maverick Meerkat(Ubuntu 10.10) source code?
I typed 
apt-get source Maverick Meerkat
but it doesn't work.

package isnt maverick meerkat, packages are ubuntu-desktop, empathy, compiz etc...

---

