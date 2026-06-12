---
title: "How to use a different bashrc without create a new account"
date: 2011-12-13
forum: General Help
---

### Post by lakeat on 2011-12-13
Hi, 

I am using the high performance computers in my university, and currently I have two versions of the same code, and after compilation, I want to use/test both of them in the same time, they are all required to set the environment variables in ~/.bashrc file, my question is this:

How can I simultaneously use two different settings without create another account?

You know I can't get another user account. I hope there are some free and good softwares like what we have in SGE management "module load software/version-1.0.x", something like that.



Many thanks!

---

### Post by TeoBigusGeekus on 2011-12-13
Can't you just rename the original bashrc
```
cp ~/.bashrc ~/.bashrc_backup
```
and then create a new one?

---

