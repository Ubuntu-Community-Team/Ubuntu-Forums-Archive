---
title: "Yet another MBR query, with apologies in advance..."
date: 2009-09-18
forum: General Help
---

### Post by mango42 on 2009-09-18
Hello,

I fully appreciate that queries on this topic must cause some grief amongst the Linux cognoscenti, for which I apologise in advance.

Despite the many excellent tutorials about partitioning on this forum, I've read so many other articles/suggestions on the net, I am *still* in a quandary about the MBR (Master Boot Record). Although I can find plenty of references to removing Ubuntu, conversely there's only 'Help!! My Windows went down' sort of articles on removing Windows.

At present I have a Grub-enabled triple boot system; an original Windows XP NTFS installation on the primary partition; an Ubuntu 8.10 upgraded to 9.04 with nVidia drivers (from an amd64 'Alternate Install' iso; I do not have a 9.04 LiveCD) on the first logical partition in the extended area of my hard disk and a 'clean, standard' install of amd64 9.04 in a second logical partition (this contains the *active* grub/menu.lst).

I would now like to free up some space by removing the Windows partition altogether. Having ventured into what looks like excellent programming in 'GParted' and following the help instructions under "Fixing GRUB boot problem" I get the following output:-

---------------------------
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,4)
 (hd0,6)

----------------------------

Yet from /boot/grub/menu.lst it appears to be hd0,0 (or as GParted reports /dev/sda1 )?

How do I safely remove the Windows partition without destroying the MBR? Resize the primary partition to, say, 1Gb or rebuild my system from square one - again...?

Once again, sorry for the 'tediousity' of this thorny topic.

---

### Post by fogNL on 2009-09-18
As far as I know, your MBR is not part of any partitions on the drive.

The MBR exists in the first 512 bytes of a hard drive, its only after this that your Windows partition starts.  You should be safe in deleting the Windows partition without affecting your MBR at all.

Theoretically, you can go into GParted and delete all your partitions on your hard drive, this will still not affect your MBR (except grub won't be able to see its config file on the linux partition).

---

### Post by Shujah on 2009-09-18
Some clarifications, If you have this triple boot on one HD then MBR is already used by Grub or you wouldn't be able to select both Windows & Ubuntu. But I don't know Grub is from which Ubuntu version, updated or standard install. Depends on what you installed first. If you delete and change the windows partition format to ext3 theoretically there wont be any difference in how GRUB boots since the entries for Grub 2nd and 3rd OS will remain the same (i.e. address hd0, 5 will remain the same). Thus you will be able to boot other two OS but selecting windows will give you an error. You wont be able to expand the 2nd partition to take place of first partition as one is primary and other are on the logical/ extended areas, even if you could you'll manually have to change grub entries because then the addresses of other two OS will change (i.e. address hd0, 5 will change to hd0, 4 thats just an example though as technically if 2nd OS partition which is logical extended, expands and takes place of primary partition address will become hd0, 0). Best option is go for a clean install delete windows and other partitions from within installation. Since we are talking about saving up place there seems to be no reason for keeping two same Ubuntu versions. I'll also recommend you Google around for Ubuntu partition scheme before making any changes and installation as adding removing partitions once Ubuntu is installed can be more challenging. For starters here is a scheme
/boot - 500 Mb (ext3)
/     - 10 GB  (ext3)    
/Home - 20 GB  (ext3) - More or Less depends on what you want here.  
/swap - 2 x Ram (if Ram < 2 GB) or 1 x Ram (if Ram > 2GB)
/Backup/Data/Media - Whatever you want to be accessed by other OS/ Distros (ext3 if you know you will only be using Linux afterwards - NTFS if there is a chance of Windows. Usually backups & media files go here. 

 This scheme is for home-user. For server environment you may need to add /var /opt /tmp etc. 

Note: ext3 appears to be more stable then ext4 at this point.

---

### Post by mango42 on 2009-09-18
Thank you both for your rapid responses.

Shujah, where you say: "there seems to be no reason for keeping two same Ubuntu versions" - I am in the early testing stages of running the dedicated 180.44 nVidia drivers on this SLI equiped machine (Alienware m9700) and I am consequently wary of their possible foibles. Besides, it's always useful to have a fall-back system if only to access the net and this wonderful Ubuntu resource when all else fails. ;-)

Then there's "You wont be able to expand the 2nd partition to take place of first partition as one is primary and other are on the logical/ extended areas".

Oh? If I leave 1Gb for primary, can I not expand the extended partition 'to the left' so to speak?

---

### Post by NoaHall on 2009-09-18
You don't need to add another partition for boot, it will add itself.

Yes, you could do so.

---

