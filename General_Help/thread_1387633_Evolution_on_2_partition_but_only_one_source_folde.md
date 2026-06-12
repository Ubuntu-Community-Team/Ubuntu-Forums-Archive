---
title: "Evolution on 2 partition but only one source folder"
date: 2010-01-22
forum: General Help
---

### Post by longtom on 2010-01-22
Hi,

I have 2 different distros on 2 partitions.  I have Evolution on both distros and want to utilise the same .evolution folder from both distros depending which one I am using at present.

In other words, if I have something changed in evolution in distro 1 I would like to see that change and work on in distro 2 and vice versa, because they work from the same /home partition. Possible?  If yes, how.

Any suggestions welcome.

---

### Post by erlguta on 2010-01-22
mmm, maybe it is possible, but yo can break something if the different distros have different version of evolution and operates in different mode. Yo can locate which folder of evolution want to share (/usr/share/evolution/2.28 and you $HOME .evolution) and put it in one own partition.
But i think is not a good idea

---

### Post by pmlxuser on 2010-01-22
if i wanted to share the actual data, then i would just place a symbolic link in one distro pointing to the folders in the other distro

---

### Post by longtom on 2010-01-22
> **pmlxuser said:**
> if i wanted to share the actual data, then i would just place a symbolic link in one distro pointing to the folders in the other distro

I am with you.  However - I want to use evolution in both distro from the same .evolution directory.  
Like editing a odt file with OpenOffice from distro 1 or distro 2.  Doesn't make a difference to OO or the distros, but the data is changed.

---

### Post by longtom on 2010-01-23
I got it right on Thunderbird.  
You can choose were you want your storage folder to be for every account.  
However - there is one account I would like to be in evolution.  Is there a way I can change my storage folder in evolution?

---

### Post by rafalr on 2011-01-18
Did you sort it out in the meantime ? Got stuck too ...

---

### Post by Dokuganryu07 on 2011-01-18
you could maybe try saving the data that needs to be shared on a small 3rd partition that is formatted in a way that both distros can read and write to it, FAT32 maybe, or EXT3?

Just a thought, not sure if it would work.

---

