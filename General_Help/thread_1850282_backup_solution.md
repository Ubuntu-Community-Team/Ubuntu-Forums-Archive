---
title: "backup solution"
date: 2011-09-26
forum: General Help
---

### Post by shubham1 on 2011-09-26
a want a backup software that can create a file of my full system backup
ih ave treid dej backup bup back in time lucky backup and loats more i want to upload to the cloud or to the cd

---

### Post by haqking on 2011-09-26
> **shubham1 said:**
> a want a backup software that can create a file of my full system backup
ih ave treid dej backup bup back in time lucky backup and loats more i want to upload to the cloud or to the cd

clonezilla [www.clonezilla.org](www.clonezilla.org)

.tar from command line

dd

remastersys

simplebackup

all will do as you want

---

### Post by Lars Noodén on 2011-09-26
there is also rsync 

bacula is a fancier option

---

### Post by shubham1 on 2011-09-26
> **haqking said:**
> clonezilla [www.clonezilla.org](www.clonezilla.org)

.tar from command line

dd

remastersys

simplebackup

all will do as you want
i installed backup it gives error

---

### Post by haqking on 2011-09-26
> **shubham1 said:**
> i installed backup it gives error

Well none of us can do or say much unless you tell us what type of error, what it said, when it happened.

How you set things up to be backed up etc.

And in addition as outlined above there are many options

cheers

---

### Post by liquidmonkey on 2011-09-26
> **shubham1 said:**
> a want a backup software that can create a file of my full system backup
ih ave treid dej backup bup back in time lucky backup and loats more i want to upload to the cloud or to the cd


i just started clonezilla and its easy peasy to use and has good tutorials on the net.

go for it!

---

### Post by shubham1 on 2011-09-26
> **haqking said:**
> Well none of us can do or say much unless you tell us what type of error, what it said, when it happened.

How you set things up to be backed up etc.

And in addition as outlined above there are many options

cheers
stat: cannot stat `/home/shubham/.simplebackup.conf': No such file or directory
/usr/bin/simplebackup: line 81: /home/shubham/.simplebackup.conf: No such file or directory

---

### Post by shubham1 on 2011-09-26
> **liquidmonkey said:**
> i just started clonezilla and its easy peasy to use and has good tutorials on the net.

go for it!
i am installing it is there any which also provied this feature open any file with it and it will provide the ncrypted version

---

### Post by shubham1 on 2011-09-26
> **shubham1 said:**
> i am installing it is there any which also provied this feature open any file with it and it will provide the ncrypted version
and when i give it encrypted it decrypts

---

### Post by nothingspecial on 2011-09-26
> The stability and reliability of this package is questionable. As of 6/14/2011 there were 48 open bugs and little sign of development. A second bug reporting site shows signs of development. 

From the simplebackup Ubuntu documentation.

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

---

### Post by haqking on 2011-09-26
> **shubham1 said:**
> i am installing it is there any which also provied this feature open any file with it and it will provide the ncrypted version

clonezilla is a live CD you boot to and make a clone of your system.

and i dont understand the rest of what you said

---

### Post by shubham1 on 2011-09-26
> **nothingspecial said:**
> From the simplebackup Ubuntu documentation.

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)
i am installing it to

---

### Post by nothingspecial on 2011-09-26
I was advising you to use something else.

---

### Post by shubham1 on 2011-09-26
> **nothingspecial said:**
> I was advising you to use something else.
i installed not user friednly i have a plan
of installing ubuntu 11.10 i have installed it i will reomove my current ubuntu and install it i have to prepare a live cd any backup soldution is not avaiable for linux

---

### Post by nothingspecial on 2011-09-26
You don't have to remove ubuntu, there are many backup solutions

clonezilla
remastersys
rsync

I do this

```

before="$(date +%s)"; sudo tar --same-owner -cpvzf /media/[COLOR="Red"]backup[/COLOR]/$(uname -n)_$(lsb_release -cs)_Backup_"$(date +%Y%m%d)".tgz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/tmp --exclude=/media /; after="$(date +%s)"; echo "Elapsed time: $(expr $after - $before) seconds."; echo -e "\a"
```

Change the red "backup" for the mountpoint of your external drive.

---

### Post by shubham1 on 2011-09-26
> **nothingspecial said:**
> You don't have to remove ubuntu, there are many backup solutions

clonezilla
remastersys
rsync

I do this

```

before="$(date +%s)"; sudo tar --same-owner -cpvzf /media/[COLOR="Red"]backup[/COLOR]/$(uname -n)_$(lsb_release -cs)_Backup_"$(date +%Y%m%d)".tgz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/tmp --exclude=/media /; after="$(date +%s)"; echo "Elapsed time: $(expr $after - $before) seconds."; echo -e "\a"
```

Change the red "backup" for the mountpoint of your external drive.
i am not remocing ubuntu for backup my ubuntu is corupted at the time of installing it hangs and removes my partion of windows second time wehni install it it works and removes complete windows but files wre there in a partion but it still faced a lot of problems so ii reinstalleed it using same pusb drive still it is facing same porblem ultra ultra horriblne net speed ubuntu one not workiung instipe of installing and removing it amy times software have porblems so i will install a complete new setup

---

### Post by shubham1 on 2011-09-26
> **shubham1 said:**
> i am not remocing ubuntu for backup my ubuntu is corupted at the time of installing it hangs and removes my partion of windows second time wehni install it it works and removes complete windows but files wre there in a partion but it still faced a lot of problems so ii reinstalleed it using same pusb drive still it is facing same porblem ultra ultra horriblne net speed ubuntu one not workiung instipe of installing and removing it amy times software have porblems so i will install a complete new setup
after installing beta using a cd or dvd then after can i upgrade to full vrsion using update manager beta might have bugs but not more than this.

---

### Post by shubham1 on 2011-09-27
can any body help in preparing live cd

---

### Post by shubham1 on 2011-09-28
i got its[FONT=monospace] to open system settings and file backup manager
[/FONT]

---

