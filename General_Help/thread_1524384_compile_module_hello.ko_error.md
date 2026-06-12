---
title: "compile module hello.ko error"
date: 2010-07-05
forum: General Help
---

### Post by zztczcx on 2010-07-05
hi all
**code:**
/*
 *   Hello world module.
 */

#include  <linux/init.h>
#include <linux/module.h>

MODULE_LICENSE("Dule  BSD/GPL");


static int hello_init(void)
{
    printk(KERN_ALERT "Hello, kernel!\n");
   return 0;
}

static  void hello_exit(void)
{
   printk(KERN_ALERT "Good-bye,  kernel!\n");
}   

module_init(hello_init);
module_exit(hello_exit);


**code:**
/* makefile  */
obj-m := hello.o


when I compile this modules ,it  appears this problems.
make -C /usr/src/linux-headers-$(uname -r)  M=$(pwd) modules
make: Entering directory  `/usr/src/linux-headers-2.6.32-23-generic'
make: *** No rule to make  target `linux'.  Stop.
make: Leaving directory  `/usr/src/linux-headers-2.6.32-23-generic'

any body has some idea  to solve it?
thanks advance &#65281;

---

