---
title: "gvfs-mount is no good in script? (when ran as root)"
date: 2011-06-08
forum: General Help
---

### Post by Bladtman242 on 2011-06-08
I've got a script at startup that depends on a certain volume being mounted,
so I thought id just add something like 
```

if [ "`mount | grep 'sda3' = "" ]
then
      gvfs-mount -d /dev/sda3
fi

```This has worked for me in other scripts, but apparently cant run as root.
So I changed line 3 to ```
su -c 'gvfs-mount -d /dev/sda3' bladt
```And this is where I get lost:
That command will work perfectly from a root terminal, but it will not work from the script
when I run it as root?

I should probably say that I'm on 10.04 64-bit

---

### Post by Bladtman242 on 2011-06-09
Anybody? :)
Any method to solve this problem,
or perhaps a way around it? :)

---

