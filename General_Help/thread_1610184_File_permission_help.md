---
title: "File permission help"
date: 2010-10-31
forum: General Help
---

### Post by DiscBrake on 2010-10-31
Greeting,

I got an .iso file with the Permission set to Read and Write. However, after extraction of that .iso file, the entire disc's Permission (under Properties right click) could not be determined. It's a Window's file (.exe) and I have Wine installed. But the executible file ("autorun.exe" or "setup.exe") is blocked and its permission could not be determined. 

I know I have to change the permission, but can someone show me how? I am relatively new at this, really appreciated it!

---

### Post by 73ckn797 on 2010-10-31
> **DiscBrake said:**
> Greeting,

I got an .iso file with the Permission set to Read and Write. However, after extraction of that .iso file, the entire disc's Permission (under Properties right click) could not be determined. It's a Window's file (.exe) and I have Wine installed. But the executible file ("autorun.exe" or "setup.exe") is blocked and its permission could not be determined. 

I know I have to change the permission, but can someone show me how? I am relatively new at this, really appreciated it!
Try opening a terminal and entering ```
sudo nautilus
``` Then  browse to the folder where the file is and right click over it and  select properties. There you can set permissions. See if this will work.

---

### Post by TeoBigusGeekus on 2010-10-31
> **73ckn797 said:**
> ```
sudo nautilus
``` 
...or better 
```
gksu nautilus
```

To op:
```
sudo chown yourusername /pathtofile/file.exe
```
to be its owner.

---

### Post by 73ckn797 on 2010-10-31
```
gksu nautilus
```
```
sudo nautilus
```
Either way accomplishes the same thing except one has a graphical window for your password.

---

### Post by TeoBigusGeekus on 2010-10-31
> **73ckn797 said:**
> ```
gksu nautilus
```
```
sudo nautilus
```
Either way accomplishes the same thing except one has a graphical window for your password.

[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by 73ckn797 on 2010-10-31
> **TeoBigusGeekus said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
I have not seen that info but have never had any issues that it speaks of. It probably would be good advice to a new user.

---

