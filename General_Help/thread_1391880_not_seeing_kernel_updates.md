---
title: "not seeing kernel updates"
date: 2010-01-27
forum: General Help
---

### Post by bowens44 on 2010-01-27
Right now I am not seeing kernel updates in synaptic. I am using ubuntu 9.10.

I have proposed updates and updates enabled. When I search 'ALL' I see kernels 2.6.31-17 and 2.6.31-18 (I am currently using 2.6.31-16).

I think that I may have broken something. I had updated to 2.6.31-17 . I had a problem with this kernel. I don't remember what the problem was but I un-installed 2.6.31-17 and went back to 2.6.31-16.


Since then I haven't seen kernel updates. I am sure that I must have removed or broken something that triggers these new kernels as being list as updates. 

Any suggestions as to how to get things back to normal?

Thanks

---

### Post by zvacet on 2010-01-28
All packages installed by synaptic,apt-get or aptitude are in /var/cache/apt/archives.Since you downloaded new kernel( doesn't matter if you don't use it) it will not show in updates any more.It is already in your system.for example if you want to install 2.6.31-17 again there will be no download.It will be installed from your /var/cache/apt/archives.

---

### Post by bowens44 on 2010-01-28
I thought of that too but it isn't in /var/cache/apt/archives. None of m previous kernel updates are. I would think that there would be a list of installed packages somewhere .

---

### Post by zvacet on 2010-01-29
You can find installed and uninstalled packages in synaptic>file tab>history.If you want to list installed packages then 

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
```

In your home directory you will find file named my-packages with list of all installed packages.

---

