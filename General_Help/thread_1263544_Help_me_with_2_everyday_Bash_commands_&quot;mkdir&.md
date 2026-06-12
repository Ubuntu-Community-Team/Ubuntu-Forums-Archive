---
title: "Help me with 2 everyday Bash commands &quot;mkdir&quot; &amp; &quot;?&quot; - beginner level"
date: 2009-09-11
forum: General Help
---

### Post by nomnex on 2009-09-11
Question ONE (MKDIR):

mkdir -p Ubuntu/Topic1 > will create ONE directory (Ubuntu) with ONE sub directory (Topic1) inside of it.
mkdir -p Ubuntu/Topic 1 Topic 2 > wil create ONE directory (Ubuntu) with ONE sub directory (Topic 1) inside of if and ANOTHER directory (Topic2)

I want to create ONE directory and AS MANY sub directories or sub-sub directories I want.
a. what is the first command: One main directory + many  sub directories (second level)
c. what is the second command: One main directory + x sub directories (second level)+ x sub-sub directories (third level)

Question TWO (I don't know the command name):

My USB HD has 2 partitions. Every time I connect it to the USB jack, there are 2 icons on my Desktop. That's fine, but everytime I want to disconnect it, I have to UNMOUNT 2x (unmount part 1 and umount part 2)
How can I umount all the partitions of the USB disk with ONE command?

Thanks

---

### Post by miklcct on 2009-09-11
1a
```

mkdir -p top/{dir1,dir2,dir3}

```
creates top/dir1 top/dir2 top/dir3

1b
```

mkdir -p a/{a/{a,b,c},b/{d,e,f/{x,y}}}

```
creates a/a/a a/a/b a/a/c a/b/d a/b/e a/b/f/x a/b/f/y

2
```

sudo umount /dev/sdc1 /dev/sdc2

```
unmounts /dev/sdc1 and /dev/sdc2

---

### Post by nomnex on 2009-09-11
@miklcct

Thanks for that, it s going to be a time saver :D

How can I create a file (like a batch under window) to run this on a double click?

```
sudo umount /dev/sdc1 /dev/sdc2
```

> I hates proprietary software very much so I have installed only few pieces of them and most of them are partially free and open source. 

That's a good one.

---

### Post by aesis05401 on 2009-09-11
For short scripts you can string commands together and place them in the 'command' field of a desktop launcher (icon).  Otherwise you should check out tldp.org's bash tutorial for writing shell scripts, then you just include a path to the script in the command field of teh desktop launcher.  Make sure you have the correct 'Type' selected for the command you are going to run.

---

### Post by meborc on 2009-09-11
> **nomnex said:**
> @miklcct

Thanks for that, it s going to be a time saver :D

How can I create a file (like a batch under window) to run this on a double click?

```
sudo umount /dev/sdc1 /dev/sdc2
```



That's a good one.

make a text file with this inside (the name of the file is not important):
> #!/bin/bash
gksudo umount /dev/sdc1 /dev/sdc2


then make the text file executable by right-click -> properties -> permissions (or similar... make executable)

now when you double-click on the file, it will prompt for password and then unmount the devices

---

### Post by nomnex on 2009-09-11
meborc, thank you.

Edit: oups, I forgot, [aesis05401]("http://ubuntuforums.org/member.php?u=736896") thanks for the link, nice bash tutorials.

---

