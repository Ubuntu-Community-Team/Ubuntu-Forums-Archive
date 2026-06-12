---
title: "Fill a file with &lt;n&gt; byets of a &lt;x&gt; value"
date: 2009-12-16
forum: General Help
---

### Post by vexy on 2009-12-16
Hello,

First of all I am sorry if this post is not in the properly thread.
This next example is to make you familiarly with my question. Let's say I want to fill a file 'test' with 5 bytes of zero and after that add in 'test' 7 bytes of random data.
```
#!/bin/bash
dd if=/dev/zero of=test bs=5 count=1
dd if=/dev/random of=test2 bs=7 count=1
cat test2 >> test
```On executing hexdump -C test i get the following:
```
hexdump -C test
00000000  00 00 00 00 00 00 00 00  00 00 00 00 3d 5d e1 be  |............=]..|
00000010  db 6c b7 3d 5d e1 be db  6c b7                    |.l.=]...l.|
0000001a

cat test
=]&#65533;&#65533;&#65533;l&#65533;=]&#65533;&#65533;&#65533;l&#65533;
```Well, supposed that you understand my problem, I would like to find out how to fill the file with <x> bytes of a number (natural). Example:

```
hexdump -C test_example
00000000  11 11 11 11 11 22 22 22  22 22 99 99 99 99 99 99
```I hope you know what I mean. Thanks a lot, and hope someone could light me up :)

---

### Post by BkkBonanza on 2009-12-16
Try, 

for x in {1..5}; do echo -en "\x35" >> test; done;

This example with count 5 and value hex 35 to file test. 
Modify as needed.

---

### Post by StuartN on 2009-12-16
> **vexy said:**
> Let's say I want to fill a file 'test' with 5 bytes of zero and after that add in 'test' 7 bytes of random data.

I can not replicate your result, so possibly there is an alias or locale-dependent conversion going on. Take one step back and write the files as:

```
#!/bin/bash
dd if=/dev/zero of=test1 bs=5 count=1
dd if=/dev/random of=test2 bs=7 count=1
cat test1 test2 >> test
hexdump -C test
```

Then test1 and test2 are the output of **dd** and for sure should contain what you describe, while test is the output of **cat** and may contain a conversion.

---

