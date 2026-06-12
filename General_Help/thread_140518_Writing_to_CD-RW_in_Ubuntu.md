---
title: "Writing to CD-RW in Ubuntu"
date: 2006-03-06
forum: General Help
---

### Post by wpshooter on 2006-03-06
How do I either format a CD-RW in Ubuntu or how do I re-write to a CD.

I am used to using Roxio in Windows, which allows me to basically use a CD-RW just as if it were another drive, i.e. I can format it, copy and paste to it, and drag & drop to it.

In Ubuntu when I attempt to write a new file to a CD, it makes me erase the previous contents off of the CD before I can write to it, am I missing something ?  Is there a hidden parameter somewhere that needs to be set in order to allow me to write to a CD multiple times without having to erase the previous contents each time.  I have tried to change the permissions for the CD but it says I can not change permissions to allow writing to the CD because it is a read-only CD.  I know this is a CD-RW (Sony) and a CD-RW capable drive (Plextor) because I can write & re-write to it all day long over on the Windows side.

Thanks.

---

### Post by evilgold on 2006-03-06
I personally use k3b for most of my burning. Its pretty easy to use, you can erase cd-rws, and rewrite to CD-Rs. Perhaps that will work better for you?

---

### Post by pbransford on 2006-03-06
What roxio does is called packet writing. I forget what filesystem that uses but it isn't an ISO system.

---

### Post by Ramses de Norre on 2006-03-06
Is there a program available for ubuntu that can do that?
And can windows computers read it out of the box or do they need a special program?

---

### Post by bb002 on 2006-03-06
Believe it is a UDF Filesystem. The "udftools" exists in the multiverse. It contains tools for creating what you are after. Haven't installed or tested it. All I did was a synaptic search for "Packet Writing" with "name and description". Of the nine results I got only udftools didn't concern networking :).

[edit]
I believe windows XP was the first version of windows to natively support UDF filesystems. I think it still requires special software to create and write UDF Filesystems though. I don't use UDF so I don't really know much at all or if what i do know is accurate...

---

### Post by mikexgough on 2006-03-06
K3b works for me fella, I have used Nero on windoze and also Easy CD creator from Roxio and they dont come close to K3b, use it and see how poor the windoze software really is

---

### Post by wpshooter on 2006-03-06
How/where do I find K3b ?  Is it on this website or is it located in the Ubuntu O/S ?

Thanks.

---

### Post by evilgold on 2006-03-06
[QUOTE=wpshooter]How/where do I find K3b ?  Is it on this website or is it located in the Ubuntu O/S ?

Thanks.[/QUOTE]

open up a terminal and type ```
sudo apt-get install k3b
```

or search synaptic for k3b

---

### Post by mr.p on 2006-03-07
Another good tool is "gnomebaker", very handy, I personally haven't used k3b as I like to keep all my applications GTK. :P

---

### Post by Zeroangel on 2006-03-07
(Nevermind)

---

### Post by wpshooter on 2006-03-07
[QUOTE=mikexgough]K3b works for me fella, I have used Nero on windoze and also Easy CD creator from Roxio and they dont come close to K3b, use it and see how poor the windoze software really is[/QUOTE]

Well, I tried the K3b and unless I am missing something, I really don't see this as being on par with the "**Drag to Disc**" portion/function of Roxio.

Thanks.

---

### Post by softgun on 2006-06-25
None of the apps - k3b, Gnomebaker etc. mentioned can do what you are asking - that is write to udf filesystems. Reading udf filesystems on CDRW is possible in Ubuntu.
Open a terminal and type something like
sudo mount -t udf /dev/cdrom /media/cdrom

To write to this is NOT possible by default in any linux version that I know of. But you can set it up if you like. 

[http://gentoo-wiki.com/HOWTO_Packet_Writing_on_CD-RW](http://gentoo-wiki.com/HOWTO_Packet_Writing_on_CD-RW)

If you want to use a DVD+RW
[http://lists.suse.com/archives/packet-writing/2006-Feb/0003.html](http://lists.suse.com/archives/packet-writing/2006-Feb/0003.html)

Best of luck!

---

