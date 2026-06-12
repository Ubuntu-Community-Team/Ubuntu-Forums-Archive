---
title: "/etc/init.d/hostname.sh MISSING!!!"
date: 2010-10-23
forum: General Help
---

### Post by adamjkok on 2010-10-23
I'm trying to change the hostname on my box. When I try to run the following command:

```
/etc/init.d/hostname.sh start
```

as root (I ran sudo -i to simulate a login as root instead of typing sudo for every command), I got the following error:

-bash: /etc/init.d/hostname.sh: No such file or directory

Since I've heard that this has to be done properly or sudo won't work, I'm not doing anything to that box without further guidance from someone who knows what they're doing.

**Ubuntu 10.10 Maverick Meerkat**

---

### Post by mhgsys on 2010-10-23
I assume you changed your hostname by editing /etc/hostname

you should ..
.. anyway.. after you changed your hostname type


```
sudo service hostname start
```

and test it 
```
hostname
```

---

### Post by Morbius1 on 2010-10-23
You need to edit two files to change the hostname or else sudo and the like go bizerk: [http://ubuntuforums.org/showpost.php?p=9730512&postcount=2](http://ubuntuforums.org/showpost.php?p=9730512&postcount=2)

Something like this will open both up simultaneously:
```
 gksu gedit /etc/hostname /etc/hosts
```

---

### Post by adamjkok on 2010-10-23
> **mhgsys said:**
> I assume you changed your hostname by editing /etc/hostname

you should ..
.. anyway.. after you changed your hostname type


```
sudo service hostname start
```and test it 
```
hostname
```

Thanks for your help! (SOLVED)

---

