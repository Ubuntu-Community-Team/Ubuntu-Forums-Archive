---
title: "error while compilation of user device driver"
date: 2011-12-21
forum: General Help
---

### Post by sathish on 2011-12-21
Hi,
Im a newbie to linux and im trying to do a homework of adding a device to the kernel.
Please point out my mistakes in the forum :)

I am trying the sample driver memory.c which i googled to load into my kernel
my memory.c looks like this
```
#include <linux/init.h>


#include <linux/config.h>


#include <linux/module.h>


#include <linux/kernel.h> /* printk() */


#include <linux/slab.h> /* kmalloc() */


#include <linux/fs.h> /* everything... */


#include <linux/errno.h> /* error codes */


#include <linux/types.h> /* size_t */


#include <linux/proc_fs.h>


#include <linux/fcntl.h> /* O_ACCMODE */


#include <asm/system.h> /* cli(), *_flags */


#include <asm/uaccess.h> /* copy_from/to_user */


MODULE_LICENSE("Dual BSD/GPL");


/* Declaration of memory.c functions */ 
int memory_open(struct inode *inode, struct file *filp); 
int memory_release(struct inode *inode, struct file *filp); 
ssize_t memory_read(struct file *filp, char *buf, size_t count, loff_t *f_pos); 
ssize_t memory_write(struct file *filp, char *buf, size_t count, loff_t *f_pos); void memory_exit(void);
int memory_init(void);


/* Structure that declares the usual file / / access functions */ 
struct file_operations memory_fops = 
{ read: memory_read,
 write: memory_write, 
open: memory_open, 
release: memory_release };


/* Declaration of the init and exit functions */ 
module_init(memory_init);
module_exit(memory_exit);


/* Global variables of the driver / / Major number */ 
int memory_major = 60; 
/* Buffer to store data */ 
char *memory_buffer;

/*------------------------------------------------------*/
int memory_init(void) 
{
  int result;


/* Registering device */ 
result = register_chrdev(memory_major, "memory", &memory_fops);
 if (result < 0) 
{ 
printk( "<1>memory: cannot obtain major number %d\n", memory_major); return result;
 }


/* Allocating memory for the buffer */ 
memory_buffer = kmalloc(1, GFP_KERNEL);
if (!memory_buffer)
 { 
result = -ENOMEM; goto fail; 
} 
memset(memory_buffer, 0, 1);


printk("<1>Inserting memory module\n"); 
return 0;


fail: memory_exit(); return result;
 }


/*---------------------------------------------*/
void memory_exit(void)
 {
  /* Freeing the major number */
  unregister_chrdev(memory_major, "memory");


/* Freeing buffer memory */ 
if (memory_buffer)
 { 
kfree(memory_buffer);
 }


printk("<1>Removing memory module\n");


}
/*-------------------------------*/
int memory_open(struct inode *inode, struct file *filp) 
{


/* Success */
 return 0; 
}
/*-------------------------------*/

int memory_release(struct inode *inode, struct file *filp) 
{


/* Success */ 
return 0;
 }

/*-------------------------------*/


ssize_t memory_read(struct file *filp, char *buf, 
                    size_t count, loff_t *f_pos) 
{


/* Transfering data to user space */ 
copy_to_user(buf,memory_buffer,1);


/* Changing reading position as best suits */ 
if (f_pos == 0)
 {
 *f_pos+=1; return 1; 
}
 else
 {
 return 0;
 } 
}

/*-------------------------------*/

ssize_t memory_write( struct file *filp, char *buf,
                      size_t count, loff_t *f_pos) 
{


char *tmp;


tmp=buf+count-1; copy_from_user(memory_buffer,tmp,1); return 1; 
}
```


Makefile used is 
```
obj-m	+= memory.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

the error im getting is 


sathish@sathish-desktop:~$ make memory
cc     memory.c   -o memory
memory.c:1:24: error: linux/init.h: No such file or directory
memory.c:4:26: error: linux/config.h: No such file or directory
memory.c:7:26: error: linux/module.h: No such file or directory
memory.c:13:40: error: linux/slab.h: No such file or directory
memory.c:25:27: error: linux/proc_fs.h: No such file or directory
In file included from /usr/include/asm/fcntl.h:1,
                 from /usr/include/linux/fcntl.h:4,
                 from memory.c:28:
/usr/include/asm-generic/fcntl.h:96: error: expected specifier-qualifier-list before ‘pid_t’
memory.c:31:45: error: asm/system.h: No such file or directory
memory.c:34:49: error: asm/uaccess.h: No such file or directory
memory.c:37: error: expected declaration specifiers or ‘...’ before string constant
memory.c:37: warning: data definition has no type or storage class
memory.c:41: warning: ‘struct file’ declared inside parameter list
memory.c:41: warning: its scope is only this definition or declaration, which is probably not what you want
memory.c:41: warning: ‘struct inode’ declared inside parameter list
memory.c:42: warning: ‘struct file’ declared inside parameter list
memory.c:42: warning: ‘struct inode’ declared inside parameter list
memory.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘memory_read’
memory.c:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘memory_write’
memory.c:49: error: variable ‘memory_fops’ has initializer but incomplete type
memory.c:50: error: unknown field ‘read’ specified in initializer
memory.c:50: error: ‘memory_read’ undeclared here (not in a function)
memory.c:50: warning: excess elements in struct initializer
memory.c:50: warning: (near initialization for ‘memory_fops’)
memory.c:51: error: unknown field ‘write’ specified in initializer
memory.c:51: error: ‘memory_write’ undeclared here (not in a function)
memory.c:51: warning: excess elements in struct initializer
memory.c:51: warning: (near initialization for ‘memory_fops’)
memory.c:52: error: unknown field ‘open’ specified in initializer
memory.c:52: warning: excess elements in struct initializer
memory.c:52: warning: (near initialization for ‘memory_fops’)
memory.c:53: error: unknown field ‘release’ specified in initializer
memory.c:53: warning: excess elements in struct initializer
memory.c:53: warning: (near initialization for ‘memory_fops’)
memory.c:57: warning: data definition has no type or storage class
memory.c:57: warning: parameter names (without types) in function declaration
memory.c:58: warning: data definition has no type or storage class
memory.c:58: warning: parameter names (without types) in function declaration
memory.c: In function ‘memory_init’:
memory.c:81: error: ‘GFP_KERNEL’ undeclared (first use in this function)
memory.c:81: error: (Each undeclared identifier is reported only once
memory.c:81: error: for each function it appears in.)
memory.c:86: warning: incompatible implicit declaration of built-in function ‘memset’
memory.c: At top level:
memory.c:116: warning: ‘struct file’ declared inside parameter list
memory.c:116: warning: ‘struct inode’ declared inside parameter list
memory.c:116: error: conflicting types for ‘memory_open’
memory.c:41: note: previous declaration of ‘memory_open’ was here
memory.c:125: warning: ‘struct file’ declared inside parameter list
memory.c:125: warning: ‘struct inode’ declared inside parameter list
memory.c:125: error: conflicting types for ‘memory_release’
memory.c:42: note: previous declaration of ‘memory_release’ was here
memory.c:136: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘memory_read’
memory.c:158: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘memory_write’
make: *** [memory] Error 1
sathish@sathish-desktop:~$ 
Please let me know the reason for this error , i tried 
sudo apt-get update
but in vain.
sathish@sathish-desktop:~$ cat /proc/version
Linux version 2.6.32-37-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011

Thanks in advance.

---

### Post by sathish on 2011-12-21
Any help is highly appreciated.

---

### Post by azmyth on 2011-12-21
Do you have the kernel header files package installed?

---

### Post by sathish on 2011-12-22
Hi 
thanks for the reply.
i have tried 
sudo apt-get install linux-headers-$(uname -r)
[sudo] password for sathish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.32-37-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-36 linux-headers-2.6.32-36-generic sdparm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

then i tried compile the module but the same error is what i got.

from the error i make out that the kernel.h(for which there is no error) is there under /usr/include/linux
but other header files are not there.

I havent compiled any source code and many header files are missing in my system i guess.
I have downloaded linux-3.1.5.tar.bz2
do i want to do something with this?


Please help in getting rid off the errors.

Thanks in advance.

---

