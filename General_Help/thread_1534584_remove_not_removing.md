---
title: "remove not removing???"
date: 2010-07-19
forum: General Help
---

### Post by choochoousmc on 2010-07-19
trying to find MP3 player I like.
Been installing and then removing via Ubuntu software center in UBUNTU 10.04. different ones. Can't find one I like.
I don't want to import all the files. Just want to open a location.
play, create / delete playlists and edit the tags all in one.

Now Ubuntu reporting no disk space left.
Openoffice has crashed all my files. Thankfully they are actually saved on a different partition.
Says I need to make more space available in
/home/choochoo/.openoffice.org/user/backups    (at least I think that is what it said)
also I use truecrypt on another partition, it's reporting no space left either.
Thunderbird locked up and would not respond or close down. Had to reboot.

Using file / disk browser, no such address exists.  How do I clean up the unnneeded
apparently unremoved bits and pieces. Disk janitor is not doing it.
Also now a notification area does not exist in main menu bar and a part of another section is not showing.
It's almost like a virus, but I haven't done anything to have gotten one yet.
Is there a software I can use that will let me clean up all  the  unneeded file remnants etc. Without being forced to reinstall UBUNTU?

---

### Post by dv3500ea on 2010-07-19
Try going to Applications -> Accessories -> Terminal
Enter:
```
sudo apt-get autoremove
```

---

### Post by choochoousmc on 2010-07-19
> **dv3500ea said:**
> Try going to Applications -> Accessories -> Terminal
Enter:
```
sudo apt-get autoremove
```


Okay, thanks I done that.  This is what it reported.

choochoo@choochoo-acer:~$ sudo apt-get autoremove
[sudo] password for choochoo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
choochoo@choochoo-acer:~$ 

But I still get a popup warning saying less than 1.2 gig space remaining on drive.
I set Ubuntu partition at 20.1 gig.  Only two external  programs have been added
limewire, truecrypt  and internal via Ubuntu center  pan, firefox and thunderbird.

ALL my data and truecrypt volumes are stored on another partition.

as above. I was using Ubuntu software center to install various mediaplayers trying to find one I liked. Installed, tried it and then removed it.
That's when the problem started.
Thunderbird crashed. Had to reboot.
Noticed my notification area has changed, items are missing.

Any other ideas?

Still need a media player as above   play, organize, create / delete playlists and edit tags.
thanks

---

### Post by dv3500ea on 2010-07-19
Can you right-click on /home and click properties to find out how much space your home folder is taking up? I'm assuming /home is on the same partition as /. It may be your files that are taking up the extra space - I've installed tons of programs which take up < 8GB space.

---

### Post by choochoousmc on 2010-07-19
> **dv3500ea said:**
> Can you right-click on /home and click properties to find out how much space your home folder is taking up? I'm assuming /home is on the same partition as /. It may be your files that are taking up the extra space - I've installed tons of programs which take up < 8GB space.

I clicked places, then right clicked home. Browser window opened showing all the default folders I have not added any folders or data to the Ubuntu partition).
During install I set it at  20.1 gig   it now reports 55 mb

actually the home folder is labeled as choo choo

---

### Post by dv3500ea on 2010-07-19
> **choochoousmc said:**
> I clicked places, then right clicked home. Browser window opened showing all the default folders I have not added any folders or data to the Ubuntu partition).
During install I set it at  20.1 gig   it now reports 55 mb

actually the home folder is labeled as choo choo

Sorry, I meant in the file browser right click on your home folder and click properties.

---

### Post by choochoousmc on 2010-07-19
> **dv3500ea said:**
> Sorry, I meant in the file browser right click on your home folder and click properties.

Ok,  I went to places, homefolder and opened it. as I said it is called choo choo when opened.
it has thirteen folder and one document in it.
desktop, documents, downloads, incomplete, limewire, music, pictures, podcasts, public, templates, ubuntu one, videos, templates
troubleshoot.txt.

Now lime wire I added when I downloaded and installed it. It then added the incomplete folder.
Under downloads is a folder truecrypt I added when I downloaded and installed it.

I did find a few files under limewire but less than a gig.
If UBUNTU uses about 7 or 8 gig and limewire and truecrypt use about 1 gig or so each
I should have around 10 gig left, not the 55 mb reported which is now upto about 600 mb, after the cleanup.

So is there somewhere else I can look or is there a good program I can use to search for any left over remnants?

thanks

---

### Post by oldos2er on 2010-07-19
Can you run these two commands and post the output here? ```
sudo fdisk -l
df -h
```

---

### Post by choochoousmc on 2010-07-19
> **oldos2er said:**
> Can you run these two commands and post the output here? ```
sudo fdisk -l
df -h
```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008169b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26217056   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda4            6529       18662    97466355    7  HPFS/NTFS
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris

Partition table entries are not in disk order

Partition table entries are not in disk order
choochoo@choochoo-acer:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              25G   19G  5.4G  78% /
none                  1.4G  268K  1.4G   1% /dev
none                  1.4G  468K  1.4G   1% /dev/shm
none                  1.4G  196K  1.4G   1% /var/run
none                  1.4G     0  1.4G   0% /var/lock
none                  1.4G     0  1.4G   0% /lib/init/rw
/home/choochoo/.Private
                       25G   19G  5.4G  78% /home/choochoo
/dev/sda4              93G   30G   64G  32% /media/DATA
choochoo@choochoo-acer:~$ 

Ok I did that.
I will have to check the file sizes of Lime wire and truecrypt, but I don't think they are 10 gig combined. because Ubuntu needs about 7 or 8 gig. and it says I have 25 and used about 19.

---

### Post by dv3500ea on 2010-07-20
It could be the files in your home folder that are taking up all the space. Likely culprits are ~/Music ~/Videos ~/.cache ~/Pictures ~/Downloads
Also, I'm not sure about ~/.Private
Run Accessories -> Disk usage Analyser
Click Analyser -> Scan Home Folder

---

### Post by oldos2er on 2010-07-20
There are some ideas for recovering hard disk space here: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by choochoousmc on 2010-07-25
> **oldos2er said:**
> There are some ideas for recovering hard disk space here: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

thanks for the help Ann.
I will run the link you sent.
I keep ALL my data on a separate partition.
I did eventually get back about 2 gig.

---

