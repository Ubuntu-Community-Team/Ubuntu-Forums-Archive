---
title: "How to fix botched usermod"
date: 2011-09-23
forum: General Help
---

### Post by krumpy on 2011-09-23
I was trying to add myself to the group staff using 

```

sudo usermod -G staff matt

```I realized that this wasn't the right way to do it after the fact.  Now I'm only a member of staff and matt.  Also my group user ID is staff instead of matt.  What is the best way to re-add myself to all groups I was originally part of.  I ran an id matt before running user mod so I have a list of all my old groups.

This is what id returned prior
```

uid=1000(matt) gid=1000(matt) groups=1000(matt),4(adm),20(dialout),24(cdrom),46(plugdev),111(lpadmin),119(admin),122(sambashare)

```

After
```

uid=1000(matt) gid=50(staff) groups=50(staff)

```

Can I just re-add myself to /etc/group/ and etc/gshadow?  I don't have much experience here so just wanted to double check the best way to proceed before messing things up any worse.

---

### Post by papibe on 2011-09-23
If you haven't lost the ability to sudo, you can use the command addgroup to add you back to those groups.

If you did, you may need to boot using the live CD to fix it.

Regards.

---

### Post by sisco311 on 2011-09-24
Next time use:
```
gpasswd -a user group
```
or
```
usermod -a -G group1,group2... user
```
To add your user to supplementary group(s).  

You might have to boot into recovery mode to add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)


If you are using Ubuntu(GNOME), then the default groups an admin is member of are listed in /etc/gnome-system-tools/user-profiles.conf

Run something like:
```
grep '^Groups' /etc/gnome-system-tools/user-profiles.conf
```
to list the groups.

---

### Post by krumpy on 2011-09-24
Thanks.  I hadn't closed the terminal and I guess I still had admin permissions so I just re-added myself.

---

