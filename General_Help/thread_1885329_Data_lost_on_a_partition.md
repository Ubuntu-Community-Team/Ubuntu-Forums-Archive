---
title: "Data lost on a partition"
date: 2011-11-23
forum: General Help
---

### Post by aryangor on 2011-11-23
Hey!

I have had two Windows partitions. One was system, the other one had data. When I tried to install Ubuntu 11.10 on the data partition, it changed the partition settings and now the data is not accessible. I never finished the installation of Ubuntu or formatted the data partition.

Also the Windows system partition is 100% fine and I can boot Windows, even through I cannot access the lost files. 

I tried to use TestDisk to recover the partition and the data but I could not get it right.

Any help would be appreciated, as the data is quite important. Thanks!

---

### Post by WSmart on 2011-11-23
Greetings,

What information do you get from gparted?   I guess you ran testdisk from the liveCD?

Bill

Edit:  Would be a good idea to back everything up before you start working on it.  Have you tried checking the disk, chkdsk, from your old OS?

Edit: Partimage is an easy linux program that can make an image of the partitions.

---

### Post by WasMeHere on 2011-11-23
Hi aryangor,

I agree with WSmart. Start doing what he suggests :-)

Then I would add that you can try a couple of other tools,
***gpart*** and ***photorec***. Browse for them on the internet and read tutorials and other help texts about them!

Gpart can guess (in an intelligent way) what a destroyed partition table should be. Try that next!

If no luck you can always resort to photorec. It started as a tool to recover picture files from flash cards. Now it is a general tool to recover most kinds of files. It works as long as the file data are still there (011000100111...) by looking for file headers. It does not need a partition table, but it helps to know what file system it was (I guess NTFS in your case). Photorec cannot restore the file names or the directory structure, so you'll have a lot of organizing work to do ... but all data that are not overwritten can be recovered.

*Edit: In any case, you need another drive to put your recovered data*

Good luck
Olle

---

### Post by aryangor on 2011-11-23
Thanks, WSmart, I will do so!

---

### Post by aryangor on 2011-11-23
> **Olle Wiklund said:**
> Hi aryangor,

I agree with WSmart. Start doing what he suggests :-)

Then I would add that you can try a couple of other tools,
***gpart*** and ***photorec***. Browse for them on the internet and read tutorials and other help texts about them!

Gpart can guess (in an intelligent way) what a destroyed partition table should be. Try that next!

If no luck you can always resort to photorec. It started as a tool to recover picture files from flash cards. Now it is a general tool to recover most kinds of files. It works as long as the file data are still there (011000100111...) by looking for file headers. It does not need a partition table, but it helps to know what file system it was (I guess NTFS in your case). Photorec cannot restore the file names or the directory structure, so you'll have a lot of organizing work to do ... but all data that are not overwritten can be recovered.

*Edit: In any case, you need another drive to put your recovered data*

Good luck
Olle

Thanks Olle! I know this was a wrong thing to do and now I am enjoying the fruits of that decision! :( Thanks a lot for suggesting the softwares! I was about to use Photorec, but will look into other ways to avoid the organizing first! Cheers!

---

### Post by Mark Phelps on 2011-11-23
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by oldtimer7777 on 2011-11-23
For data recovery I use this for free:

[https://debianhelp.wordpress.com/2011/07/05/how-to-use-photorec-for-data-recovery-in-ubuntu-linux/](https://debianhelp.wordpress.com/2011/07/05/how-to-use-photorec-for-data-recovery-in-ubuntu-linux/)

> **aryangor said:**
> Hey!

I have had two Windows partitions. One was system, the other one had data. When I tried to install Ubuntu 11.10 on the data partition, it changed the partition settings and now the data is not accessible. I never finished the installation of Ubuntu or formatted the data partition.

Also the Windows system partition is 100% fine and I can boot Windows, even through I cannot access the lost files. 

I tried to use TestDisk to recover the partition and the data but I could not get it right.

Any help would be appreciated, as the data is quite important. Thanks!

---

### Post by drdos2006 on 2011-11-23
If you tried to install the Ubuntu OS onto the data partition, Ubuntu would have formatted to ext3 or ext4 file system. 
It may be that the hard drive partition table has been altered. 
Can you run the Ubuntu Live CD and access your data partition ? 
If so then you may be able to rescue your data.

regards

---

