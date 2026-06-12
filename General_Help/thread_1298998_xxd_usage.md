---
title: "xxd usage"
date: 2009-10-23
forum: General Help
---

### Post by v.cecchetto on 2009-10-23
Hi all!

I am playing with hard disk image, and reverse dumping with xxd.


!!! BE AWARE !!!

The next command lines are for people that knows exactly what they are doing.

You can loose all your data if you don't know exactly what you are doing... 

Don't execute the next command if you are a beginner or you can loose all your data. 

I'am NOT responsible if you damage your hard disk using the following commands.

!!! BE AWARE !!!


Ok. I start.

I have a pendrive in /dev/sdc, about 256MB.

I use xxd command to create a file image of all its bytes.

$ xxd -a -g 1 /dev/sdc > pendrive.xxd

(naturally you have to be a superuser)

This command give me an hexdump of all bytes in the pendrive, something like this:

..........................................................................
0000000: fa b8 00 10 8e d0 bc 00 b0 b8 00 00 8e d8 8e c0  ................
*
f99fff0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
..........................................................................

The * indicate that the bytes:

- from 0000000 to f99fff0  

are all zero.

After this I mess with my pendrive content writing a lot of stuff in it, with an hexeditor, till I get the following pendrive content:

$ xxd -a -g 1 /dev/sdc

..........................................................................
0000000: aa bb cc dd 00 00 00 00 00 00 00 00 00 00 00 00  ................
*
0008000: 44 55 66 77 00 00 00 00 00 00 00 00 00 00 00 00  DUfw............
*
f99fff0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
..........................................................................

Notice the fact that i changed the first 16 bytes and some bytes at address 0x8000.

Ok, suppose now i want to turn back to the original condition.

I give the following command (reverse dump):

(!!! REALLY HARMFUL !!!)

$ xxd -r pendrive.xxd > /dev/sdc

(!!! REALLY HARMFUL !!!)

Ok, now I analyze my pendrive content, and i find the stuff at the 0x8000 not changed:

$ xxd -a -g 1 /dev/sdc

..........................................................................
0000000: fa b8 00 10 8e d0 bc 00 b0 b8 00 00 8e d8 8e c0  ................
*
0008000: 44 55 66 77 00 00 00 00 00 00 00 00 00 00 00 00  DUfw............
*
f99fff0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
..........................................................................

Wrong!

I need this:

..........................................................................
0000000: fa b8 00 10 8e d0 bc 00 b0 b8 00 00 8e d8 8e c0  ................
*
f99fff0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
..........................................................................

The stuff at the 0x8000 address still are in place, not fullfilled with zeroes.

If I use file instead of device i get the correct results. 

For now I solved this situation zeroing the device before doing a reverse dump.

I don't know if this is a bug of xxd or a wrong way to use it.

Someone other is playing with harddisk content and partition table?

---

