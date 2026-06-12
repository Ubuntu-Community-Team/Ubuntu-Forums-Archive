---
title: "Will installing Win 7 over-write my GRUB?"
date: 2009-10-24
forum: General Help
---

### Post by PsychedelicWonders on 2009-10-24
I'm about to install Win 7 64 over my XP Pro 32 partition.

Will Win 7 overwrite my GRUB menu?

If so, what do I need to do to set it back up properly?

Or will I be ok since I already have XP Pro on there?

Also how can I make an exact copy of my Ubuntu Partition INCLUDING all of the bells & whistles I've added to it?

---

### Post by Iowan on 2009-10-25
Windows tends to be a bit aggressive - Vista would honor XP, but installing XP after Vista caused problems. There was a How-To around here (somewhere) for installing XP after Ubuntu... The technique would *probably* be similar.

---

### Post by blwizard on 2009-10-25
Win7 will overwrite your disk MBR. So after installing it, boot your computer with your ubuntu livecd, go to the terminal, and install grub again.

basically it's like this:
? sudo grub
when your in grub, do:
> root (hd0, 5)   #if your ubuntu /boot is on /dev/sda6
> setup (hd0)
> quit

Then your good to go.

EDIT: oh you will probably have to manually add an entry in menu.lst for win7, just duplicate your xp entry and change the "root" line to the corresponding win7 partition

---

### Post by blwizard on 2009-10-25
> **PsychedelicWonders said:**
> 
Also how can I make an exact copy of my Ubuntu Partition INCLUDING all of the bells & whistles I've added to it?

If you want to make an exact copy of your whole ubuntu partition, use "dd" to dump the whole partition into a file but that will also copy unused space and the resulting file will be very big. Usually people use some other kind of backup tools, which I don't really know of. I used "tar" before it worked fine, but I think you need some special parameters for it. Just google and you will find plenty of answers.

---

### Post by diaco on 2009-10-25
and the gui soloution:
1.install win 7
2.install "easyBCD" on win 7
3.run "easyBDC" and add your ubuntu partition as an entry in the boot menu of win 7
4. now u can boot ubuntu without grub. if u want grub, load ubuntu and reinstall grub.

---

### Post by psycho5 on 2009-10-25
> **diaco said:**
> and the gui soloution:
1.install win 7
2.install "easyBCD" on win 7
3.run "easyBDC" and add your ubuntu partition as an entry in the boot menu of win 7
4. now u can boot ubuntu without grub. if u want grub, load ubuntu and reinstall grub.

That only works if your ubuntu grub is installed on the parition not the disk MBR. so instead of 

root (hd0,5)
setup (hd0) 

u should do

root (hd0,5)
setup (hd0,5)

Thats how my setup is.

---

