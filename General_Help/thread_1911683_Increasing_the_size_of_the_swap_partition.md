---
title: "Increasing the size of the swap partition"
date: 2012-01-19
forum: General Help
---

### Post by ChemMeister on 2012-01-19
Hi,

I have a code that uses a lot of memory (over 50 GB) and my RAM (16 GB) and current swap space (32 GB) are not enough. Is there way to increase the swap partition size without having to reformat the drive? I also heard you can use swap files (I have no idea how to do that), and can you have huge swap file >20 GB ? 
Thanks in advance

---

### Post by Buntumatic on 2012-01-19
You can use swap files as big as your filesystem can support. Or you can create a bunch of smaller files. 

See [http://ubuntuforums.org/showpost.php?p=11600983&postcount=12](http://ubuntuforums.org/showpost.php?p=11600983&postcount=12)

---

### Post by kevdog on 2012-01-19
Yes you can change the swap partition size, however I believe this partition needs to be the last partition on the hard drive if you want to resize it permanently.  You can use over things as swap partitions however and dynamically resize these.  What is your setup?

---

### Post by HermanAB on 2012-01-19
Howdy,

You can use a mix of disk and file based swap.  Read the swapon man page.  It is all explained in there:
$ man swapon

---

### Post by ChemMeister on 2012-01-19
Thank you all for the replies, I have a couple of questions. 

A) Is there a performance penalty for using a disk swap vs a file swap.

B) Creating a swap file seems easy enough, can you simply "delete" it when you are done

C) My swap partition is the last partition, so it should be easy to increase and change later if i choose to. 

Thanks again

---

### Post by jerrrys on 2012-01-19
I came across this just the other day and it is untried by me.

[dynamic swapping manager]("http://manpages.ubuntu.com/manpages/maverick/en/man8/swapd.8.html")

to install:

sudo apt-get install swapspace

---

### Post by Buntumatic on 2012-01-19
> **ChemMeister said:**
> Thank you all for the replies, I have a couple of questions. 

A) Is there a performance penalty for using a disk swap vs a file swap.

B) Creating a swap file seems easy enough, can you simply "delete" it when you are done

C) My swap partition is the last partition, so it should be easy to increase and change later if i choose to. 

Thanks again

A) There is always a performance penalty when you use slow HDD instead of fast RAM

B) Yes, just run swapoff on it first

---

### Post by ChemMeister on 2012-01-19
> **Buntumatic said:**
> A) There is always a performance penalty when you use slow HDD instead of fast RAM

B) Yes, just run swapoff on it first

No yes i know, i was referring to using a swap partition vs using a swap file.

---

### Post by Buntumatic on 2012-01-19
> **ChemMeister said:**
> No yes i know, i was referring to using a swap partition vs using a swap file.

Near to none. There may be a tiny overhead but I doubt it would be noticeable even on a 40 MHz 386.

---

### Post by ChemMeister on 2012-01-19
> **jerrrys said:**
> I came across this just the other day and it is untried by me.

[dynamic swapping manager]("http://manpages.ubuntu.com/manpages/maverick/en/man8/swapd.8.html")

to install:

sudo apt-get install swapspace

Thanks i wonder if there is an extra performance penalty for using dynamic vs fixed swap space.

---

### Post by HermanAB on 2012-01-19
Laak ah sed, read the swapon man page.  All your answers are in there.

---

