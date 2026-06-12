---
title: "unable to recovery or reset root pwd bootin by grub single user mode"
date: 2009-12-24
forum: General Help
---

### Post by ubuscout on 2009-12-24
Hi people,

I've just upgraded to 9.10 (ext4 fs), and I'm a bit surprised to be unable reset or change root pwd by bootin' as in object. 

I follow as usual this steps:
-at grub propt I select recovery mode and edit it modifing the end with rw single init=/bin/bash  and select b to perform the selected boot

-after I prompted root shell, id command give me of course root response.

-now giving the passwd command, as usual I expect inesrt new pwd prompt but system give me a more sad response "perimission denied" I think "funny I'm root :confused: "  ...feeling it could be a pam problem, it doesn't matter how in many different way I can modify pam conf ensuring with nullok_secure the pam_unix.so module etc... 

-strange it is, in another notebook with 9.10 (but ext3 !  ..could it be this the difference/problem ?!) I perform the steps above without problem (without changing any pam conf).

Any advice about this ?!

thx in advance

---

### Post by wojox on 2009-12-24
```

a. Boot your computer into Recovery Mode (second option in the Grub Menu), and select the terminal.

b. Type: 

passwd your_own_username (for example: passwd john)

press Enter.

Note: when you type your new password, it remains invisible. Not even asterisks, which is normal.

c. Type: 

reboot

press Enter.

```

---

### Post by ubuscout on 2009-12-24
> **wojox said:**
> ```

a. Boot your computer into Recovery Mode (second option in the Grub Menu), and select the terminal.

b. Type: 

passwd your_own_username (for example: passwd john)

press Enter.

Note: when you type your new password, it remains invisible. Not even asterisks, which is normal.

c. Type: 

reboot

press Enter.

```

thx wojox

I perform "a" step ...it give me Recovery menu, here I've not "terminal option" but : resume, clean, dpkg, grub, netroot, root  ...of course I think u are meanin about "root" option  so I follow that and I get root prompt (as said id command give me: uid=0 e gid=0)  but if I give passwd it repaly me with :
passwd: Permission denied
passwd: password unchanged

any idea ?!?

thx

---

### Post by wojox on 2009-12-24
So you typed:

```
passwd ubuscout
```

and it says permission denied?

---

### Post by ubuscout on 2009-12-24
> **wojox said:**
> So you typed:

```
passwd ubuscout
```

and it says permission denied?

..as root, usually I type simply "passwd" and I've got that replay... by the way the same answer is if I type "passwd root" or "passwd johnfoo"

thx

---

### Post by ubuscout on 2009-12-28
...a polite toc toc :-)

---

