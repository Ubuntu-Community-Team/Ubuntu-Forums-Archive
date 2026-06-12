---
title: "Help with dd"
date: 2012-06-06
forum: General Help
---

### Post by Fisher on 2012-06-06
Hi.
I need to write a file from sector 8192 to sector 8610 of a harddisk.
Can it be done with dd without erasing the other sectors?
I have made a test with two small files, but have not found a way to do this.
In all my tries, I ended up erasing the end of the output file, wich is not desired. I tried dd if=teste of=teste1 seek=5 bs=1, the contents of teste was written to teste1 after the 5th character, but I've lost the end of the file, wich is not desired.
Can someone help?

---

### Post by HermanAB on 2012-06-07
Yes, Data Definition can do that.  You need to set the block size equal to the sector size, then use skip, seek and count.  You also need to know whether you should start at sector zero or one, so some testing is inevitable.  Read the man page.

---

### Post by Fisher on 2012-06-10
I have made some tests, and found a solution:
Created a file, test with 1234567890:
echo 1234567890 > test

Than, created a file named test 1 with 123456789012345678901234567890:
echo 123456789012345678901234567890 > test1

Then I tried:
dd if=teste of=teste1 bs=1 seek=15 conv=notrunc

and got in test1:
1234567890123451234567890
7890

So, to make it on hdd the command should be this one:
dd if=mbr.bin of=/dev/sdx bs=512 seek=15 conv=notrunc

I'm just waiting for my usb to hdd converter to arrive, so I can test it on the real hdd.

Thanks!!

---

