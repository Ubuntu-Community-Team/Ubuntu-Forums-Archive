---
title: "How do I OPEN 7 zip?"
date: 2010-09-02
forum: General Help
---

### Post by Basheequa on 2010-09-02
I have ubuntu 10.04 and I have installed 7 zip onto it. But I don't know how to access it.

Can I use it to open ,rar files? I come from useing windows but I already love linux so much more

I look in accessories but it's not there or anywhere I look and I have a .rar file of pictures I need to open. 

Can someone help? And if there is a complicated way of doing it can I put an icon on there bar for easy access?

P.S. even when I right click on the file and click "open with..." it doesn't show up in the list

---

### Post by Tracy177 on 2010-09-02
> **Basheequa said:**
> I have ubuntu 10.04 and I have installed 7 zip onto it. But I don't know how to access it.

Can I use it to open ,rar files? I come from useing windows but I already love linux so much more

I look in accessories but it's not there or anywhere I look and I have a .rar file of pictures I need to open. 

Can someone help? And if there is a complicated way of doing it can I put an icon on there bar for easy access?

P.S. even when I right click on the file and click "open with..." it doesn't show up in the list

i always use right click on the file then there will be list scroll to extract and extract like in windows think it does work with zip and tar gz etc

---

### Post by Dayofswords on 2010-09-02
7zip dont have a gui in linux, but adds to fileroller(the archive manager and exracter) and adds 7z support to that

if you want to add the non-free rar part to it, click here
[apt: p7zip-rar]("apt:p7zip-rar")
and here to make sure you have the whole 7zip
[apt: p7zip-full]("apt:7zip-full")

p7zip-rar will let you open rar, but like 7zip, you cant make them, but you can click here([apt:rar]("apt:rar"))

full code in terminal is 
```
sudo apt-get install p7zip-rar 7zip-full rar 
```

---

