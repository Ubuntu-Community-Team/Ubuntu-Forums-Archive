---
title: "system wont boot anymore"
date: 2012-08-24
forum: General Help
---

### Post by MADDSNIPER on 2012-08-24
ok first off im completely new to ubuntu/linux but i finally managed to get lubuntu 12.04 installed along side windows xp. (seperate partition)

after install the update manager popped up and wanted to do all the various updates which it was in the middle of doing when i decided to have a bit of a lookey about. i opened the file manager and was trying to click on the other partitions but it kept coming up access denied (for a little bit previously i had ubuntu 12.04 installed through lubu and i was able to view the other partitions ok including the one windows xp was installed on) anyway it seems my mad clicking made the operating system crash in the middle of updating itself, i tried to do various things after the crash but hardly anything was working including the power button to reset the pc so i did a hard reset.

upon rebooting im greated with "disc boot failure insert system disc and press enter" i tried to boot with the windows xp disc so that i could just delete the lubuntu partition and start again but it wouldnt let me get that far. i was able to boot with the lubuntu live cd though and get access to a command prompt where i tried out the following that was advised to someone else in a similar situation when i googled searched the problem.

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair


at the end of running this it said "no os detected" and gimmie this link to post: [http://paste.ubuntu.com/1164689/](http://paste.ubuntu.com/1164689/)


oh also i was able to use ultimate boot cd and then run partition magic from which i tried to run gparted i think its called but it was unable to detect any drives at all :/

any ideas?

---

### Post by oldfred on 2012-08-24
Welcome to forums.

Hard shut down is one of the worst things to do, if anything is/was running system will be corrupted. Best to remember the elephants.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

I have not seen a boot info report with no hard drive at all. Does BIOS still see a drive?

If BIOS sees drive, see what testdisk shows.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by MADDSNIPER on 2012-08-24
thanks, i will try this tomorrow as it means dismantling this pc to get the other one connected up, ill report back if it works or not.

---

### Post by MADDSNIPER on 2012-08-25
ok testdisk worked (mostly)  it found all the right partitions and no old ones, so i used it to write new code to the MBR and i restarted the pc. It booted straight into win xp with no option to pick OS, in Win XP i deleted the ubuntu partitions and got ready to start again....

let me try to explain my setup, i have one 750gb harddrive, i had it made into 3 partitions: the first one around around 350gb (this became c:\ and the system partition when i was installing windows, i wanted to use it for mp3s, videos etc that i could share between lubuntu and win xp)

the other 2 partitions were around 170gb each, i installed winxp on one (this became f:\ and the boot partition somehow when i installed win xp)

and i intended to install lubuntu on the last partition also around 170gb.

Now when i picked the install option "install lubuntu along side windows xp" it wanted to install it on my 350gb partition. i wanted it on the smaller one so i went into the custom options on the lubuntu install cd abd had a look how to partition it for this. (i dont really understand this part) it seemed the 350gb partition was called sda1, windows xp was on sda2 and i wanted to get lubuntu on sda3 but it kept saying "no root file system is defined" i kept trying to figure it out but couldnt so eventually i gave up and just let it install its self on the 350gb partition and i rebooted after install....

after reboot it came straight into windows xp again :/ seems my grub2 bootloader isnt kicking in right after what i did with testdisk? i read solutions on how to fix this but all seemed quite involved and as i cant have both my pcs running at once i would have had to start writing all the instructions down as i dont think i would have remembered them sadly.

all this being said i thought it would be easier to just install lubuntu again on one 750gb partition forgetting about windows etc for the time being (i probably wont even keep lubuntu look anyway, its ubuntu studio i really wanna look at but im still learning linux so its all good)

lubuntu is running great now, slowly picking it up. thanks for the help. any thoughts on how i should do things different next time for dual booting win xp and linux? was it a bad thing the way when i originally installed xp it made my 350gb partition c:\ and the system partition? when all i wanted the 350gb partition for was a dump for media files shared between operating systems?

---

### Post by black veils on 2012-08-25
should have been:

windows system
data partition
leave the space as unallocated for linux

you make windows the desired size with windows tools. create your second partition. then for ubuntu based systems, you can use the wizard method to just install alongside windows.

the install alongside option will automatically create 2 partitions. one is the root partition (your system), in ext4 format, mounted as /  .  the other is swap, which has the format of swap, no mount point, this is for your page filing, it needs to be about the size of your ram or more, depending on if you use hibernate or not. if you dont use hibernate, it depends on your ram size, as to what size the swap should be. the boot loader, grub, gets installed on sda, which is the beginning of your hard drive, not a main partition.

---

### Post by oldfred on 2012-08-25
Windows installs to a primary partition formatted NTFS with the boot flag. So it may have been the boot flag?

I do normally suggest smaller system partitions and larger shared data partitions like your original goal.

---

### Post by MADDSNIPER on 2012-08-25
when using the 'install along side' option a little slider appeared letting me pick the size of the 2 partitions (i left it in the middle) is this determining the size of the root partition and the swap file? (im thinking not because both were around 80gb each and i noticed in testdisk that one( maybe 2 ) partitions had been created around 4gb each (size of my ram)

if the slider isnt for that, what is it for?


also any idea why in my original install of lubuntu it kept saying access denied when trying to click on any of the other none linux partitions in file manager? seemed ok in ubuntu 12.04 installed through lubu.

---

### Post by black veils on 2012-08-25
the alongside slider is to choose you windows system and lubuntu system+swap size. if the slider had been more to the right, your windows would have bigger (on the left) and lubuntu would have been smaller (on the right).

i do not know the answer to your last question.

---

### Post by MADDSNIPER on 2012-08-25
ok no worries well thanks for the help guys.

mods can you mark the thread as solved as original problem is sorted now, thanks.

---

### Post by black veils on 2012-08-25
you can mark it as solved by going to the top of the thread, to **thread tools**, and choosing the option from drop-down menu

---

