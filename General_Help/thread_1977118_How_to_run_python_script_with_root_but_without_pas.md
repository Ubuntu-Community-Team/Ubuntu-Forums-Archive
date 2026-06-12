---
title: "How to run python script with root but without password"
date: 2012-05-09
forum: General Help
---

### Post by Jolladay on 2012-05-09
Hi there,

I'm fairly new to linux permissions. I have a Python script that does things such as run shell scripts, dd, ntfsclone, ntfsresize. Many of which require me to sudo and enter a password. The requirements are that the script should run on boot and not require a password of the user. 

I have added various things to sudoers:

```
username ALL=(ALL) ALL
username ALL=NOPASSWD: /path/to/my/script.py
username ALL=NOPASSWD: /usr/bin/python,/bin/dd,/bin/sh
```

none of these seem to work. When I run 
```
python myscript.py
```

it gets to the point in the script where it is running 

```
os.system("./shellscript.sh")
```

and asks for a password.

Thanks for any help!

-Jolladay

---

### Post by Jolladay on 2012-05-10
Does anyone know how to do this?

-Jolladay

---

### Post by boshkash1151 on 2012-06-01
try adding sudo at the beginning 
```
sudo python myscript.py
```

also make sure to add it after %admin as noted here
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

