---
title: "Permission on /usr/local"
date: 2012-02-19
forum: General Help
---

### Post by Butterfly-Love on 2012-02-19
Hi everyone, 

I am new to ubuntu.

I needed to install an SML compiler, which requires me to run a extract a tar file and run some scripts.

But it keeps telling me that i don't have the permission to create certain folders...

I installed ubuntu on my own computer. And i used that sudo <command> thing. yet it still happens. Why is it happening? I thought i am the boss. But apparently my computer doesn't think so.

---

### Post by wildmanne39 on 2012-02-19
Hi, try this please:
```
gksu nautilus
```
then try to create the folders.
Thanks

---

### Post by lexyn on 2012-02-19
Where do you need to create a folder ? 
If you want to copy a folder to /usr/local you can use this in terminal:
cd to your folder location then:
sudo cp -r yourfolder /usr/local/yourfolder (it will be created automatically)
After that you cand run scripts from that location using sudo ofc.

---

