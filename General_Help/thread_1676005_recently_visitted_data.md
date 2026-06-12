---
title: "recently visitted data"
date: 2011-01-26
forum: General Help
---

### Post by harkumar on 2011-01-26
hi...
I am using ubuntu 10.10 netbook edition. 
I do not want to store the recently visited files/documents/images that can be seen directly from the "Files and Folder" icon. Where and how to change the settings....please help!!

---

### Post by harkumar on 2011-01-31
still waiting for some help....

---

### Post by howefield on 2011-01-31
To disable the list of recent documents open a terminal and type the following command... 

```
rm ~/.recently-used.xbel
```

followed by 

```
touch ~/.recently-used.xbel
```

and finally..
 
```
sudo chattr +i ~/.recently-used.xbel
```

To re-enable logging of recently used documents, use this...
 
```
sudo chattr -i ~/.recently-used.xbel
```

---

### Post by harkumar on 2011-01-31
thank you for your help.

---

