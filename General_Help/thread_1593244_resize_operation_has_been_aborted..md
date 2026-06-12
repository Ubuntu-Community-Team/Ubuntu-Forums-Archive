---
title: "resize operation has been aborted."
date: 2010-10-11
forum: General Help
---

### Post by yamaha83 on 2010-10-11
trying to install 10.10 for thr first time from a cd and am new to all this. when i say to install along side windows it gives me the option to say how much space to give ubuntu and i say to give it about 90gig to make sure i have room for music and movies and such... then when it starts to partition i get an error in the middle saying "an error occurred while writing changes to the storage device. the resize operation has been aborted" what can i do to get it to work? is 90 gig to much? not enough? im really new to all this and i did some searching but couldnt find a way past my problem... i wouldnt mind doing a full install and deleting windows but i need to be able to use lightroom 3 and photoshop cs5... thanks for any help in advance!

---

### Post by Quackers on 2010-10-11
Welcome to UbuntuForums :-)
I would set up an area of unallocated space on the hard drive first, by resizing anything that is already on there, if necessary. I wouldn't recommend doing it during the install. Then during the install you can select the "largest contiguous space" for the installation.
What OS is on the drive at the moment - and does it still boot up?

---

### Post by yamaha83 on 2010-10-11
> **Quackers said:**
> Welcome to UbuntuForums :-)
I would set up an area of unallocated space on the hard drive first, by resizing anything that is already on there, if necessary. I wouldn't recommend doing it during the install. Then during the install you can select the "largest contiguous space" for the installation.
What OS is on the drive at the moment - and does it still boot up?
 
 
currently have vista on there and it still boots up. when i restart after the error it has to go through some steps to check and fix the hdd but after it boots up everything works fine. have tried a couple times and it happens every time. do you know of a ggod walkthrough showing me how to set up the unallocated space first?

---

### Post by Quackers on 2010-10-11
In Vista click on Start orb. Right-click on Computer in the start screen > select Manage. In the screen that comes up on the left side select Disk Management. A display of your hard drive(s) will appear. If there is no unallocated space at the moment, right-click on your Windows partition and select Shrink. Another window will open up asking how much to shrink. I would leave the numbers alone as it is probably the best available. Click ok and after it has run you should see some unallocated space on your hard drive.

It is a good idea to defrag your hard drive first (maybe even twice) but as the Windows defrag will take all week I would suggest something like Auslogics disk defrag (free).
If you have any problems just ask.

---

### Post by yamaha83 on 2010-10-11
> **Quackers said:**
> In Vista click on Start orb. Right-click on Computer in the start screen > select Manage. In the screen that comes up on the left side select Disk Management. A display of your hard drive(s) will appear. If there is no unallocated space at the moment, right-click on your Windows partition and select Shrink. Another window will open up asking how much to shrink. I would leave the numbers alone as it is probably the best available. Click ok and after it has run you should see some unallocated space on your hard drive.
 
It is a good idea to defrag your hard drive first (maybe even twice) but as the Windows defrag will take all week I would suggest something like Auslogics disk defrag (free).
If you have any problems just ask.
 
thanks for the fast help! ill give it a try when i go home for lunch! :guitar:

---

### Post by Quackers on 2010-10-11
Ok, Don't eat too fast, you'll get indigestion! :-)

---

### Post by oldfred on 2010-10-11
Gparted & Ubuntu do not like to touch NTFS partitions that have the chkdsk flag set or other errors. So if you are having issues booting you need to resolve those first.

Vista often has issues with resizing, but it is best to use the windows tools to resize Vista.

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)

---

### Post by yamaha83 on 2010-10-11
ok so over lunch i resized the partion through vista and got ubuntu to load and seems to be working. but when i shrunk the disk it said it was 11gig... then during install i clicked to install allongside windows, then at the bottom i clicked use entire partion. does this mean that i only have 11gig of space for things like music and stuff? if so how can i make it bigger? i know i have like 100gig or free space on my hdd... also. whenever i restarted ubuntu a couple times to driver installs it never gave me the option to boot into windows? is this because i hit restart instead of shutdown? or did i mess something up when setting up?

---

### Post by oldfred on 2010-10-11
Click on all your partitions as it only shows mounted partitions and run this:
```

df -Th
```

If all partitions are not shown, run this.

```
sudo fdisk -lu
```

---

### Post by yamaha83 on 2010-10-11
> **oldfred said:**
> Click on all your partitions as it only shows mounted partitions and run this:
```

df -Th
```
 
If all partitions are not shown, run this.
 
```
sudo fdisk -lu
```
 
thats over my head... still learing... lol
 
where do i type that in and what is it going to do?

---

### Post by oldfred on 2010-10-11
To open terminal - click on applications, accessories, terminal to open terminal window.
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Copy and paste the above into the terminal. the df command will show space used of all mounted partitions and fdisk shows all partitions (but not space used). sudo is to temporarily give root access and it will ask for your password. 

If you want more info on commands in terminal type 
man df
man fdisk
man anyothercommand
type q to exit man commands screen.

---

### Post by yamaha83 on 2010-10-11
> **oldfred said:**
> To open terminal - click on applications, accessories, terminal to open terminal window.
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Copy and paste the above into the terminal. the df command will show space used of all mounted partitions and fdisk shows all partitions (but not space used). sudo is to temporarily give root access and it will ask for your password. 

If you want more info on commands in terminal type 
man df
man fdisk
man anyothercommand
type q to exit man commands screen.

ok this is what i get... not sure how to decifer what its saying or what i need to do... 

```
yamaha83@yamaha83-HP-Pavilion-dv6700-Notebook-PC:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    221G  2.9G  207G   2% /
none      devtmpfs    1.5G  268K  1.5G   1% /dev
none         tmpfs    1.5G  208K  1.5G   1% /dev/shm
none         tmpfs    1.5G   96K  1.5G   1% /var/run
none         tmpfs    1.5G     0  1.5G   0% /var/lock
none       debugfs    221G  2.9G  207G   2% /var/lib/ureadahead/debugfs
yamaha83@yamaha83-HP-Pavilion-dv6700-Notebook-PC:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00033bbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   469968895   234983424   83  Linux
/dev/sda2       469970942   488396799     9212929    5  Extended
/dev/sda5       469970944   488396799     9212928   82  Linux swap / Solaris
```

---

### Post by yamaha83 on 2010-10-11
ok so i dont know what i did wrong or if im missing something... but i cant get windows to boot up? i turn off my comp and when i turn it back on i never get the option to load into windows? it goes straight back into Ubuntu...??

---

### Post by oldfred on 2010-10-11
You show the entire drive as Linux. One of the install choices is to use the entire drive and that looks like what you selected.

Windows is not recoverable since you have written data on the drive. You may be able to recover some data with testdisk (unlikely) or photorec (random files in areas not written to). One reason for good backups before any major system changes.

Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Foremost
[http://www.howtoforge.com/recover-deleted-files-with-foremost](http://www.howtoforge.com/recover-deleted-files-with-foremost)
[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)

---

### Post by yamaha83 on 2010-10-12
> **oldfred said:**
> You show the entire drive as Linux. One of the install choices is to use the entire drive and that looks like what you selected.

Windows is not recoverable since you have written data on the drive. You may be able to recover some data with testdisk (unlikely) or photorec (random files in areas not written to). One reason for good backups before any major system changes.

Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Foremost
[http://www.howtoforge.com/recover-deleted-files-with-foremost](http://www.howtoforge.com/recover-deleted-files-with-foremost)
[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)

well suck! i clicked install besides windows and then on the screen i selected use entire partition cuz i figured that was the option the select since i shrunk windows... oh well... live and learn... i really like what i have so far the only reason i needed windows was for photoshop cs5 and lightroom 3 and i have see where people have gotten cs5 to load i just cant seem to figure it out... guess this gives me more of an incentive! and good thing i backed up all my files to an external hdd!! 

anyone know of an easy way to get photoshop cs5 and lightroom 3 to install? i tried using wine but i get error "The file '/home/yamaha83/Desktop/Adobe1/Photoshop Lightroom 3.2/Install Lightroom 3.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

---

### Post by yamaha83 on 2010-10-12
nevermind... i think i figured it out! i had to allow the executable since i copied the .exe from my external drive!

---

