---
title: "Which command rounds better file sizes?"
date: 2011-01-13
forum: General Help
---

### Post by HotForLinux on 2011-01-13
Which command rounds better the file size?

```

me@mypc:~$ ls -l /tmp/Screenshot-Zimbra.jpg 
-rw-r--r-- 1 me me [COLOR=Red]173417[/COLOR] 2011-01-13 13:49 /tmp/Screenshot-Zimbra.jpg

me@mypc:~$ ls -lh /tmp/Screenshot-Zimbra.jpg 
-rw-r--r-- 1 me me [COLOR=Red]170K[/COLOR] 2011-01-13 13:49 /tmp/Screenshot-Zimbra.jpg

me@mypc:~$ ls -lk /tmp/Screenshot-Zimbra.jpg 
-rw-r--r-- 1 me me [COLOR=Red]170[/COLOR] 2011-01-13 13:49 /tmp/Screenshot-Zimbra.jpg


me@mypc:~$ du -b /tmp/Screenshot-Zimbra.jpg 
[COLOR=Red]173417[/COLOR]    /tmp/Screenshot-Zimbra.jpg

me@mypc:~$ du -h /tmp/Screenshot-Zimbra.jpg 
[COLOR=Red]172K[/COLOR]    /tmp/Screenshot-Zimbra.jpg

me@mypc:~$ du -k /tmp/Screenshot-Zimbra.jpg 
[COLOR=Red]172[/COLOR]    /tmp/Screenshot-Zimbra.jpg


```What is the reason for the difference?
Does ls show the apparent size?

---

### Post by 3Miro on 2011-01-13
They both agree on the bytes. 1 Kb = 1024b in computer terms or 1Kb = 1000b in some other cases. Depending on the definition of Kilo you mag get a discrepancy.

(BTW I tries couple of files on my machine and they always gave the same result for both du and ls)

---

### Post by HotForLinux on 2011-01-24
> **3Miro said:**
> They both agree on the bytes. 1 Kb = 1024b in computer terms or 1Kb = 1000b in some other cases. Depending on the definition of Kilo you mag get a discrepancy.

(BTW I tries couple of files on my machine and they always gave the same result for both du and ls)

I don't understand your reply. Both man pages (ls and du) say:

```
[B][FONT="Fixedsys"]
-k      like --block-size=1K

-h, --human-readable
        print sizes in human readable format (e.g., 1K 234M 2G)

--si   like -h, but use powers of 1000 not 1024[/FONT][/B]
```

---

### Post by AlphaLexman on 2011-01-24
Either way, you are comparing apples to oranges...

Using 1000k or 1024k , one file will be larger or smaller than the other.

---

### Post by HotForLinux on 2011-06-04
> **AlphaLexman said:**
> Either way, you are comparing apples to oranges...

Using 1000k or 1024k , one file will be larger or smaller than the other.

There's only one file here:  Screenshot-Zimbra.jpg
[COLOR=black]
[/COLOR]173417 bytes = 169.3525390625 KB =

 | = **170** KB _rounded up_
 |= 169 KB rounded down (nearest, but down)

(taking 1KB = 1024 bytes; traditional notation)

173417 bytes = 173.417 KiB =

 | = 174 KiB rounded up
 |= **173** KiB r_ounded down_ (nearest, but down)

(taking 1KiB = 1000 bytes; stupid new notation should be with "i")

But [COLOR=Red]**172**[/COLOR]?

The worst thing of all is that neither the input parameters nor the output specify what units are we talking about.
A COMPLETE MESS .

Linux could be much easier if hundreds of thousands of details like this one weren't left unpolished.

---

### Post by papibe on 2011-06-04
```
$ ls -l dummy
-rw-r--r-- 1 user user 173417 2011-06-04 14:36 dummy

$ du --apparent-size -h dummy
170K    dummy

```
From man du:
>  --apparent-size
[INDENT]print apparent sizes,  rather  than  disk  usage;  although  the
apparent  size is usually smaller, it may be larger due to holes
in (`sparse') files, internal  fragmentation,  indirect  blocks,
and the like
[/INDENT]

What is happening here is that du reports by default how much space is used in the hard drive to store the file. Data is saved in your hard drive by writing complete blocks. Even if your file has 1 byte of usable data, it will use 1 block of disk space.

This is an easy example. Here you can see that my hard disk uses 4K blocks:
```
~$ ls -l dummy2
-rw-r--r-- 1 user user  1  2011-06-04 14:58 dummy2

$ du -h dummy2
4.0K    dummy2

$ du --apparent-size -h dummy2
1       dummy2

```
Hope it helps.

---

