---
title: "Worth to erase a disk using dd previously to format and install linux or other os ?"
date: 2011-02-18
forum: General Help
---

### Post by whitewolf573 on 2011-02-18
Sometime ago i bought a netbook , and lately i have been being for my taste a bit paranoid.I want to install centos in my pc for 3d modeling. As i don't trust to download any iso from windows, i managed to get a ubuntu disc (10.04 that i had at home) and i run the live-cd.

I installed it , installed vuze , and downloaded the iso. And used md5sum to verify the iso. Was correct, so i decided to download the nvidia drivers for my GTX 470, and the avast for linux.

Then , i don't now, why , but i did again a md5sum , it was lasting a bit (normal i think , at least now) , and i do a ctrl + c to terminate the command. Then i thought that using it could damage the iso (i don't know if it is possible that), and decided to reinstall ubuntu (and have using linux some years, and i can't evite reinstall sometimes), and download again the iso.

I boot to the 10.04 live-cd , and previously to install ubuntu, i decided to erase all data from the disk (not because security , but for reability or trust)

I did a sudo dd if=/dev/zero of=/dev/sda and now i am waiting to finish it (that late about 6 hours in my 250 GB disk to finish)

And i ask myself and why not to the forum , worth to spend 6 hours doing this to then format the disk and reinstall linux, or windows or whatever ?

dd what does is write zeroes to each bit (well , i not sure if is each bit , but writes zeroes to disk) so 6 hours after , you have a pretty big number of zeroes in your disk instead of a combination of zeroes and ones.

This could be useful to destroy the information, so not be able to retrieve it , but if you will go to install a operating sistem, for you, the os will not care have all zeroes or a aleatory mix of 1 and 0 , as won't now where is the old information , as you have formated the disk and destroyed the partition table.

If you have a virus , perhaps you can do it , but if you have problems because a failed install , update , some corrupted data (because software or human fail, not physical damage)do a format is quite similar to do a dd, but much faster no ?

Once you format the disk , is like have a clean disk , with 'nothing in it' , well have a mix of 0 and 1 , but for the OS , is  the same overwrite a 0 , or a 1 , no ? , so there is no way for the os to get influenced / corrupted or any other paranoid think.

So, it is a waste of time to do a dd previous to install a OS, to "clean" the disk, no ?

---

### Post by mikewhatever on 2011-02-18
Yes, IMO, and a really major waist of time.

---

### Post by t0p on 2011-02-18
Using dd for this purpose is a waste of time IMHO.  Use **gparted** to reformat a partition/disk if it needs reformatting.

If you need to securely delete the data from a whole partition or disk, there's an app called **[DBAN]("http://www.dban.org")** (*Darik's Boot And Nuke*[/b].  But I think what DBAN does is basically your dd command.  There's a most informative webpage on the subject [here]("http://mirror.href.com/thestarman/asm/mbr/WIPE.html"), which I suggest everyone should read.  Even if you think you have no need for privacy or security (you write all your letters on postcards or never bother to seal envelopes, and conduct all your telephone calls on loudspeaker), you might crave decent security and/or privacy in the future, when the commies take over or whatever; so it's well worth spending the time to acquaint yourself with the facts.  I think computer security is a fascinating subject.

---

