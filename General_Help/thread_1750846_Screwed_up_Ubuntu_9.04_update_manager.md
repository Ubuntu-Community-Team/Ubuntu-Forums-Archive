---
title: "Screwed up Ubuntu 9.04 update manager"
date: 2011-05-05
forum: General Help
---

### Post by perolad on 2011-05-05
I tried to use the Update Manager in 9.04 LTS and it started running, removing, preparing but not yet installing files. It said 1 hr. and 20 mins left (Dell Studio XPS with dell installed 9.04 distro.)  I got tired of waiting since it's almost midnignt so I decided to resume tomorrow.  I shut the computer down which obviously was a bad idea. When I tried to restart it, the Ubuntu screen came up, but no desktop or terminal.  Only a black screen with this message in the upper right corner: "Install Problem! The configuration defaults for GNOME power manager not installed correctly. Please contact your computer administrator."

Now what do I do?   I am the "administrator" but flying blind.  I tried to set up CMOS to boot from CDROM and popped in a CD containing the .iso copy of the orig. Ubuntu install but it didn't work.  Same black screen and Install Problem message as above.  

I should have left well enough alone!  Now what do I do to go back to where I was? Otherwise, I'm dead in the water!

Help!!!!   

Thanks,

Per

---

### Post by zvacet on 2011-05-06
I'm little bit confused about version you are running.because 9.04 in not LTS.so do yo run LTS or 9.04.I ask you this because 9.04 is not supported any more and that can be source of problem.Even if you run 8.04 LTS it is become unsupported too.I think it is best to back up all your valuable data and do fresh install of 10.10 or latest 11.04.

---

### Post by perolad on 2011-05-06
> **zvacet said:**
> I'm little bit confused about version you are running.because 9.04 in not LTS.so do yo run LTS or 9.04.I ask you this because 9.04 is not supported any more and that can be source of problem.Even if you run 8.04 LTS it is become unsupported too.I think it is best to back up all your valuable data and do fresh install of 10.10 or latest 11.04.
Sorry, I meant 10.04 LTS.   No way to back up my data since I can't access it anymore, but doesn't matter since this is a relatively new relatively new machine and nothing important lost.) Anyway, that leads me to 2 further questions since I'm new at using Ubuntu Linux: should I reinstall Ubuntu 10.04 LTS originally or update to 10.10 from an .iso downloaded from the Web? In either case, I'm not sure I know how to do that--downloading the .iso on an XP machine with NTFS file system and burning it to CD, then installing it on the ext3 -- or is it ext4 -- formatted Linux drive.  The 3Gb Dell XPS Dimension AMD machine contains what I believe is a 64 processor, to wit from spec sheet:  Processor, X4, 630, 2.8, 512X4, 4C, C3.  If it's 64 bit should I download that .iso--and what would be the advantage?  Again, don't know what to do next.  (Originally the 32-bit 10.04 bit version was installed.)

Thanks,

Per

---

### Post by zvacet on 2011-05-08
If you don´t have any files to lose maybe it is best to start with fresh install of Natty (version 11.04).Install it on same partition where 10.4 is now and format partition as ext 4 and put mount point / root.For 3GB or ram you don´t need 64 bit version.

---

### Post by perolad on 2011-05-10
> **zvacet said:**
> If you don´t have any files to lose maybe it is best to start with fresh install of Natty (version 11.04).Install it on same partition where 10.4 is now and format partition as ext 4 and put mount point / root.For 3GB or ram you don´t need 64 bit version.

Thanks for the input.  I already reinstalled 10.04 because of its LTS aspect.  I could install 32-bit 11.04 (have the .iso) but wonder if there is any reason to update a distro until the next LTS comes out, esp. since I currently have things configured to my preferences and am still using 10.04 as a learning tool--not yet a productivity OS.  Hope to migrate eventually, but more to get used to, esp. migrating my Windows XP apps and years of data intact.   Any thoughts???

---

