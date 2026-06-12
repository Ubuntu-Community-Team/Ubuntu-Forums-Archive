---
title: "How to know the dependancies?"
date: 2009-07-28
forum: General Help
---

### Post by praveesh on 2009-07-28
If I get a .deb file, is there any way to know the dependancies of that file ? If I extract that file, can I see any file(a text file?) in it which says about the dependancies? Thank you

---

### Post by philinux on 2009-07-28
No need to extract. Just use this command.

dpkg -I nameofpackage.deb

I = info
i = install

---

### Post by DaithiF on 2009-07-28
Hi,
in a terminal, run 
dpkg-deb -I somepackage.deb

and look for the 'Depends' line in the output

---

### Post by praveesh on 2009-07-28
Thanks

---

### Post by x33a on 2009-07-28
gdebi lists the dependencies.

you can use it from the commandline too:
```
sudo gdebi filename.deb
```

---

### Post by praveesh on 2009-07-28
Thanks. Some more doubts. 
1.Sometimes a dependancy will have dependancies . Will this command show the dependancies of dependancies' (that is , will this command display all  the packages to be downloaded? . Iam trying to install apps in a computer without internet ).
2. Is there any commands to know the extra softwares to be installed? (Some of the dependancies might be already installed in the computer. So no need of downloading) 
. Thank you

---

