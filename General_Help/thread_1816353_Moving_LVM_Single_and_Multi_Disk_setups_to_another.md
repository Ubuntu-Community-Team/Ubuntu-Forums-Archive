---
title: "Moving LVM Single and Multi Disk setups to another system?"
date: 2011-08-01
forum: General Help
---

### Post by shaggy999 on 2011-08-01
I am curious about how to go about moving an LVM setup from one system to another. I currently have a 1 TB drive that is formatted with LVM (this is a secondary disk for data storage only). I have actually re-installed the operating system several times leaving the LVM drive intact and it re-discovers the drive when I re-install the OS just fine (I just have to make sure LVM gets installed).

But I am wondering if there is an issue with moving it to a completely separate system. Also, is anything more complicated if I have a single LVM spread out over multiple drives? Is LVM smart enough to re-discover the proper drives plugged into a new motherboard?

The reason I ask is because I would like to move from 1x1TB -> 2x3TB setup. My 1 TB drive is full so I need at least one of the 3TB drives right now. But my server is an old PII 300 so the only system I can plug it into is my desktop (which is currently housing the 1 TB drive). At a later date (in 6 - 12 months) I would like to build a new server and migrate the drive over to the server.

Is there anything complicated I have to do, or can I just turn off my desktop, unplug the drives, plug them into the server, boot up, and run pvscan?

---

### Post by chrisem0 on 2011-08-10
Im curious to the answer to this because I would like to rebuild my server without having to reload all the data.  I use my Ubuntu PC to serve DVDs and Music to HTPCs.  However, i need to alter my LVM formatted as NTFS (2TB+1TB+400GB) to provide more space to my Home directory to setup a Virtual Box machine...  I cant find a way to edit the LVM without it breaking and the data being lost.

---

### Post by LiquidStranger on 2011-08-30
Afaik, moving the whole LVM-setup from one computer to another should not be a problem at all. Each PV (physical volume) stores the necessary metadata at least once, therefore it should work as long as you plug in all the drives that make up your lvm.

As far as altering a LVM, it depends on what exactly you want to change. Most changes (adding/removing a disk, changing logical volume size) can even be done while the system is in use.

I found [Markus Gattol's page]("http://www.markus-gattol.name/ws/lvm.html") a great source for information on LVM.

---

