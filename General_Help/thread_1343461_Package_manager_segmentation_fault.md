---
title: "Package manager segmentation fault?"
date: 2009-12-01
forum: General Help
---

### Post by william_hunter on 2009-12-01
Hi all. I'm having a problem with installing a new package. I get an error message in terminal:

```

william@ubuntu-desktop:~$ sudo apt-get install libstdc++5
Segmentation fault
william@ubuntu-desktop:~$ 




```

How do I repair my package manager short of re-installing the OS? I can't seem to find anything on this anywhere..thanks.

---

### Post by whoop on 2009-12-01
> **william_hunter said:**
> Hi all. I'm having a problem with installing a new package. I get an error message in terminal:

```

william@ubuntu-desktop:~$ sudo apt-get install libstdc++5
Segmentation fault
william@ubuntu-desktop:~$ 




```

How do I repair my package manager short of re-installing the OS? I can't seem to find anything on this anywhere..thanks.

That package is not in the (standard) repos is it?

---

### Post by jmszr on 2009-12-01
william_hunter,

This fixed a similar situation for me:

```
sudo rm /var/cache/apt/*.bin
```

Hope that helps.

---

### Post by william_hunter on 2009-12-01
> **whoop said:**
> That package is not in the (standard) repos is it?

Not sure, I cant even run Synaptic, it just does not seem to even open up. 

Trying solution above.

---

### Post by william_hunter on 2009-12-01
Output (such as it is) from the suggestion above:

```

william@ubuntu-desktop:~$ sudo rm /var/cache/apt/*.bin
william@ubuntu-desktop:~$ 


```

Something is all sorts of borked, isn't it? When I try to run Synaptic from the menu, nothing happens. No error message that I can see, nothing.

---

### Post by william_hunter on 2009-12-02
> **whoop said:**
> That package is not in the (standard) repos is it?

No, its an older package. I think I managed to fix the issue I was having with Synaptic by upgrading to the newest desktop version, but I still need this package apparently, because the error still comes up even though I have the current GCC package installed. How do I go about getting the older packages?

---

### Post by william_hunter on 2009-12-15
A reinstall fixed the problem for me..nothing else i found seemed to work.

---

