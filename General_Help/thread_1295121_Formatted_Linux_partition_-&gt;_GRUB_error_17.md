---
title: "Formatted Linux partition -&gt; GRUB error 17"
date: 2009-10-19
forum: General Help
---

### Post by Gazilida on 2009-10-19
Since I didn't use Ubuntu anymore, I formatted the partition in Windows Vista so I would have more space for documents.

Problem is, I used GRUB as a boatloader and that has also been erased. 

Now I will have to redirect the boatloader to the Vista one.

How can I do this?

I have HP BIOS version F.0F and wasn't able to find any options to boot directly from my Vista partition.
I have a notebook and hence only one HD

---

### Post by renkinjutsu on 2009-10-19
if you've got a windows install CD, you can fix your mbr with that. If not, you can try booting into Vista from the Grub command line.. at the grub menu, press C (i think) and type things like

```
root (hd0,0)
rootnoverify
chainloader +1
boot
```

but i'm not sure, as i have nearly no knowledge of GRUB

---

### Post by Gazilida on 2009-10-19
I don't have a Vista CD, as I use an image that I downloaded from my company's server.

Also, the error is a fatal error and I can't (or at least don't know how to) bring up the command line.

But thanks for the help :)

---

### Post by louieb on 2009-10-19
You will need a Vista Install or recovery CD. [Vista Recovery Disc — NeoSmart]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")
Boot to recovery console [Bootrec.exe tool Vista (MS support)]("http://support.microsoft.com/kb/927392")
```
bootrec.exe /fixmbr
```

---

