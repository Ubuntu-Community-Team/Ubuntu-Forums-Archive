---
title: "Compile simple Kernel Module Problem"
date: 2012-07-14
forum: General Help
---

### Post by SMFloris on 2012-07-14
Hello, this is my first time here and i come with a problem i have been trying to figure out for 2 days. I just want to compile a simple "hello_world" kernel module.

Here is my kernel module code (hello_module.c):
 ```

#include <linux/init.h>
#include <linux/module.h>

static int hello_init(void){
    printk (KERN_ALERT "Hello, I am a little module");     
    return 0;
}

static void hello_exit(void){
    printk (KERN_ALERT "Bye bye, nice to meet you");
}

module_init(hello_init);
module_exit(hello_exit);

```

This is my Makefile:
```

obj-m += hello_module.o

KDIR = /usr/src/linux-headers-3.2.0-26-generic

all:
    $(MAKE) -C $(KDIR) SUBDIR=$(PWD)

clean:
    rm -rf *.o *.ko *.mod *.symvers *.order

```

The problem comes when i go to the directory and make, i get the following error:
```

make -C /usr/src/linux-headers-3.2.0-26-generic SUBDIR=/home/smfloris/Desktop/Modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic'
make[2]: *** No rule to make target `arch/x86/tools/relocs.c', needed by `arch/x86/tools/relocs'.  Stop.
make[1]: *** [archscripts] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic'
make: *** [all] Error 2
```

I couldn't find my problem anywhere, nor the solution. As a note, i've checked the headers and found that i have the latest version; I would also like to add that i installed Ubuntu through the Wubi installer.

Any help is greatly appreciated,
Flo. 

P.S. Please keep it simple, as i am still a beginner

---

### Post by SMFloris on 2012-07-14
So, i found a solution while browsing some threads; I removed the static keywords from the "hello_module.c" and modified the Makefile as such:

```

obj-m += hello_module.o
 
all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
 
clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clea

```

---

### Post by cityprince143 on 2012-09-19
i am having same issue tried de solution you recommend but no use plz help me

Thamks in advance
Error:-

make -C /lib/modules/3.2.0-29-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
make[2]: *** No rule to make target `arch/x86/tools/relocs.c', needed by `arch/x86/tools/relocs'.  Stop.
make[1]: *** [archscripts] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
make: *** [all] Error 2


Make file

obj-m += hello_module.o
 
all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
 
clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean


please help me////already wasted 5-6 hours already :-(
I am a beginner. So try to make the solution simple

---

### Post by Koomikko on 2012-10-25
Hi,
I have the same problem as cityprince143 but not yet spent 5 hours with it. Please help.

---

### Post by ravinderdasila on 2013-03-06
I was facing same problem..getting the msg:

No rule to make target `arch/x86/tools/relocs.c', needed by `arch/x86/tools/relocs'.

The solution shown above didn't do me any good.

Then I updated my linux source:
$ sudo apt-get update
  $ sudo apt-get install linux-source.


After doing this, I found a new folder in /usr/src:  'linux-source-3.2.0'
Thus I had 4 folders now:
linux-headers-3.2.0-32/             linux-headers-3.2.0-32-generic-pae/
linux-headers-3.2.0-32-generic/     linux-source-3.2.0/

The 'linux-source-3.2.0/' folder contained 'linux-source-3.2.0.tar.bz2'. I unzipped it and now the contents were:
debian  debian.master  linux-source-3.2.0  linux-source-3.2.0.tar.bz2

Now I just wrote one line in my Makefile: 'obj-m := first_driver.o' and executed the make command:
sudo make -C /usr/src/linux-headers-3.2.0-32-generic-pae SUBDIRS=/home/isc/Desktop/first_driver.

Voila!!! this generated the .ko file..

---

### Post by jero2rome on 2013-03-12
In the make file, just change M=$(PWD) into M=$(shell pwd)...

Works like charm

---

