---
title: "how do i make simply graphic in gcc ubuntu"
date: 2010-02-24
forum: General Help
---

### Post by oz6oh on 2010-02-24
I would like to make 2 vertical lines and two horizontial lines around this program. please help me. I use gcc as compiler.

[email]olehasselbalch@gmail.com[/email]


 * Simple parallel port output control program for Linux
 *
 *
 * The program output the data value to PC parallel port data pins
 * (default lpt1 I/O address 0x378). The data values are given as the
 * command line parameter to the program. The number can be
 * in decimal (0..255) or hexadecimal format (0x00..0xFF).
 *
 */

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/io.h>

#define base 0x0378           /* printer port base address */

main(int argc, char **argv)
{                    
  int value;

  if (argc!=2)
    fprintf(stderr, "Error: Wrong number of arguments. This program needs one argument which is number between 0 and 255.\n"), exit(1);
  if (sscanf(argv[1],"%i",&value)!=1)
    fprintf(stderr, "Error: Parameter is not a number.\n"), exit(1);
  if ((value<0) || (value>255))
    fprintf(stderr, "Error: Invalid numeric value. The parameter number must be between 0 and 255\n"), exit(1);
  if (ioperm(base,1,1))
    fprintf(stderr, "Error: Couldn't get the port at %x\n", base), exit(1);

  outb((unsigned char)value, base);
}

---

### Post by rnerwein on 2010-02-24
hi
can you tell me what's your problem is ?
what is the output of your program when you run it ( what is the argv ) ?
do you run your program with root privileges ( CAP_SYS_RAWIO ) ?
ciao

--> c is like a razor blade but with out a grip :-)

---

### Post by oz6oh on 2010-02-24
Lieber freund. Besten dank fuwe antwort. Mein problem ist, wie mache ich ein Ramen rund mein program. Also wie ein kleine fenster.
Ole Hasselbalch  oz6oh als funkamateur

[email]olehasselbalch@gmail.com[/email]

---

### Post by oz6oh on 2010-02-24
> **rnerwein said:**
> hi
can you tell me what's your problem is ?
what is the output of your program when you run it ( what is the argv ) ?
do you run your program with root privileges ( CAP_SYS_RAWIO ) ?
ciao

--> c is like a razor blade but with out a grip :-)

Mein input ist ./p 1 oder ./p 255  und zahlen darzwischen

---

### Post by luisridaocruz on 2010-02-24
Hi,

I have used LVPM to resize my ubuntu root.disk from 25 GB to 30 GB.
But this was a big mistake because I had 61 GB in my /host drive and I seemed
to used it up all. I have not lost data because my work was in another partition
but Windows won't start up. I copy-paste the files ystem space usage (from ubuntu):

luisridaocruz@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             25G   22G  1.2G  95% /
udev                 1001M  332K 1000M   1% /dev
none                 1001M  252K 1001M   1% /dev/shm
none                 1001M   92K 1001M   1% /var/run
none                 1001M     0 1001M   0% /var/lock
none                 1001M     0 1001M   0% /lib/init/rw
/dev/sda1              61G   61G     0 100% /host
/dev/sdb1             233G  207G   27G  89% /media/New Volume
/dev/sda2              89G   52G   38G  59% /media/Data

How can I free up some of the memory in /host so that Windows will work?

Thanks in advance

---

### Post by rnerwein on 2010-02-24
> **oz6oh said:**
> Lieber freund. Besten dank fuwe antwort. Mein problem ist, wie mache ich ein Ramen rund mein program. Also wie ein kleine fenster.
Ole Hasselbalch  oz6oh als funkamateur

[EMAIL="olehasselbalch@gmail.com"]olehasselbalch@gmail.com[/EMAIL]

hi
i don't know if i understand you right. but if you want to have a simple ascii method to do
this ( in terminal windows - not on the printer ). you should use ncurses there are hundreds of function calls. e.g. box(WINDOW *win, chtype verch, chtype horch) see man pages for this.
hope this helps
ciao

---

### Post by oz6oh on 2010-02-24
> **rnerwein said:**
> hi
i don't know if i understand you right. but if you want to have a simple ascii method to do
this ( in terminal windows - not on the printer ). you should use ncurses there are hundreds of function calls. e.g. box(WINDOW *win, chtype verch, chtype horch) see man pages for this.
hope this helps
ciao
Lieber freund. Ich wollte rund mein programme ein rectagel bauen aber in fein graphic. Verstehst du mein frage?? Olehasselbalch

---

