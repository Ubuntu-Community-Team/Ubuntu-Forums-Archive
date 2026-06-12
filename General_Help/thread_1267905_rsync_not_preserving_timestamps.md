---
title: "rsync not preserving timestamps"
date: 2009-09-16
forum: General Help
---

### Post by kigali on 2009-09-16
I don't know what I'm doing wrong, or where possibly the hook is...

I'm trying to copy files preserving their modification time timestamps. I used

cp -p
rsync -a
rsync -t

both in on my machine (jaunty) and through ssh to work server (intrepid). And it simply does not work... It sets as modification time the time of the file creation (of the copy). 

Any suggestion what the problem may be? Pls help!

---

### Post by sedawk on 2009-09-16
rsync -a should work.

Can you try to copy some files to the "ramdisk" at /dev/shm
locally and to the remote machine to check if there
might be any issues with the file systems you are using:

```

rsync -a ./testfile.txt /dev/shm
rsync -a ./testfile.txt remote:/dev/shm # rsync over ssh

```

If this works as expected (timestamp of testfile.txt is
copied too), copy the file to the target file system 
you normally use and check if it stops working again.

---

### Post by gaussian on 2009-09-16
This could be a permission problem too. My recollection is that in order to modify timestamps you need to be root (use sudo). But I might be wrong...

---

### Post by kigali on 2009-09-17
> **sedawk said:**
> rsync -a should work.
 ```

rsync -a ./testfile.txt /dev/shm
rsync -a ./testfile.txt remote:/dev/shm # rsync over ssh

```

I've tried both. The timestamps got changed though.

I've tried also gaussian suggestion to use sudo. Not working neither.

This is very strange. Could it be because of hpet being disabled (high precision event timer, i disabled it as some ppl reported problems with it for overall machine stability, it seemed to be an issue for me to, nevertheless i guess then it was disabled by default for newest kernel by ubuntu dev team)? This is the only trace I can think of...

---

### Post by kigali on 2009-09-17
It's solved. Stupid me!!!

 I didn't read carefully and took timestamp under flag -c as time of last modification of file, not its status.

There are three different timestamps: modification time (ls -l), access time (ls -lu), time of last modification of file status information (ls -lc). The last is the only one which changes when using rsync -a.

Thanks for all responses!

---

