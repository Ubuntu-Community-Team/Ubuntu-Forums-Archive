---
title: "Can't remove a file!"
date: 2012-03-08
forum: General Help
---

### Post by Alan.Brown on 2012-03-08
I am developing a short C program using Code::Blocks.  An error arose saying that there was not enough space on the disk - which is false.

I have traced the problem to a file in **/proc **called **kcore** of 128TB !!

I have tried **sudo rm -f /proc/kcore** and get the following message

> **rm: cannot remove `/proc/kcore': Operation not permitted**How can I get rid of this file??  What is it??  A core dump?? Of that size??

TIA

Alan

---

### Post by TeoBigusGeekus on 2012-03-08
Try rebooting and see if it persists.

---

### Post by lechien73 on 2012-03-08
The files in proc are virtual filesystems - they're not actually files per se, and don't take up hard disk space. They're more like windows into your kernel operation.

/proc/kcore is like a symbolic link for the memory in your computer, so it doesn't take up any space on your hard disk.

To check available disk space, you can open a terminal window and type:

```
df -h
```

Or, you can find files over a certain size by typing:

```
find / -name '*' -size +1G
```

Which will find all files on the disk, which are 1Gb or larger.

---

### Post by papibe on 2012-03-08
/proc/kcore is a virtual file, like an alias to access the RAM.

It really does not take the amount of space you think. Try this:
```
du -sh /proc/kcore
0
```
I wouldn't recommend trying to delete it.

Hope it helps.
Regards.

---

### Post by Alan.Brown on 2012-03-08
Thanks for all your replies.

I have rebooted several time - same thing.

I realise that the **/proc** 'files' are virtual - but how did **kcore** get there and why does it persist?  It must be recreated at each start-up.

I will leave it and live with it :D but am curious.

Alan

---

### Post by lechien73 on 2012-03-08
/proc/kcore is a virtual "file" that is the size of the maximum amount of RAM the kernel can allocate. On 64-bit systems, this is 128Tb.

If you were to page through portions of the file, you would - in effect - be paging through your computer's RAM.

---

### Post by Alan.Brown on 2012-03-08
I think I understand now.

Thanks

Alan

---

