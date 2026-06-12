---
title: "Reformat windows drive as a secondary Ubuntu drive."
date: 2006-04-22
forum: General Help
---

### Post by Trajan on 2006-04-22
I was weeding thru all the posts over this subject but none covered or said anything about what I wanted to do.
Basically what I want to do is switch my dual booting system into a full Ubuntu system. But now my issue is the following:

How can I go about reformating the windows xp drive (wipe it clean + drive is /dev/hda ) and add it as a secondary ubuntu drive to the main Ubuntu drive that is already being used (/dev/hdb1) without modifying the main ubuntu drive.(2nd drive to be used only for dumping miscellaneous junk,data & or svn usage per se.)
Any suggestions are welcomed.

---

### Post by aysiu on 2006-04-22
This is actually a lot easier than you'd think.

In Ubuntu, unmount your Windows drive. I'm guessing it's only one partition on that drive--is that correct? If so, go to Applications > Accessories > Terminal and copy and paste this command: ```
sudo umount /dev/hda1
```

Then, install GParted to reformat the Windows drive: ```
sudo apt-get update
sudo apt-get install gparted ntfsprogs
sudo gparted
```

Delete the Windows drive and then reformat it as Ext3

```
sudo mkdir /storage
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` If there's already a line referring to /dev/hda1, delete it. Then add this line ```
/dev/hda1 /storage ext3 defaults 0 0
```

Finally ```
sudo mount -a
sudo chown -R trajan:trajan /storage
sudo chmod -R 775 /storage
```

**Edit**: All this assumes that Ubuntu's Grub is installed to the MBR. If Windows is in charge of the Master Boot Record, then the procedure's a little more complicated.

---

### Post by Trajan on 2006-04-22
Wonderful ! Thanks for the help aysiu.

---

### Post by aysiu on 2006-04-22
[QUOTE=Trajan]Wonderful ! Thanks for the help aysiu.[/QUOTE] Say that *after* it works.

Well, report back anyway--whether you run into problems or you run into no problems at all.

---

### Post by Trajan on 2006-04-22
Actually I meant to say Wonderful ! It worked flawlessly. One question though, how can I actually make it mount to the desktop as a hard drive icon  ? Like I actually had my Windows Drive before ? If theres not a convenient way then don't stress it, as long as the hard drive is working as my new backup I'm happy.

Oh yes one more thing I was going to ask, how can I configure my folders to show their size (text next or under the folder). I have it like that with my mac. Is this possible on ubuntu also  w/out any gdesklets. Just native.

---

### Post by aysiu on 2006-04-22
[QUOTE=Trajan]Actually I meant to say Wonderful ! It worked flawlessly.[/quote] Oh, good. > One question though, how can I actually make it mount to the desktop as a hard drive icon  ? Like I actually had my Windows Drive before ? If theres not a convenient way then don't stress it, as long as the hard drive is working as my new backup I'm happy. If you did mount it at /storage, open up Nautilus and navigate to /

Then select the /storage folder and middle-click-drag it to the desktop and select "link here."

> 
Oh yes one more thing I was going to ask, how can I configure my folders to show their size (text next or under the folder). I have it like that with my mac. Is this possible on ubuntu also  w/out any gdesklets. Just native. No idea.

---

### Post by Face1 on 2006-04-22
You can create a custom launcher on your desktop that runs the command ```
nautilus /storage
``` (Replace /storage with the drive's mount point.  Double clicking (or whatever) this launcher will open nautilus to the folder.  I think that is what you wanted.

As for your second question, in nautilus, click on **edit -> preferences** and click on the "display" tab.  Change the first box to size, and then use whichever zoom level will show what you want (just experiment)

---

### Post by Trajan on 2006-04-22
Face1 you're brilliant !

---

### Post by Ramses de Norre on 2006-04-22
Or you can mount it under /media (/media/storage for example) and nautilus will set an icon on your desktop and places menu itself.

---

### Post by smurphv2 on 2007-03-21
In the first reply it is stated: 

> **aysiu said:**
> 
I'm guessing it's only one partition on that drive--is that correct? 

Will this work the same way if there are many partitions on the drive? Really all you're doing is handling the partition right?

---

