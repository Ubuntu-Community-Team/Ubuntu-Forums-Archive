---
title: "Removing all traces of Ubuntu"
date: 2011-11-01
forum: General Help
---

### Post by loseby on 2011-11-01
I guess I am talking about the MBR and GRUB. I am going to remove 11.10 from one of my PC's. Wireless is a nightmare on it so am putting Windows back on it and want all traces of Ubuntu removed from a Seagate 1TB drive.

Will the Win7 installation disc do this or do I need something else ?
btw: am not dumping Ubuntu as I have it installed on an external hard drive and this I use for all financial transactions and I am happy with

---

### Post by christopher.wortman on 2011-11-01
No wireless issues with KDE/Kubuntu. The network manager in Gnome 3.2 is kinda broken, you can try the KDE version of Ubuntu as it works so much better in every way.

To answer your other question, delete all partitions including /boot if there is one, format and you should be fine. Linux hasn't messed with the boot sectors of a hard drive in a long time... 2.4 if I last recall it was. But Windows should remove everything. If not Kubuntu is really spiffy.

---

### Post by matt_symes on 2011-11-01
Hi

> Will the Win7 installation disc do this ?

Yes it will. 

You might have to install grub on your external hard drive to boot Ubuntu though and edit the boot order when booting to Ubuntu.

> btw: am not dumping Ubuntu as I have it installed on an external hard drive and this I use for all financial transactions and I am happy with

You really don't have to defend installing Windows 7. I think it is a good OS. I am glad you like Ubuntu though.

Kind regards

---

### Post by Slim Odds on 2011-11-01
> **matt_symes said:**
> Hi

Yes it will. 

You might have to install grub on your external hard drive to boot Ubuntu though and edit the boot order when booting to Ubuntu.

You really don't have to defend installing Windows 7. I think it is a good OS. I am glad you like Ubuntu though.

Kind regards

That's not quite true. The Win7 installer gets very confused if it finds GRUB on the MBR.

To the OP, you might have to wipe out the MBR to get the Win7 installer to play nice. I had this problem with my laptop.

---

### Post by mordoc on 2011-11-01
I've often found it helpful to dump out to the command line and run fdisk /mbr to fix a Win7 install over any Linux.

> **Slim Odds said:**
> That's not quite true. The Win7 installer gets very confused if it finds GRUB on the MBR.

To the OP, you might have to wipe out the MBR to get the Win7 installer to play nice. I had this problem with my laptop.

---

### Post by christopher.wortman on 2011-11-01
> **matt_symes said:**
> 
You really don't have to defend installing Windows 7. I think it is a good OS. I am glad you like Ubuntu though.
Kind regards

I agree and Windows 8 will be just as good if not better I am using the windows developer preview and get updates and it is almost beta now, and it is faster and better than Windows 7. Microsoft is actually doing a good job.

---

### Post by loseby on 2011-11-03
> **matt_symes said:**
> Hi



Yes it will. 

You might have to install grub on your external hard drive to boot Ubuntu though and edit the boot order when booting to Ubuntu.



You really don't have to defend installing Windows 7. I think it is a good OS. I am glad you like Ubuntu though.

Kind regards

I like Ubuntu and the good thing about the external hard drive is I dont need grub  .... the F12 key whilst booting shows the hard drives including external and you just select and way you go

---

### Post by loseby on 2011-11-03
> **Slim Odds said:**
> That's not quite true. The Win7 installer gets very confused if it finds GRUB on the MBR.

To the OP, you might have to wipe out the MBR to get the Win7 installer to play nice. I had this problem with my laptop.

will the seagate tools do this ?

---

### Post by Slim Odds on 2011-11-03
> **losbey said:**
> will the seagate tools do this ?

I'm not sure. I used a LiveUSB Ubuntu and the dd program.

---

### Post by phDaemon on 2011-11-03
You could download gparted onto a livecd (or just get the ubuntu livecd) and reformat the hard drive deleting all the partitions...

---

