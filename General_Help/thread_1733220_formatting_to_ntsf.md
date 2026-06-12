---
title: "formatting to ntsf"
date: 2011-04-19
forum: General Help
---

### Post by azed on 2011-04-19
Hey guys, one post wonder here
so heres what happened.
A month or so back i was trying to get a hardrive to be detected since i have had success getting them to work with a ubuntu cd, in my overtired state and the portable harddrive not working i thought maybe completely installing Ubuntu would make it work (it did not)
now the computer i was using i didn't use often, but now i want to use it.

Today I got windows 7 and tried to install it, got it to boot up but I am unable to install it, i get the following message

'Windows cannot be installed to this hard disk space. WIndows must be installed to a partion formatted as NTFS

WIndows cannot be installed to this hard disk space. The partion is of an unrecognized type.'

I also tried to install windows xp, but no cigar.

So what is the best way to reformat to NTSF?

---

### Post by matt_symes on 2011-04-19
Hi

Boot into the Ubuntu LiveCD and start up GParted. You can format the partition that way using a nice user interface. 

Make sure you unmount any swap partitions then you will be able to create a new partition table.

Create at least one primary partition for windows and set it as bootable.

Kind regards

---

### Post by Mark Phelps on 2011-04-19
> **azed said:**
> So what is the best way to reformat to NTSF?

For an installation of Windows 7 -- NOT.

Leave the space unformatted and let Windows 7 format it as part of the installation.

---

