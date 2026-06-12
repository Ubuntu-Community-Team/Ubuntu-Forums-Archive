---
title: "Partion help"
date: 2010-02-04
forum: General Help
---

### Post by askinne2 on 2010-02-04
Hey guys. So heres my situation. I am running ubuntu only on my laptop. I have a copy of windows 7 and would like to install it as the only os on this laptop. The problem is with the partions. I have one drive (/dev/sda) that contains sda1 as an ext3 and also contains sda2 as extended which contains sda5 that is swap. I am a complete noob when it comes to this stuff. 

So first off, when I reformat to an nfts to use for windows will my ubuntu system be usable? I mean will I be able to boot up ubuntu running that sda1 drive as a nfts in case the installation of windows has a problem? Do I need to format those other two drives (sda2 and sda5) also? 

And lastly, I went ahead and tried to reformat sda1 but when I tried to unmount the drive it said that it is busy. I was doing this from the terminal because gparted said that it was unable to unmount it because "Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually." But I know that the sda2 drive is not mounted. So any ideas?

Thanks for all the help guys!

---

### Post by lotharmat on 2010-02-04
Windows install will take the whole drive if you choose the defaults

---

### Post by chewearn on 2010-02-04
> **askinne2 said:**
> Hey guys. So heres my situation. I am running ubuntu only on my laptop. I have a copy of windows 7 and [COLOR=Red]would like to install it as the only os on this laptop[/COLOR]

I highlight the line in [COLOR=Red]red[/COLOR] to confirm that you want Win7 ONLY, and to delete Ubuntu, right?

In that case, just stick the Win7 in the CDROM and start install.  There would probably be an option during the install to delete entire drive.

---

### Post by indytim on 2010-02-04
> And lastly, I went ahead and tried to reformat sda1 but when I tried to unmount the drive it said that it is busy. I was doing this from the terminal because gparted said that it was unable to unmount it because "Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually." But I know that the sda2 drive is not mounted. So any ideas?

Just as a point of illustration for other new users.  You **CANNOT** change the partition that you are mounted to with the partition editors.

-IndyTim

---

### Post by askinne2 on 2010-02-04
Yes I do want to delete ubuntu and run only windows 7 on this computer. I ran the windows 7 installation but it would not continue without the drive being an nfts....No option to delete anything.

@IndyTim - Thanks. I did not know that. How would I go about reformatting the drive then?

---

### Post by chewearn on 2010-02-04
In that case, boot into ubuntu liveCD and run Partition Editor there.  You would then be able to delete Ubuntu.


Note:
To delete the swap, you might need to select "Swap off" first.

---

### Post by askinne2 on 2010-02-04
Ok, sounds good. Thanks for all the help. Guess I need to go burn me a new ubuntu livecd.

---

### Post by urbeg on 2010-02-04
If you reformat your entire hard drive then your Ubuntu system will be over written and be completely unusable.

If you wanted to use Ubuntu and Windows 7 side by side you would have to shrink your Ubuntu partition to allow room for Windows 7 to be installed. It seems to be a good rule of practice to have Windows installed first tho.

I gather from the other replies that you only want Windows 7 so I suggest you boot up the Ubuntu Live CD and use gparted from the System > Administration menu. You should be able to unmount the swap partition by right clicking it and selecting 'Swapoff'. This will then allow you to delete it. You can now delete the main Ubuntu partition and apply all the operations leaving the hard drive as unallocated space. Now simply proceed to install Windows 7.

---

