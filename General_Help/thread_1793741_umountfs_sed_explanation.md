---
title: "umountfs sed explanation"
date: 2011-06-30
forum: General Help
---

### Post by charbo on 2011-06-30
Hello all,

I am trying to understand the shutdown unmounting process.
I traced that /etc/init.d/umounfs script seems to be responsible for unmounting all the mounted partitions.  However, I do not see how this script is unmounting all partitions...

It is probably because I don't understand the sed very well.
Can someone explain what 

sed -n '0,/^\/[^ ]* \/ /p' /proc/mounts

is doing?  

I understand that this prints only selected lines somehow. But what is the condition?

1. I read man page for 0,addr2 portion, but frankly, I don't understand the explanation.

" Start out in "matched  first  address"  state,  until  addr2  is found.  This is similar to 1,addr2, except that if addr2 matches the very first line of input the 0,addr2 form will be at the end of  its  range,  whereas	the  1,addr2 form will still be at the beginning of its range."

2. What pattern does /^\/[^ ]* \/ / match?
Isn't it the following?
Any line that starts with a "/" followed by non-space characters followed by a space and a "/" followed by a space?

Apparently this understanding is wrong, because the first line of output is
rootfs / rootfs rw 0 0

Any guidance, and explanation as to why that is the case is highly, highly appreciated.

Thank you so much for your help in advance.

---

### Post by DaithiF on 2011-06-30
Hi,
your understanding of the pattern is correct.

```
0,/pattern/p

```
says to print lines from the start of the file up to the first line that matches the pattern.

in short, its printing the contents of /proc/mount up until & including the mount point for the root of the filesystem (ie. / )

---

