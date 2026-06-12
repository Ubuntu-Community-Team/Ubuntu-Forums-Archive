---
title: "how to access ext4 partition in windows xp"
date: 2009-07-04
forum: General Help
---

### Post by luvuman on 2009-07-04
hi...i have installed the jaunty jacklop (9.04 )in my desktop machine. and im using dual booting system with XP. now i want to access some files in my linux partition through windows XP. i only need a read only access.i just want to copy some files from linux partition to windows partition(of course without booting ubuntu and transfer files to win partition)....any idea(tool) how to do it... :KS

---

### Post by alphacrucis2 on 2009-07-04
> **luvuman said:**
> hi...i have installed the jaunty jacklop (9.04 )in my desktop machine. and im using dual booting system with XP. now i want to access some files in my linux partition through windows XP. i only need a read only access.i just want to copy some files from linux partition to windows partition(of course without booting ubuntu and transfer files to win partition)....any idea(tool) how to do it... :KS

I don't think you can yet.. There are tools available for reading ext3 but last I looked ext4 wasn't supported to date.

---

### Post by jenkinbr on 2009-07-04
> **alphacrucis2 said:**
> I don't think you can yet.. There are tools available for reading ext3 but last I looked ext4 wasn't supported to date.
+1

A bit of googling turned up the same.

---

### Post by luvuman on 2009-07-04
> **alphacrucis2 said:**
> I don't think you can yet.. There are tools available for reading ext3 but last I looked ext4 wasn't supported to date.

> **jenkinbr said:**
> +1

A bit of googling turned up the same.



ohh..noo.....is that soo....
in that case i guess i have to do that in old fashion way :( ...goto ubuntu and transfer the files to the win partition...bla bla....
anyway...thanks for replying buddy... :KS ):P

---

### Post by Eestlane on 2009-09-25
A little old topic, but this would be really useful. I hate it if I have to switch the OS to view one file from Ubuntu's drive. 

Also, as I share my connection, I don't want others to loose it fow 2 minutes.

---

### Post by Nyken on 2009-12-22
I made a small partition just for inter-OS transfers. Not perfect, but it helps.

---

### Post by chilenoneto on 2010-01-03
> **Nyken said:**
> I made a small partition just for inter-OS transfers. Not perfect, but it helps.

this is a "elegant" solution, but may need to log in your ubuntu to  put files on the partition... 

Looking for a solution too... there is no way that i can access my files from my karmic/ext4 home partition from windoze... where i need to login to access my corporate apps.. .sadly not wine compatible (but soon to be i hope ... :twisted: )

---

### Post by The Cog on 2010-01-03
We have one app at work that doesn't work in wine. So I run XP inside VirtualBox when I need to run that app. VirtualBox can arrange to share folders between the host and guest OS.

---

### Post by Martin McFly on 2010-02-18
Hello. Is there at the moment some way how to access it ? I've tried few tools, but they weren't able to load it (due to 256 I suppose?).

So, do you know about some software/app/tool, which can access my data ?

---

### Post by rnerwein on 2010-02-18
> **luvuman said:**
> hi...i have installed the jaunty jacklop (9.04 )in my desktop machine. and im using dual booting system with XP. now i want to access some files in my linux partition through windows XP. i only need a read only access.i just want to copy some files from linux partition to windows partition(of course without booting ubuntu and transfer files to win partition)....any idea(tool) how to do it... :KS

hi
what's about an usb-stick formated ntfs. both systems can use it. you can mirror it via rsync.
ciao

---

### Post by mregmi on 2010-04-04
Hi,
  You can use the new release of Ext2read to vview copy ext4 file systems with extents enabled. You can download it from [http://ext2read.sf.net](http://ext2read.sf.net)

release thread is here:
[http://sourceforge.net/mailarchive/forum.php?thread_name=v2y652016d31004041148kb1f7f4cn3414d44ce52be20d@mail.gmail.com&forum_name=ext2read-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=v2y652016d31004041148kb1f7f4cn3414d44ce52be20d@mail.gmail.com&forum_name=ext2read-devel)

regrads
Manish Regmi

---

### Post by Dusal on 2010-04-26
Thank you mregmi. You life saver :)

---

### Post by davidpaul2020 on 2010-08-14
> **Nyken said:**
> I made a small partition just for inter-OS transfers. Not perfect, but it helps.

That's a good idea. I made a 3GB Fat32 partition and named it COMMON DRIVE, where I copy files which I need to access from either Windows or Linux.

Another option would be at the point of installing Ubuntu. Create one partition in ext3 or ext4 for ubuntu's boot drive, and another FAT32 partition as the home drive. That way all your documents, music, pictures, etc in ubuntu will automatically be saved in the FAT32 partition, which will be readily accessible from Windows.

---

### Post by Ginsu543 on 2010-08-15
If you do a lot file transfers between Ubuntu and Windows, you might consider creating a large NTFS partition to keep your data in. Ubuntu has no problems accessing NTFS partitions and Windows will obviously see it since it is its native format.

---

### Post by Fludizz on 2010-08-15
That's what I generally recommend as well when using dual boot win/linux systems:
Use relatively small OS partitions and one large NTFS partition for data storage. Windows is a b*tch with non-windows filesystems and linux happily uses any windows filesystems.

---

### Post by Ginsu543 on 2010-08-15
Yup, this. On my 1 TB drive, I allocate 100 GB for OS (/ and /home) and 900 GB in NTFS for data (music, pictures, movies, etc.). That way, no matter what system (Ubuntu or Windows) or manner (dual-boot or samba shares over wireless network), my data files are always accessible by every computer I have.

---

### Post by ramnathsagar on 2010-08-26
Hello,
I have a lenovo T400 laptop. I recently, I installed ubuntu 9.10 (prev had Suse) along with Windows. Before I was able to access the data using ext2 . But after I did clean install of ubuntu, I was no longer able to read the data. 
I thought it might be because the default format is ext4, but when I did fdisk -l, it shows that the partition where ubuntu is installed is ext3.
I tried different softwares, but none worked. can anyone help me out.?

---

### Post by haringwati on 2011-02-21
> **ramnathsagar said:**
> Hello,
I have a lenovo T400 laptop. I recently, I installed ubuntu 9.10 (prev had Suse) along with Windows. Before I was able to access the data using ext2 . But after I did clean install of ubuntu, I was no longer able to read the data. 
I thought it might be because the default format is ext4, but when I did fdisk -l, it shows that the partition where ubuntu is installed is ext3.
I tried different softwares, but none worked. can anyone help me out.?

Are you trying to access your Ubuntu partitions while running Windows?  You can try Ext2Fsd.  The latest version claims to have extents readonly support for ext4.  See here: [http://www.ext2fsd.com/?p=74](http://www.ext2fsd.com/?p=74)

---

### Post by sankeerthana on 2011-05-09
Hi,
The solution is **ext2read**
Please check this link.
Works well for ext3 and ext4.

[http://sourceforge.net/projects/ext2read/]("http://sourceforge.net/projects/ext2read/")
:D :D

---

### Post by Comp_Tech_7C3 on 2011-05-22
Try this little program from DiskInternals :KS
 
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by linuxinstalledfromhdd on 2011-05-22
Build a NAS external hard drive. Hook it to your network's router.  It makes a great inexpensive file server.  Most people have a spare old hard drive around that can be put to use. The enclosure is pretty cheap on ebay.  Get a gigabit kind if you can afford one.  No more hassle with usb drives that give out eventually.

---

### Post by tcf38012 on 2011-12-18
Try This:

[http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)

I Just Found It

PS: Sorry For Being old thread just found it on google

EDIT: Well Someone else posted lol

Maybe i Should look next time

---

