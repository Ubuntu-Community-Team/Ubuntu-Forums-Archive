---
title: "How is ext fragmentation resistant?"
date: 2010-04-24
forum: General Help
---

### Post by s3a on 2010-04-24
I told my friend ext3 and ext4 are very fragmentation resistant compared to ntfs and he questioned me as to what happens if a small file was removed from in between other file chunks and then another (larger) file was to be written and it wouldn't fit there; where would it go? His argument was that the ext filesystem does need to defragment in order to get past that and his argument seems logical.

Does anyone know the answer to this? (because it actually captured my curiosity)

Any input would be appreciated!
Thanks!

---

### Post by dcstar on 2010-04-25
> **s3a said:**
> I told my friend ext3 and ext4 are very fragmentation resistant compared to ntfs and he questioned me as to what happens if a small file was removed from in between other file chunks and then another (larger) file was to be written and it wouldn't fit there; where would it go? His argument was that the ext filesystem does need to defragment in order to get past that and his argument seems logical.

Does anyone know the answer to this? (because it actually captured my curiosity)

Any input would be appreciated!
Thanks!

There are many things already on this subject with detailed explanations, a simple web search will offer a lot of them.

---

### Post by asmoore82 on 2010-04-25
Remember in your web travels that a lot of conversations/arguments regarding
"Linux Fragmentation" is _*not*_ talking about filesystems,
but instead the multitude of different distros available.

Also, the simple act of moving your files off of a filesystem and then copying them back
is quicker, easier, and safer than a traditional "defrag" utility.

---

### Post by s3a on 2010-04-25
But that doesn't answer my question as to what happens if you just emove a small file in between other files and then try to add a larger file that won't fit contiguously. Also, this was a conversation with my friend, not a web travel. The internet only seems to give me obvious answers.

---

### Post by QLee on 2010-04-25
> **s3a said:**
> But that doesn't answer my question as to what happens if you just emove a small file in between other files and then try to add a larger file that won't fit contiguously. Also, this was a conversation with my friend, not a web travel. The internet only seems to give me obvious answers.

To put this in simple terms and thus not be absolutely correct in every aspect:
Tell you friend that the paradigm for where to put the new, larger, file after the deletion of the smaller file is different on windows system. Traditionally, the difference is why those filesystems needed to defrag after use such as your friend proposed. Something similar could happen to ext too in the situation where the partition was getting critically low on space but in that case you have bigger problems than fragmentation slow down. It's just that your friend only understands the MicroSoft filesystems.

---

### Post by Sef on 2010-04-25
> But that doesn't answer my question as to what happens if you just emove  a small file in between other files and then try to add a larger file  that won't fit contiguously. Also, this was a conversation with my  friend, not a web travel. The internet only seems to give me obvious  answers. 	

This is one of the best [explanations]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting") for your question.

> dcstar: There are many things already on this subject with detailed  explanations, a simple web search will offer a lot of them. 	

Finding the right key words is not so easy for many people.  Next time please provide a link.

---

### Post by howefield on 2010-04-25
> **s3a said:**
> what happens if a small file was removed from in between other file chunks and then another (larger) file was to be written and it wouldn't fit there; where would it go?

It wouldn't be written there in the first place, unless there was no other place on the disk for it to go, aiui.

Although ext file systems are resistent to fragmentation, this does not mean that there is NO fragmentation.

Your original assertion is correct, 

```
ext3 and ext4 are very fragmentation resistant compared to ntfs
```

Your friends example doesn't change that.

---

