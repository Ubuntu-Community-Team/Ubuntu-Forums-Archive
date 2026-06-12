---
title: "copying files across network"
date: 2010-04-06
forum: General Help
---

### Post by LuniTux on 2010-04-06
Hello,

I am trying to copy files across a network using terminal. i know this is possible but i can't find a way. i tried scp but got:

```
scp "Desktop/helloworld.py" smb://xxx.xxx.xxx.xxx/myfolder
ssh: Could not resolve hostname smb: Name or service not known
lost connection

```

but i can paste smb://xxx.xxx.xxx.xxx/myfolder in the address bar in a folder and navigate to the correct area.

is there some other way i can do this?

---

### Post by nothingspecial on 2010-04-06
Install openssh-server and openssh-client on both machines then try scp again.

---

### Post by LuniTux on 2010-04-06
i am copying files from linux to windows is there another way to do that without ssh? any method would work. i could not get mount to work either

---

### Post by chaanakya_chiraag on 2010-04-06
You could try ```
smbmount
``` and ```
cp
```

---

### Post by Alabamaschalk on 2010-04-06
Hi There!
I used the following instructions:
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
for making this work

---

### Post by nothingspecial on 2010-04-06
> **LuniTux said:**
> i am copying files from linux to windows is there another way to do that without ssh? any method would work. i could not get mount to work either

Sorry, my windows know-how = 0

---

### Post by LuniTux on 2010-04-06
how would i "cp" to a network folder?

---

### Post by LuniTux on 2010-04-06
smbmount worked perfectly.

Thank you

---

### Post by chaanakya_chiraag on 2010-04-08
No problem!! :)

---

