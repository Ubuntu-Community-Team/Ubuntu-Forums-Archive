---
title: "df returning wrong available space"
date: 2010-02-02
forum: General Help
---

### Post by nicoseb on 2010-02-02
I am running Lucid on a barebone laptop. After running out of space, I emptied 3GB on my partition, started an application that filled up 1GB and all of a sudden my system dropped from 2G free of space to 0.

#uname -a
Linux brainless 2.6.32-12-generic #16-Ubuntu SMP Thu Jan 28 07:47:05 UTC 2010 x86_64 GNU/Linux

#df -h returns
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   35G  466M  99% /
none                  2.0G  300K  2.0G   1% /dev
none                  2.0G  1.2M  2.0G   1% /dev/shm
none                  2.0G  232K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G  4.0K  2.0G   1% /lib/init/rw
/dev/sda4              17G   14G  3.4G  81% /windows
/dev/sda5             243G  232G   11G  96% /data

It has nothing to deal with the journal or something, I even did the tune2fs, resize2fs... commands
I run a deep fsck with no luck.
There are not file over 1GB on my system, and I just ran out of ideas.
Now, if I run gparted, I get 2.31GB of unused space!

I know that they look at the free space two different ways, I don't really care about that, I care about the fact that Thuar and other applications believe I have only 400M of free space and that I run out of space when I should not!!!

If someone has a miracle solution that would make me happy! :)

thanks

---

### Post by rnerwein on 2010-02-02
hi
i even don't think it's cause by jornal. but what's about your default 5% reservation. do you used tune2fs -m  ??. 2.3 GB which you loose  looks for me like 1.9 gb reservation + 466 MB = 2.3 gb
ciao

---

### Post by nicoseb on 2010-02-04
Sorry I just said i was not reservation, but after running your command with -m 0 I got my 2GB back!!!
I'm just confused that this happened out of nowhere. My reservation block was 0% and all of a sudden it turned into 5% without me doing anything... kinda weird!

Anyway, thanks a lot! I'm glad to get my space back!

---

