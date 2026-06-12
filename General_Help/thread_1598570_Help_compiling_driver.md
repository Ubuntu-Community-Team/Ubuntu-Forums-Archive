---
title: "Help compiling driver"
date: 2010-10-16
forum: General Help
---

### Post by |Enraiha on 2010-10-16
I'm trying to Ubuntu 10.04 to run on a Plackard Bell EasyNote but my Ethernet port isn't working. I've searched these forums for a solution and it turns out that I need to compile my own driver. I found and downloaded the driver, with it was this readme.txt;

```
"make modules" fails on Redhat 8.0.It is kernel 2.4.18-14 , and it need driver 1.08.06.
You can individually compile the sis900.o with below procedures: 
a.Symbolic Links "asm" and "linux" to "/usr/src/linux-2.4.18-14/include/." 
a.1.Go to /usr/include directory 
a.2.mv asm asm_ ( or rm asm) 
a.3.mv linux linux_ (or rm linux) 
a.4.ln -s /usr/src/linux-2.4.18-14/include/asm asm 
a.5.ln -s /usr/src/linux-2.4.18-14/include/linux linux 
b.Create new directory and copy sis900.c and sis900.o into them. 
b.1 mkdir tmp 
b.2 cp -f sis900.c /tmp/sis900.c 
b.3 cp -f sis900.h /tmp/sis900.h 
b.4 cd /tmp 
b.5 gcc -DMODULE -D__KERNEL__ -Wall -Wstrict-prototypes -o6 -c -sis900.c 
c.Copy and replace sis900.o into "/lib/modules/2.4.18-14/kernel/drivers/net/." 
c.1 cp -f sis900.o /lib/modules/2.4.18-14/kernel/drivers/net/sis900.o  

```
I've got as far as b.5 but I get the following errors

gcc: unrecognized option '-sis900.c'
gcc: no input files

Can anyone help me continue?

Thanks.

---

