---
title: "Network shareing"
date: 2011-04-08
forum: General Help
---

### Post by bubbajtj on 2011-04-08
OK, I have 2 problems.

1. I have installed the sharing program onto my ubntu 10.10 machine and it says this "Failed to execute child process "testparm" (No such file or directory)".

2. How do I get numlock to run autimaticly when my pc boots?

any solutions?

---

### Post by clayman1000x on 2011-04-08
> **bubbajtj said:**
> OK, I have 2 problems.

1. I have installed the sharing program onto my ubntu 10.10 machine and it says this "Failed to execute child process "testparm" (No such file or directory)".

2. How do I get numlock to run autimaticly when my pc boots?

any solutions?

I could use some help with # 2, my BIOS is set for numlock on boot, windows does it fine but Ubuntu 10.04 does not. By the way, how do I find out what version of Ubuntu I am running?

---

### Post by garvinrick4 on 2011-04-08
> By the way, how do I find out what version of Ubuntu I am running? 	
```
lsb_release -a
```

---

### Post by garvinrick4 on 2011-04-08
> 1. I have installed the sharing program onto my ubntu 10.10 machineWhat sharing program?

---

### Post by bubbajtj on 2011-04-09
> **garvinrick4 said:**
> What sharing program?

The one that is standard with ubuntu? the one it install automaticly when you share the folder.

---

### Post by bab1 on 2011-04-10
> **bubbajtj said:**
> OK, I have 2 problems.

1. I have installed the sharing program onto my ubntu 10.10 machine and it says this "Failed to execute child process "testparm" (No such file or directory)".

2. How do I get numlock to run autimaticly when my pc boots?

any solutions?

For #2 you need to install the package *numlockx* and then add the following to the bottom of your **[FONT="Courier New"]/etc/gdm/Init/Default[/FONT]** file: ```
if [ -x /usr/bin/numlockx ]; then
	/usr/bin/numlockx on
fi

```

---

