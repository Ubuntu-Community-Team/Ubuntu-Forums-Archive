---
title: "How to use unused hard disk space in /"
date: 2010-10-20
forum: General Help
---

### Post by csshreeram on 2010-10-20
I am the sole user of my laptop and i have the following hard disk space

```

Device       Directory     Type   Total         Free         Available  Used 
/dev/sda7    /             ext4     18.8GiB   15.4GiB   14.5GiB    3.4GiB
/dev/sda8    /home         ext4     33.5GiB   7.2GiB     5.5GiB     26.3GiB

```Now i want to use the free space in /(root) by moving files there.But i cannot create a folder or file in /.How do i go about this?

TIA
C.S.Shreeram
Ubuntu Newbie

---

### Post by Elfy on 2010-10-20
You would have to use sudo to do so. You'd be better off shrinking / and resizing /home in my opinion.

[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by silbak04 on 2010-10-20
You can install gparted, and mess with your partition tables using gparted. Run this in a terminal:

```

$ sudo aptitude install gparted

```

then for more information for gparted:

```

$ man gparted

```

---

### Post by Elfy on 2010-10-20
> **silbak04 said:**
> You can install gparted, and mess with your partition tables using gparted. Run this in a terminal:

```

$ sudo aptitude install gparted

```

then for more information for gparted:

```

$ man gparted

```

You'll need a livecd - either a linux livecd with a partition editor or a standalone partition editor.

---

### Post by csshreeram on 2010-10-20
Thanks guys will try it and get back to you..

How much should i leave in / directory and this would look like a stupid question to you guys but i have to ask...what exactly is in /? Been a windows user this long so long. Does the OS files as in Windows and Program Files reside in / directory? 

Thanks Again
Shreeram:popcorn:

Edit

I do have a 10.04 Live cd from which i installed Lucid.Will it work?

---

### Post by Elfy on 2010-10-20
> **csshreeram said:**
> Thanks guys will try it and get back to you..

How much should i leave in / directory and this would look like a stupid question to you guys but i have to ask...what exactly is in /? Been a windows user this long so long. Does the OS files as in Windows and Program Files reside in / directory? 

Thanks Again
Shreeram:popcorn:

Edit

I do have a 10.04 Live cd from which i installed Lucid.Will it work?

There are no stupid questions.

/home will contain your personal data. / contains the rest - and would also contain /home if you did not have a seperate partition for it.

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Yes there is a partition editor in the lucid livecd - system admin menu

You will likely need to turn off swap before you can change the partitions - right click the dswap partition and turn it off

If you leave 8Gb in / that should be more than sufficient, depending on what you install.

---

### Post by csshreeram on 2010-10-21
Hello Again


Using Gparted in Live CD worked like a charm.As you said shrinked/moved /dev/sda7 to 8gig and resized /dev/sda8.Thanks again for clearing / doubt.

You guys :guitar:

Shreeram

---

