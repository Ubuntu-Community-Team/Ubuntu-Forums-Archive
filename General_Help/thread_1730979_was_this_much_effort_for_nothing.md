---
title: "was this much effort for nothing??"
date: 2011-04-16
forum: General Help
---

### Post by vivek.pandey on 2011-04-16
hey everyone
   i wrote the following code
```

#include <linux/module.h>	/* Needed by all modules */
#include <linux/kernel.h>	/* Needed for KERN_INFO */

int init_module(void)
{
	printk(KERN_INFO "Hello world 1.\n");

	/* 
	 * A non 0 return means init_module failed; module can't be loaded. 
	 */
	return 0;
}

void cleanup_module(void)
{
	printk(KERN_INFO "Goodbye world 1.\n");
}

```
i then made the makefile
```

obj-m += hello1.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```
then ran each command one by one
```

make
modinfo hello1.ko
insmod ./hello1.ko

```
i can see my file in the kernel.... but what next.. i mean thought i would see a hello world sometime when i start my laptop or atleast some effect of my code but nothing happens so whatever i did went in vain or i am not noticing something?
please answer

---

### Post by vivek.pandey on 2011-04-17
bump?

---

