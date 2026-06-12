---
title: "making calling 'gdm' equivalent to 'sudo gdm'"
date: 2011-07-12
forum: General Help
---

### Post by Bre Ntt on 2011-07-12
Hi, I'm booting from the bash command line, and I was wondering if there is a way to make it to where when 'gdm' is called it is always called as if it had root permissions. Just so I don't always have to type 'sudo gdm' and enter a password (which would require entering a password twice, since the gdm splash screen also asks for a password.)

---

### Post by WorMzy on 2011-07-12
You can make "sudo gdm" not ask for a password. Just run
```
sudo visudo
```
and add the following line:

```
%admin ALL=(ALL) NOPASSWD: /usr/sbin/gdm
```

EDIT: You might need to change "admin" to "sudo". Not sure on that though.

---

### Post by sisco311 on 2011-07-12
You don't have to use a display (or login) manager to start an X session. 

You can use xinit or startx.

---

### Post by ajgreeny on 2011-07-12
> **Bre Ntt said:**
> Hi, I'm booting from the bash command line, and I was wondering if there is a way to make it to where when 'gdm' is called it is always called as if it had root permissions. Just so I don't always have to type 'sudo gdm' and enter a password (which would require entering a password twice, since the gdm splash screen also asks for a password.)
I am not sure what youn mean by "booting from the bash command line".

If you are in bash, you must already have booted, so surely using ```
startx
``` command would get you to a GUI, wouldn't it?

Have I misunderstood the situation?

EDIT:  sisco311 was too quick!

---

### Post by WorMzy on 2011-07-12
Good point, Sisco.

Using startx (or xinit) will also have the benefit of you not having to enter your password again.

---

