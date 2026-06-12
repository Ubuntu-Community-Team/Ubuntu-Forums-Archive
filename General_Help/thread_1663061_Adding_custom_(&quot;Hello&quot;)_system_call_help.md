---
title: "Adding custom (&quot;Hello&quot;) system call: help"
date: 2011-01-09
forum: General Help
---

### Post by courteous on 2011-01-09
I'm trying to add a custom ("Hello world" :o) system call.
In [FONT="Fixedsys"]**/usr/src/linux/hello/**[/FONT] I put simple [FONT="Fixedsys"]**hello.c**[/FONT] ...```
#include "linux/linkage.h" // for linking a system call
#include "linux/kernel.h" // for "printk"

asmlinkage int sys_hello() 
{
	printk(KERN_ALERT "Hello!");
	return 1;
}
```... and in home directory [FONT="Fixedsys"]**helloTest.c**[/FONT]: ```
#include <stdio.h>
#include <sys/syscall.h>
#include <linux/unistd.h>

#define __NR_hello	338

int main()
{
	syscall(__NR_hello);
	return 0;
}
``` I compiled [FONT="Fixedsys"]**helloTest.c**[/FONT] and ran [FONT="Fixedsys"]**./a.out**[/FONT]: [COLOR="Red"]in [FONT="Fixedsys"]**/var/log/messages**[/FONT] nothing gets written![/COLOR] :cry:

Before _"compile & install & reboot"_ I did these steps ([FONT="Fixedsys"][COLOR="SeaGreen"]**linux**[/COLOR][/FONT] is symbolic link to [FONT="Fixedsys"][COLOR="SeaGreen"]**linux-2.6.35.10**[/COLOR][/FONT]):
[LIST=1]
[*]In [FONT="Fixedsys"]**/usr/src/[COLOR="SeaGreen"]linux[/COLOR]/arch/x86/include/asm/unistd_32.h**[/FONT], I've added/changed: ```
#define __NR_hello	 338
#define __NR_syscalls	 339
```
[*]In [FONT="Fixedsys"]**/usr/src/[COLOR="SeaGreen"]linux[/COLOR]/arch/x86/kernel/syscall_table.S**[/FONT], I've added (on the last line):```
.long sys_hello
```
[*]In [FONT="Fixedsys"]**/usr/src/[COLOR="SeaGreen"]linux[/COLOR]/hello**[/FONT], I've created a [FONT="Fixedsys"]**Makefile**[/FONT]:```
obj-y += hello.o
```... and in [FONT="Fixedsys"]**/usr/src/[COLOR="SeaGreen"]linux[/COLOR]**[/FONT], I've modified [FONT="Fixedsys"]**Makefile**[/FONT] and added [COLOR="Blue"]**hello/**[/COLOR] directory:```
core-y += kernel/ mm/ fs/ ipc/ security/ crypto/ block/ [COLOR="Blue"]**hello/**[/COLOR]
```
[*]In [FONT="Fixedsys"]**/usr/src/[COLOR="SeaGreen"]linux[/COLOR]/include/linux/syscalls.h**[/FONT], I've added (on the last line):```
asmlinkage long sys_hello(void)
```
[/LIST]

---

### Post by courteous on 2011-01-13
I've checked [FONT="Fixedsys"]System.map[/FONT] (in [FONT="Fixedsys"]/boot[/FONT] directory) and 'hello' is indeed there:
```
c015c3c0 T sys_hello
```

Does that imply that something is wrong with my test call, [FONT="Fixedsys"]helloTest.c[/FONT]?

EDIT: [FONT="Fixedsys"]**dmesg**[/FONT][COLOR="Blue"]*[/COLOR] ***does* print "Hello!"** on the last line, but there is **nothing in [FONT="Fixedsys"]/var/log/messages[/FONT]** file.


[COLOR="Blue"]*[/COLOR] **[FONT="Fixedsys"]dmesg[/FONT]** [FONT="Fixedsys"]- prints or controls the kernel ring buffer[/FONT]

---

