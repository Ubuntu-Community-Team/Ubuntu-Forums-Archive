---
title: "vista takes up too much space"
date: 2010-02-15
forum: General Help
---

### Post by volatilepyro on 2010-02-15
So I have a dual boot system using ubuntu, 7, and vista. I want to get rid of vista. I already tried to use my recovery discs but they never give me an option as per what to partition and what not to, and it comes with vista and seven. I really need the space and can't currently afford a portable hard drive. any help would be appreciated.

---

### Post by saif_held on 2010-02-15
Can't you just format the vista drive?

---

### Post by Raiju on 2010-02-15
if you do that, and vista was installed first you might have to reinstall grub. i remember having to do it with a vista/xp/linux boot

---

### Post by Techsnap on 2010-02-15
A fresh install of Vista or an older install of Vista? If you're never going to use it, disable System Restore, on an older system this can give you back a bit of space.

---

### Post by saif_held on 2010-02-15
I once did install vista 1st then Ubuntu, then simply formatted vista's drive and nothing went wrong..

---

### Post by Raiju on 2010-02-15
note how i said "might"^^

---

### Post by saif_held on 2010-02-15
I did notice it, I just wanted to clarify any misunderstanding. No hard feelings :)

---

### Post by oldfred on 2010-02-15
Your title says wubi. Do you have wubi inside Vista? If you delete Vista it will delete wubi.

A system restore from the PC vendor typically just totally reformats your entire hard drive and makes it just as you purchased it. Restores to like new but loses all you changes.

If you have installed two windows you have a combined boot and will have to repair the windows remaining.

[http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by volatilepyro on 2010-02-16
Sorry about the title. I guess I had a misunderstanding as to what wubi meant. I cannot simply format a harddrive because it's on a laptop and they're both on the same hard drive. Also I use seven from time to time. Mostly just when I'm having a problem with ubuntu or to play video games. Also, is there anyway to change the prefix to avoid further confusion???

---

### Post by Mark Phelps on 2010-02-16
Also, if you installed Win7 after Vista (and it sounds like you did), Win7 almost certainly wrote its boot loader files to the Vista partition.  IF you blindly follow the advice of others here and wipe Vista, you will wipe out the Win7 boot loader files -- and will not be able to boot into Win7.

Before you do anything else, if your machine has a CD burner, get a blank CD and use the Win7 backup feature to create and burn a Win7 Repair CD.  You will need that to restore boot capability if you remove Vista.

---

### Post by Jackzor on 2010-02-16
If he is using grub then removing vista wouldn't harm anything? Am I missing something? If he has Ubuntu installed(not wubi) then he uses grub as the bootloader and it has nothing to do with vista's mbr? Right?

---

### Post by oldfred on 2010-02-16
As Mark Phelps said the Win7 boots thru the Vista partition. Grub probaly boots windows by booting vista and Vista boot gives a choice of Vista or 7.

Move boot flag to the win7 partition & Use Win7 repair disk to fixboot on the Win7 partition and update grub to see if you can directly boot 7, then you can reformat the Vista partition.

 You can use gparted to set boot flag or 
set boot flag on for sda1 (off on others)
sudo sfdisk -A1 /dev/sda

If grub2 
sudo update-grub

If grub legacy you will have to modify menu.lst.

---

### Post by volatilepyro on 2010-02-17
Well a small problem has occurred. Grub screwed up for the umpteenth time recently so I wiped 7 and vista off the hard drive for the time being. I do intend to put 7 back on though. However while I had them on here it gave me the option to boot vista or 7 straight from the grub menu. I think I may try to put 7 back on and burn a new recovery disc from 7 and wipe the hard drive again and try to simply reinstall 7 and hope it doesn't keep vista. As it stands I use the recovery discs that I got with the laptop. Would burning a new disc with just 7 take out all the firm/software for the laptop as well or would that be imported with the operating system???

---

