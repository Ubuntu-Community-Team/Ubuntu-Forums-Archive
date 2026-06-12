---
title: "tee in pipe changes data and causes error?"
date: 2010-12-23
forum: General Help
---

### Post by xerces8 on 2010-12-23
```
ubuntu@ubuntu:~$ lzop -d < .gvfs/store\ on\ otherpc.example.org/sda.img.lzo | sudo tee /dev/sda | md5sum
lzop: Invalid argument: <stdin>
7910e468a8ef83137532fa613b96c096  -
ubuntu@ubuntu:~$ lzop -d < .gvfs/store\ on\ otherpc.example.org/sda.img.lzo | md5sum
015da51a13009b6c69a5f06e26d09704  -

```

Why is there an error and different md5sum if I put tee in between?

This is reproducible.
The second MD5 sum is correct and same when testing on the other PC locally.

Any idea what is going on?

This is in Ubuntu 10.10 CD in the live environment (running inside VMWare Server v1.0.10 on Windowx XP).
lzop 1.02~rc1-2

---

### Post by gmargo on 2010-12-23
Unusual to use tee to write to a physical device but it should work.

Things to try for testing:

[LIST=1]
[*]Figure out why you get an lzop error on one command but not the other.
[*]Replace md5sum with "wc -c" to see if the sizes check.
[*]Replace /dev/sda with /dev/null to get the physical device out of the way.
[/LIST]

---

### Post by dcstar on 2010-12-24
> **gmargo said:**
> Unusual to use tee to write to a physical device but it should work.
.........

Why would tee be able to write to a BLOCK device?

It is supposed to **only** output to stdout or a file, a BLOCK device is not either of those.

---

### Post by gmargo on 2010-12-24
> **dcstar said:**
> Why would tee be able to write to a BLOCK device?

It is supposed to **only** output to stdout or a file, a BLOCK device is not either of those.

This is Unix.  Everything is a file.  To tee, /dev/sdb is a file.  It doesn't care about anything other than the **fopen** system call succeeding.

Try it yourself.  Perfect use for a virtual machine.

How about a character device?  Replace /dev/sdb with the tty device of another open terminal (use **tty(1)** to get name of terminal device, which will be something like /dev/pts/4).  You'll see the output show up on the other terminal.  (You should test with a text file instead of a binary!)

---

### Post by dcstar on 2010-12-25
> **gmargo said:**
> This is Unix.  Everything is a file.  To tee, /dev/sdb is a file.  It doesn't care about anything other than the **fopen** system call succeeding.

Try it yourself.  Perfect use for a virtual machine.
........

You are correct, I took the tee man page literally as only outputting to stdout and files - I didn't consider a block device would work with it as I only ever use things like dd with those.

As for the OP's issue, I would enclose that first command's file name in quotes and see if it makes any difference.

---

