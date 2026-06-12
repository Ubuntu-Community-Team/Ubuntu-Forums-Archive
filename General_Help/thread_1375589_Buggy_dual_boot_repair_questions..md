---
title: "Buggy dual boot repair questions."
date: 2010-01-08
forum: General Help
---

### Post by PyrexKidd on 2010-01-08
ok so hardware details

MSI K7N2DeltaLSU + AMD Sempron2800+

Maxtor 40gb HDD (Master)
WDC 149.9gb HDD (Slave) 

MSI vVIDIA GeForce Fx520-TD64 (which i can't for the life of me figure out how to get working)

Trying to run Ubuntu (Karmic Koala) and Windows XP SP1 (and upgrade to SP3 thru updates)

Now the thought is to use the smaller drive to install the two OS's and use the bigger drive to store all of the files, media etc. 

Initially I ran DBAN so i could start fresh.

I while installing XP, I formatted 2 partitions on the HDD, the XP side NTFS, and i left the other half unformatted.

when I installed Ubuntu I somehow ended up with three separate partitions, I'm sure it's the slider in the Ubuntu install.  

So several reasons I decided to wipe the drive and start fresh.  Ran DBAN again and it loaded and immediately quit.
When I tried to reinstall windows it loaded and then had a fatal error, something about the boot sector (yes shoulda written it down...)  
IF_NO_AND_THEN 

something about the boot sector

and then it gave a hex address.

Then i unpluged my WDC (slave) and take the Maxtors jumper out I can Run DBAN and it doesn't quit out.  When I tried to run DBAN again after replacing the jumper to make the maxtor the master again DBAN returned a fatal error which immediately was replaced by a DBAN ran successfully with no fatal errors message.

does Grub have anything to do with my problems?  Can i successfully install windows after Ubuntu?  what is the deal with Grub affecting DBAN?

thanks for the help in advance.

---

### Post by zvacet on 2010-01-08
>  Can i successfully install windows after Ubuntu?

Yes,but you will have to [reinstall grub.]("https://help.ubuntu.com/community/Grub2") After installing ubuntu you ended up with 3 partitions,because ubuntu created root and swap partition.Nothing wrong with it.

---

