---
title: "apt-get update or apt-get --fix-missing?"
date: 2009-08-15
forum: General Help
---

### Post by isee on 2009-08-15
I was downloading Edubuntu with &quot;sudo apt-get install edubuntu-desktop&quot; and got this at the end:

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kalzium-data_4.2.2-0ubuntu1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/kalzium-data_4.2.2-0ubuntu1_all.deb) Connection failed [IP: 91.189.88.40 80]
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

Could I have some instruction on how to run the right command please?

---

### Post by zvacet on 2009-08-15
Just in case run

```
sudo apt-get update
```

and in **synaptic>edit tab>mark packages by task>edubuntu-desktop**

---

### Post by isee on 2009-08-19
```
sudo apt-get update
```

Is this the same as running update manager?  Not that I'm opposed to code, I learn more with every question about code.  Ctrl-T brings up the terminal on my computer now.

Thanks!

---

