---
title: "Disable HFS+ journaling from within Ubuntu"
date: 2010-03-03
forum: General Help
---

### Post by Ancanus on 2010-03-03
Hello,

I have an external hard drive with a single HFS+ partition on it. I'd like to shrink this partition to make room for other partitions. It is to my understanding that I need to disable the HFS journaling before proceeding, and that journaling may be disabled from within MAC OSX.

I do not have access to an OSX machine so I was wondering if it was possible to disable Journaling from within Ubuntu? 


P.D: I would rather not wipe the whole hard drive and create the partitions from scratch.

Thanks.

---

### Post by Ancanus on 2010-03-05
I ended wiping the whole hard drive and creating partitions from scratch.

This would be a nice project. I mean, implementing disable journaling can't be that difficult. Perhaps it's just a boolean flag somewhere or something.

---

### Post by Bladehawke on 2010-03-18
It *can* be done.  And there's code already written to do it.  Please see [http://dmunsie.wordpress.com/code/hacks/]("http://dmunsie.wordpress.com/code/hacks/") and [http://loquerasparalinux.blogspot.com/2009/02/hfsplus-desactivando-journaling-sin.html]("http://loquerasparalinux.blogspot.com/2009/02/hfsplus-desactivando-journaling-sin.html") for the particulars.  In short, dmunsie wrote a brief C program for OSX that can change the necessary bits in the partition header and the second link points to a very simple patch to make it compile under linux along with instructions for use.

---

### Post by Ancanus on 2010-03-19
Thanks, Bladehawke!
This will be definitely useful in the future.

---

### Post by rmtatum on 2010-06-28
Using information from the following link, I removed all references CFSwapInt32HostToBig and its dependencies and substituted CFSwapInt32HostToBig with bswap_32.

The program compiled (albeit with warning messages).

To run the program, simply use ```
sudo ./a.out /dev/sdXX
``` where /dev/sdXX is the partition you need to mount.

Then you should be able to mount using the following
```
sudo mount -t hfsplus -o rw,user /dev/sdXX /media/hfspart 
```

For your convenience, you may find the code at the following url:

[http://pastebin.com/7rvxR38d](http://pastebin.com/7rvxR38d)

---

### Post by kaar3l on 2010-11-25
Cannot get it compiled:S

```
gcc -o disable_journal disable_journal.c
disable_journal.c: In function ‘main’:
disable_journal.c:31: warning: format ‘%8.8x’ expects type ‘unsigned int’, but argument 2 has type ‘long unsigned int’
/tmp/ccz3QZ1P.o: In function `main':
disable_journal.c:(.text+0xfe): undefined reference to `bswap_32'
disable_journal.c:(.text+0x14f): undefined reference to `bswap_32'
collect2: ld returned 1 exit status

```

---

### Post by blink on 2011-01-01
I tweaked the code to compile cleanly on ubuntu.  The two line difference is highlighted in yellow on the pastebin link.

[http://pastebin.com/W8pfgHRe](http://pastebin.com/W8pfgHRe)

Cheers,
bk

---

### Post by BurgerKing on 2011-01-02
Thanks a lot, helped me a lot when fixing my hackintosh :D

---

### Post by jewnersey on 2011-10-18
can someone please help me with compiling this and getting it to work. im Noobuntu..

---

### Post by oldos2er on 2011-10-18
Please start a new thread for your problem, and give as much detail as possible.

---

