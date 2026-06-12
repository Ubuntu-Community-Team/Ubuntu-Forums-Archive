---
title: "Kernel Build error"
date: 2009-08-21
forum: General Help
---

### Post by tonysonney on 2009-08-21
I am trying to Build my first Kernel module file from the book "Linux Device Driver". But I can compile it. Can anybody help please.?

The code I use is

[I]#include<linux/init.h>
#include<linux/module.h>
#include<linux/kernel.h>
MODULE_LICENSE("GPL");

static int hello_init(void)
{
	printf(KERN_ALERT "Hello World\n");
	return 0;
}

static void hello_exit()
{
	printf(KERN_ALERT, "Goodbye, cruel world\n");
}

module_init(hello_init);
module_exit(hello_exit);[/I]



       The make file I use is 


[I]
obj-m += test.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean[/I]

I get a huge error set(So made an attachment) test.txt


Thanks,
Tony

---

