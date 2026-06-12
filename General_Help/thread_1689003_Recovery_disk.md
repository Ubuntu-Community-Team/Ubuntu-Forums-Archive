---
title: "Recovery disk"
date: 2011-02-16
forum: General Help
---

### Post by Steve Moss on 2011-02-16
Hi

How can I protect against, for instance a hard drive failure, or corrupt OS so that I can't boot into Ubuntu

Can I create a recovery disk that will load up all my settings, installed software etc or is there some other method to do this

My apologies if this has been covered elsewhere

---

### Post by anglican on 2011-02-16
> **Steve Moss said:**
> Hi

How can I protect against, for instance a hard drive failure, or corrupt OS so that I can't boot into Ubuntu

Can I create a recovery disk that will load up all my settings, installed software etc or is there some other method to do this

My apologies if this has been covered elsewhereThere are many ways to do this, I use a program called "mondoarchive" (it's in the repos) for this. I backup everything apart from my /home (which are too large) directories to a single DVD. I use rsync (also in the repos) to backup my /home directory to a remote disk drive. Both are scheduled using cron to happen at convenient times. The mondoarchive I only run weekly (I'm not too bothered about losing a few updates), the rsync **much** more often (three times a day). When the HD fails (it has happened) I can use by mondo backup to restore the system to a new disk and rsync to restore the contents of /home. Others may have different (maybe better) options to do this.

H

---

### Post by Steve Moss on 2011-02-20
Hi Anglican

Thanks for the reply

I am very new to Ubuntu (and Linux)

Can you give some detailed instructions how to set up the procedures you suggest

Thanks for your help

---

### Post by anglican on 2011-02-21
> **Steve Moss said:**
> Hi Anglican

Thanks for the reply

I am very new to Ubuntu (and Linux)

Can you give some detailed instructions how to set up the procedures you suggest

Thanks for your helpInstructions for mondoarchive are very simple, you just need to install the software:
```
sudo apt-get install mondo
```The backup can be scheduled using the system's "cron" scheduler. Because it requires access to the whole filesystem it will need to be run by root so first you open a terminal then run a shell as root:
```
sudo bash
```In that shell you will be editing root's "crontab" file (see "man crontab" for more information) which you do with the command:
```
crontab -e
```which opens roots crontab in the default editor (probably vim). If you're not familiar with vim, you need to type "i" when it starts to get into insert mode then make the following entry:
> 0 4 * * 0 /usr/sbin/mondoarchive -Or -E "/home" -d /dev/hda -9 -e -s 4400mwhich will run your backup at 4am on Sunday (see "man 5 crontab" for detail on how to run at different times). Type [ESC] to leave insert mode them ":wq" to write the file and quit. This will backup everything except /home onto a DVD/RW at /dev/hda (you may need to change this device to suit your system) - I'm assuming that everything will fit on one DVD (compression is used, so provided your system is < 9GB it probably will). The DVD will be bootable and can be used to restore the system onto "bare metal".

Backing up /home I do with the rsync program (I think it is in the default install). Again you can use cron to run it, but it doesn't need to be run as root if you only have one user on your system. I tend to run it much more frequently (1-3 times daily) - it depends on how much work you're willing to risk losing to a crash. rsync adds only (the parts of) files that have changed since the last backup so it is relatively fast (mondoarchive will take a few hours to run - though it also can make incremental backups). How you use rsync depends on where you're backing up to e.g. another computer or an external hard drive. I suggest reading the man page and a bit of googling. Basically it works just like a cp (copy) command.

Hope this helps.

H

---

### Post by Steve Moss on 2011-02-21
OK undrstand the first part of the cron command

I can't work out the last part. eg how do I find out my DVD drive dev sd[COLOR="Red"]?[/COLOR]and an explanation of the command 

 /dev/hda -9 -e -s 4400m

Sorry to be a pain

---

### Post by anglican on 2011-02-21
> **Steve Moss said:**
> OK undrstand the first part of the cron command

I can't work out the last part. eg how do I find out my DVD drive dev sd[COLOR=Red]?[/COLOR]and an explanation of the command 

 /dev/hda -9 -e -s 4400m
You can try ```
cdrecord -scanbus
``` which will give a list something like:
> scsibus1:
    1,0,0    100) 'SONY    ' 'DVD RW DW-U14A  ' '2.0d' Removable CD-ROM
    1,1,0    101) *
    1,2,0    102) *
    1,3,0    103) *
    1,4,0    104) *
    1,5,0    105) *
    1,6,0    106) *
    1,7,0    107) *so you would then use "-d 1,0,0" where I've used "-d /dev/hda" in the above example. This bit is very dependent on your system set-up. On the system I copied this entry from it wasn't happy with "1,0,0" for some reason but was quite happy with "/dev/hda" (I take a pragmatic approach to such issues - whatever works!). The "-9" specifies the level of compression to be used "-9" is the maximum which obviously takes the longest time, -0 is for no compression. "-e" is to prevent the DVD being ejected during the backup (necessary for an unattended backup). Finally "-s 4400" sets the size for each disk in the backup set (hopefully only one). Actually for a DVD/RW you could make this 4480.

Just to complete the options I've used, "-Or" is specifying DVD media and -E specifies the list of directories to exclude from the backup> **Steve Moss said:**
> 
Sorry to be a painNo problem.

H

---

### Post by Steve Moss on 2011-02-24
Sorry I haven't given any feedback

Not had time to try out yet

Will have a go at the weekend

---

### Post by Steve Moss on 2011-02-25
ok I typed      cdrecord -scanbus and got this


scsibus1:
	1,0,0	100) 'PHILIPS ' 'DROM6216        ' 'DD08' Removable CD-ROM
	1,1,0	101) 'PHILIPS ' 'DVDR1628P1      ' 'Q1.1' Removable CD-ROM
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *

I then typed crontab -l and got this

# m h  dom mon dow   command
50 6 * * 5 /usr/sbin/mondoarchive -Or -E "/home" -d 1,1,0 -9 -e -s 4480m

which I beleive should run at 6:50 am on Friday

I put a blank DVD-RW disk in the drive and waited until 6:50

Nothing happened

I am not sure if this is importnat but when I type cdrecord -scanbus with the DVD in the drive I get

scsibus1:
	1,0,0	100) 'PHILIPS ' 'DROM6216        ' 'DD08' Removable CD-ROM
	1,1,0	101) '
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *

Any ideas what to do now?

---

### Post by anglican on 2011-02-25
> **Steve Moss said:**
> ok I typed      cdrecord -scanbus and got this


scsibus1:
	1,0,0	100) 'PHILIPS ' 'DROM6216        ' 'DD08' Removable CD-ROM
	1,1,0	101) 'PHILIPS ' 'DVDR1628P1      ' 'Q1.1' Removable CD-ROM
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *

I then typed crontab -l and got this

# m h  dom mon dow   command
50 6 * * 5 /usr/sbin/mondoarchive -Or -E "/home" -d 1,1,0 -9 -e -s 4480m

which I beleive should run at 6:50 am on Friday

I put a blank DVD-RW disk in the drive and waited until 6:50

Nothing happened

I am not sure if this is importnat but when I type cdrecord -scanbus with the DVD in the drive I get

scsibus1:
	1,0,0	100) 'PHILIPS ' 'DROM6216        ' 'DD08' Removable CD-ROM
	1,1,0	101) '
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *

Any ideas what to do now?To test mondo I'd run it from the command line rather than use cron i.e.
```
sudo bash
/usr/sbin/mondoarchive -Or -E "/home" -d 1,1,0 -9 -e -s 4480m
```
mondo makes a log file (mondoarchive.log) to tell you what happened in /var/log so take a look at that. Generally the error comes at the end - so no need to post it all here. To make it run quickly you can always exclude a bit more of your HD (e.g. add /usr to the list). If nothing really happened, I'd expect cron to report that, so you might take a look at root's mail for any errors:
```
sudo bash
mail
```
mondoarchive can also be run interactively by not specifying command line options. I don't really know what to make of your "cdrecord -scanbus" output, perhaps this is a case where "1,1,0" isn't going to work, try using something like "/dev/dvdrecorder" instead - which is probably a symlink to /dev/<something> which could also be used. Use ```
ls -l /dev/dvdrecorder
``` to find out the actual device being used.

H

---

### Post by Steve Moss on 2011-02-26
Hi again

The problem seems to be finding the device name for the DVD+RW

I tried typing in   root@steve:~# df

And got his result

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb5            138071088  12045292 119012116  10% /
none                   1026476       300   1026176   1% /dev
none                   1030824      1568   1029256   1% /dev/shm
none                   1030824       216   1030608   1% /var/run
none                   1030824         0   1030824   0% /var/lock
none                   1030824         0   1030824   0% /lib/init/rw
/dev/sda1            293025568  62632436 230393132  22% /media/6E401B1B401AEA1B
/dev/sdb1            146781256     70520 146710736   1% /media/C6ACBA98ACBA830B
/dev/sdc1              1957600    188800   1768800  10% /media/Lexar
/dev/sdd1             40174960        16  40174944   1% /media/External


 sda is my first hard drive
 sdb is my second hard drive
 sdc is my USB drive
 sdd is n external hard drive

I can't find the DVD+RW or the CD drives so it looks like they are not mounted. In fact it although the DVD drive works it appears that there is no record of it anywhere on the system

---

### Post by Steve Moss on 2011-02-26
Forgot to add the mondoarchive.log output


...ran with res=256
[TH=3436] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sdb

No, Schlomo, that doesn't mean /dev/sdb is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=3436] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
        [TH=3436] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /10%/mondo.tmp.6mh5xo for Mondo.
        [TH=3436] libmondo-files.c->register_pid#815: Unregistering PID
        [TH=3436] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not mounted
--------------------------------end of output------------------------------
...ran with res=256

---

### Post by bikodog on 2011-02-26
> **Steve Moss said:**
> Hi

How can I protect against, for instance a hard drive failure, or corrupt OS so that I can't boot into Ubuntu

Can I create a recovery disk that will load up all my settings, installed software etc or is there some other method to do this

My apologies if this has been covered elsewhere

Another way is to use rsync to backup entire partitions to an external drive. This is especially handy if you install /home on a separate partition.

psychocat's tutorial explains it pretty well

[http://www.psychocats.net/ubuntu/backup]("http://www.psychocats.net/ubuntu/backup")

---

### Post by Steve Moss on 2011-02-26
Hi bikodog thanks for helping me

I clicked your link and followed the instructions until it said


Then copy the appropriate settings directories to the /etc/skel directory.

At this point I got stuck

What are the "appropriate" settings???

Sorry I am so thick but this is all new to me

---

### Post by Steve Moss on 2011-02-26
OOps forgot to say this is the remastersys link

---

### Post by anglican on 2011-02-28
> **Steve Moss said:**
> Forgot to add the mondoarchive.log output


...ran with res=256
[TH=3436] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sdb

No, Schlomo, that doesn't mean /dev/sdb is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=3436] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
        [TH=3436] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /10%/mondo.tmp.6mh5xo for Mondo.
        [TH=3436] libmondo-files.c->register_pid#815: Unregistering PID
        [TH=3436] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not mounted
--------------------------------end of output------------------------------
...ran with res=256Can you put in a DVD that actually does mount - and then use df to find the device name for your drive.

H

---

### Post by Steve Moss on 2011-02-28
yes


Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb5            138071088  11280548 119776860   9% /
none                   1023760       304   1023456   1% /dev
none                   1030824      1228   1029596   1% /dev/shm
none                   1030824       348   1030476   1% /var/run
none                   1030824         0   1030824   0% /var/lock
none                   1030824         0   1030824   0% /lib/init/rw
/dev/sdb1            146781256     70520 146710736   1% /media/C6ACBA98ACBA830B
/dev/sda1            293025568  62632436 230393132  22% /media/6E401B1B401AEA1B
/dev/sdd1              1957600    188832   1768768  10% /media/Lexar
/dev/sdc1             40174960   6978272  33196688  18% /media/External
/dev/sr1                122836    122836         0 100% /media/2007.11.03_2329

I then tried running

sudo bash
/usr/sbin/mondoarchive -Or -E "/home" -d /dev/sr1 -9 -e -s 4480m

but got the same eroor message

HOWEVER I seem to have created a recover disk using Remastersys but haven't figured out how to schedule it

I have also worked out rsync but would very much appreciate if you could give me the command variables you use. I guess I can then just add these into crontab

---

### Post by anglican on 2011-02-28
> **Steve Moss said:**
> 
I have also worked out rsync but would very much appreciate if you could give me the command variables you use. I guess I can then just add these into crontabI use rsync over ssh for my backup, I followed instructions found here:

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

However, if you don't need to do this securely over a network (i.e. to a local disk) it's much simpler, you can just put everything into a shell script something like:
```
#!/bin/sh

# Full name of rsync binary
RSYNC=/usr/bin/rsync

# 1st backup path
RPATH=/path/to/backup/direcory/
LPATH=/home/

$RSYNC -az $LPATH $RPATH
```... which you schedule with cron.

H

---

### Post by anglican on 2011-02-28
> **Steve Moss said:**
> 
I then tried running

sudo bash
/usr/sbin/mondoarchive -Or -E "/home" -d /dev/sr1 -9 -e -s 4480m

but got the same eroor message

What does ls -l /dev/dvd show? Perhaps if you try something like /dev/dvdrw0 (or 1) you might have more luck.

H

---

### Post by Steve Moss on 2011-02-28
#!/bin/sh

# Full name of rsync binary
RSYNC=/usr/bin/rsync

# 1st backup path
RPATH=/path/to/backup/direcory/
LPATH=/home/

$RSYNC -az $LPATH $RPATH

EEEEEK!!!!

I want to back up automatically at regular intervals on an incremental basis to an external hard drive. I was hoping to be able to do something simple like the following line in crontab

50 6 * * 5 /user/bin/rsync /home/steve /media/external 

with the appropriate paramaeters (-b -r etc etc)

If that would work what parameters would I set?

---

### Post by Steve Moss on 2011-02-28
You suggest I type ls -l /dev/dvd

root@steve:~# ls -l /dev/dvd 
lrwxrwxrwx 1 root root 3 2011-02-28 14:44 /dev/dvd -> sr1

I have tried using /dev/dvd    or   /sr1     or /dev/sr1

all give the same error message

---

### Post by Steve Moss on 2011-02-28
OK

Fingers crossed

I found a thread that says the repositories only have old versions. I checked mine and it was 1.2.something. I have uninstalled mondo and reinstalled latest version 2.2.9.5-1

The backup is running so we will see if it completes but gonna take about an hour

---

### Post by Steve Moss on 2011-03-01
No good

Got to write to disc and failed at that point

Looks as if its a software problem

Will try the mondo forums

---

