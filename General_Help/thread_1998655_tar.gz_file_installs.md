---
title: "tar.gz file installs"
date: 2012-06-07
forum: General Help
---

### Post by ThunderMoon99 on 2012-06-07
Hi im trying to install a tar.gz file on my 12.04LTS system. I go to extract it but all that happens is it opens up as a folder :( I have no idea what to do from here

---

### Post by nothingspecial on 2012-06-07
Is there a README file in the folder?

Are you sure this isn't available in the software centre or from a PPA?

---

### Post by snowpine on 2012-06-07
What is the application? From where did you download it? Is there a README or INSTALL file? Is the app not available in the Software Center?

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by bbarcesaj125 on 2012-06-07
Generally speaking, there is no standard way to install a tar.gz but i'll you give some advices:
- If you're new to Linux, i suggest you avoid compiling from source. You need to look if this software is available in the software center or if there is a ppa. 
- Basically, compiling from source is reserved for advanced users and should be treated as a last resort. However, the general way to install such a package is by using these commands:

```
cd YOURFOLDER
./configure
make
sudo make install
```

Note: This method doesn't work in all cases and you need to satisfy the program dependencies before compiling otherwise you'll get an error.

---

