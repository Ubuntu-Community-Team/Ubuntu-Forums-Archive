---
title: "If I copy my HP_TOOLS partition, delete it, and then recreate it as an extended..."
date: 2011-02-05
forum: General Help
---

### Post by sirspazzolot on 2011-02-05
Will it still work? All four primary spots are taken. Ideally, I can shrink my C:, remake HP_TOOLS as an extended partition, and install Ubuntu in the extended, and still have HP_TOOLS be accessible. Does anyone know if it'll work? Or will my computer stop working if I delete HP_TOOLS?

---

### Post by dcstar on 2011-02-05
> **sirspazzolot said:**
> Will it still work? All four primary spots are taken. Ideally, I can shrink my C:, remake HP_TOOLS as an extended partition, and install Ubuntu in the extended, and still have HP_TOOLS be accessible. Does anyone know if it'll work? Or will my computer stop working if I delete HP_TOOLS?

Chances are you won't be able to use the HP Recovery boot option.

---

### Post by Mark124 on 2011-02-15
I just installed Ubuntu on an HP like this.  I tried to move HP_TOOLS partition to the extended partition I created but GParted doesn't allow FAT32 partitions in extended partitions.  I take that to mean FAT32 can only exist as a primary.  According to this doc:

[http://h20000.www2.hp.com/bc/docs/support/SupportManual/c01564727/c01564727.pdf?jumpid=reg_R1002_USEN](http://h20000.www2.hp.com/bc/docs/support/SupportManual/c01564727/c01564727.pdf?jumpid=reg_R1002_USEN)

the partition needs to be FAT32 so I gave up on trying to preserve HP_TOOLS but I copied the contents to the windows 7 directory and it can always be restored if it needs to.

Anyhow I just killed that partition and everything is working fine so far both windows and Ubuntu are working.  Haven't attempted any HP diagnostics or windows recovery.

---

### Post by PaulReaver on 2011-02-15
> **sirspazzolot said:**
> Will it still work? All four primary spots are taken. Ideally, I can shrink my C:, remake HP_TOOLS as an extended partition, and install Ubuntu in the extended, and still have HP_TOOLS be accessible. Does anyone know if it'll work? Or will my computer stop working if I delete HP_TOOLS?

NO. the recovery partition has to be in the same place for it to work. also you probably need the mbr to boot the recovery partition.  Your computer will still "work" but your windows would be unrecoverable.

unless you dumped HP_TOOLS and the mbr to files???... you could restore them later when needed


> **Mark124 said:**
> 
Anyhow I just killed that partition and everything is working fine so far both windows and Ubuntu are working.  Haven't attempted any HP diagnostics or windows recovery.


should've used dd to dump the partition to a file

first backup the master boot record... this dumps the mbr to a file called mbr.backup in my /home

$ dd if=/dev/sda of=/home/paul/mbr.backup bs=512 count=1


then backup the recovery partition... this dumps the recovery partition to a file called HP_TOOLS.backup in my /home

dd if=/dev/sda1 of=/home/paul/HP_TOOLS.backup




you can then use dd to restore them later

the above commands are posted for educational purposes only.. they are examples.... research the above before using on your own machine....test them on a virtual machine first..... they can seriously hose your machine if used incorrectly... which is why I left out sudo above. I will not be blamed for people wrecklessly cutting and pasting into the terminal...

---

### Post by srs5694 on 2011-02-16
> **PaulReaver said:**
> NO. the recovery partition has to be in the same place for it to work. also you probably need the mbr to boot the recovery partition.  Your computer will still "work" but your windows would be unrecoverable.

Unless I'm very much mistaken (which I might be; I don't own any HP computers), the HP_TOOLS partition is *not* the same as the Windows recovery partition. My understanding is that the HP_TOOLS partition contains HP-specific software provided with HP computers. If so, converting the partition to a logical partition will not cause problems with recovery; at worst, the software on the partition will not work or install correctly (although probably it would).

I must reiterate that I don't have such a computer and so my response is speculative. I recommend that the OP take advice on this issue from somebody who has an HP computer with such a partition and who's made the suggested adjustment.

One more point: Most modern (Windows 7) computers have another partition that holds the Windows installation media. This partition takes the place of the installation disc(s) that have been provided with computers in the past. Typically, it's about 10 or 20 GiB in size. There's normally a Windows utility that copies the contents of this partition to DVDs. Once this is done, that partition can be deleted with no negative consequences; you'll just have to use the DVDs to restore the system, should Windows become so damaged that this becomes necessary. You could do this instead of adjusting the HP_TOOLS partition. I recommend writing a letter to HP (with a cc: to Microsoft) expressing displeasure at their cheapness in not providing proper recovery media while you play human disc changer when making the backups, too; they'll keep cutting corners like this so long as people don't complain.

---

### Post by Mark124 on 2011-02-17
PaulReaver, if you have a look at the link I posted there are instructions in that HP document on how to create the HP_TOOLS partition from scratch.  The bios isn't that picky it's just looking for a FAT32 partition labeled HP_TOOLS where it can find it's .efi programs that's all.  The contents of that partition to the best of my knowledge are mainly extended diagnostic programs probably launched from some part of the bios.  Here are some of the efi programs in that folder:  CryptRSA.efi SystemDiags.efi VideoMem32.efi.  So no real harm in just backing up the file contents on that folder to disk in case it needs to be restored later.  As I mentioned I have ubuntu and windows 7 working just fine on this machine.

To clarify HP_TOOLS has nothing to do with windows recovery.  I just did some actual verification for you guys.  The machine I'm working with here is an HP dv4-2045dx.  I tried F11 to go into recovery, HP bios prints a short message F11 recovery and then it goes into grub boot menu.  So it seems grub has killed the out of the box behavior however it identifies all bootable partitions.  Here are the windows partitions that it lists:

Windows 7 (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)
Windows Vista (loader) (on /dev/sda3)

the first one (sda1) boots windows 7.  The second one (sda2) is dead, it loads some type of win code and then gives you option to boot to ram disk.  Last option (sda3) takes you to the recovery disk, for obvious reasons I didn't go any farther with recovery :p but I think it proves that recovery functionality is preserved.

---

### Post by PaulReaver on 2011-02-19
Whoa whoa guys calm... I meant no offence....  

Your HP must be completely different from brothers.
HP_TOOLS on my bro's 6735s is a five gig partition that contains the vista recovery media???

It's another option for backup up partitions.... thats all.. not an order...ok? we cool?

---

### Post by Mark124 on 2011-02-20
No offense taken on my part whatsoever I hope it didn't come across that way.  Just trying to provide solid information for people contemplating the linux jump on their HP laptops. 

While doing this install I couldn't help think if maxing the partitions was some kinda microcrap move to prevent people from installing other operating systems.

---

