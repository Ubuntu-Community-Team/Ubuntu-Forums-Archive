---
title: "convert ntfs to ext4"
date: 2009-06-29
forum: General Help
---

### Post by mamali on 2009-06-29
i want to convert my ntfs drive to a ext
can i do this without losing my data

---

### Post by baseface on 2009-06-29
no.
just make backups and reformat, then restore data from your backups.

---

### Post by colau on 2009-06-29
> **mamali said:**
> i want to convert my ntfs drive to a ext
can i do this without losing my data
It's not possible.you will lose your data.

---

### Post by mamali on 2009-06-29
Tnx

---

### Post by mensoft2003 on 2009-08-20
Use Partition magic. you can do it with partition magic .:guitar:

---

### Post by afrodeity on 2010-02-09
And what happened? Did it work or did you lose your data?

---

### Post by Mark Phelps on 2010-02-09
> **mensoft2003 said:**
> Use Partition magic. you can do it with partition magic.

NO ... it doesn't.

I think you meant to say "Parted Magic" -- entirely different program.

---

### Post by afrodeity on 2010-02-09
Does parted magic work then?

---

### Post by Mark Phelps on 2010-02-10
> **afrodeity said:**
> Does parted magic work then?

That's what the website page claims.  Haven't used it myself so I don't know.

---

### Post by elliotn on 2010-02-10
I dont think it would work

---

### Post by gjoellee on 2010-02-10
> **elliotn said:**
> I dont think it would work

Me neither, it will format your drive I think...

---

### Post by afrodeity on 2010-02-11
That's what I thought. It turns up in searches for NTFS to EXT4 but I don't think its possible, unless some major reverse-engineering of the NTFS file system occurred overnight while nobody was looking? Maybe its finally been done? Linux hackers conquer NTFS, the proprietary Microsoft holy cow, news surely?

---

### Post by egalvan on 2010-02-11
Are you all talking about Parted Magic the Distro?

[http://partedmagic.com](http://partedmagic.com)

This is the only Parted Magic I found using google..

Of course, I've been using PartedMagic for over a year,
it's a great mini-distro for drive-type stuff
(partition, format, etc)

I use it so much, I became a subscriber early last year,
proud to support such a good distro.

---

### Post by Arenlor on 2010-02-11
I think likely what it does would seem like conversion, but is actually just it resizing the NTFS partition, creating an EXT4 partition, writing to it, resizing the NFTS partition again, writing to the EXT4 partition again, rinse and repeat until it has all been written. It probably takes less time on drives where a smaller percentage of the partition has been written to (for example if everything is in first 50% it will take only one go.

---

### Post by afrodeity on 2010-02-12
Ouch. So much can go wrong with such a procedure. Still holding out for somebody to crack NTFS and give us all a better method.

---

### Post by PASAf on 2013-01-08
You could easly convert ntfs to ext2 ext3 with **anyconvertfs** from anyfs-tools: [http://anyfs-tools.sf.net/](http://anyfs-tools.sf.net/)

Then you just need to convert it to ext4 with *tune2fs*.

That's all.

---

### Post by howefield on 2013-01-08
Old thread closed.

---

