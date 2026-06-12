---
title: "copying files with large names"
date: 2012-01-31
forum: General Help
---

### Post by LiamG on 2012-01-31
I have an external hard disk with all my music on it. When I installed 11.04, I copied them across to my laptop HD. But some of them didn't copy because the file names were too long. This is peculiar, as I'd copied the same files onto my previous installation of Ubuntu with no problem. Does anyone know how I could copy them so that this doesn't happen?

Also, now that most of the files (150GB+) are on my laptop without problem, is there a way that I could "merge" the files from the external HD so that identical ones don't get replaced?

---

### Post by Khayyam on 2012-02-01
LiamG ...

The ext filename limit is 255 bytes (equivalent to 255 charaters) so I don't imagine this was the problem you encountered. It may have been characters in the filenames but its hard to say without further details.

The easiest method of syncing two directory structures is with 'rsync' from the command line. You probably drag-n-droped the files but it shouldn't be too difficult to have rsync selectively sync any missed from the 'source' directory, and preserve any changes that have since been made to the 'destination' directory. That said, some care is needed when using rsync as if not used properly some unintended results may ensue. For that reason you should first understand what the following commands do before proceeding to perform these on the 'destination'. The '--list-only' and '--dry-run' options will be used bellow so that you get some idea of what the command will do on the 'destination' prior to running it without these options (that is, actually sync'ing).

I'll assume that 'source' and 'destination' still have the same name and directory structure .. ie (source) */media and (destination) */media 

```
sudo rsync -av --list-only --dry-run /path/to/source/media /path/to/destination/media
```Sudo is used so that rsync can deal with permissions. The '-a' equates to 'archive' mode (and will preserve timestamps, user permissions, etc), and the '-v' option is for 'verbose'. As we are not using '--delete' the 'destination' should not be sync'ed to a exact replica of 'source', it should only copy files/directories not present on the 'target'.

Note that you have to be careful with trailing slashes, '/media' and '/media/' are **not** the same thing (or rather they behave differently), so when sync'ing be sure that you don't wipe out files in 'destination' due to a trailing slash. I'll reiterate what I said above: you should have some understanding of what the command does before using it. I'd recommend you read some online examples, like [this]("http://defindit.com/readme_files/rsync_backup.html"), and get familiar with its operation prior to doing this faux-real.

Also, as we have maintained permissions from 'source' to 'destination',  'destination' may now have files not owed (or readable) by your user, this can be fixed either by not using 'archive mode' or by using 'chown' (**ch**ange **own**ership).

```
sudo chown -R username /path/to/destination/media
```HTH ..

---

### Post by LiamG on 2012-02-02
Thanks Khayyam, that was very detailed instructions.

I think that the file names probably do exceed 255 characters--long album names and titles sometimes add up. The strange thing is that they were all copied to a linux system without any hassle before, but now they won't copy. Is there any way of forcing them to copy? I don't particularly care about keeping the file titles.

---

### Post by philinux on 2012-02-02
> **LiamG said:**
> Thanks Khayyam, that was very detailed instructions.

I think that the file names probably do exceed 255 characters--long album names and titles sometimes add up. The strange thing is that they were all copied to a linux system without any hassle before, but now they won't copy. Is there any way of forcing them to copy? I don't particularly care about keeping the file titles.

You could use eyed3 to rename them all. I used a script which I used when I had to recover a lot of deleted files. Here's the script but I cant remember now how it worked. It was a while ago.

```
for file_name in `ls *.mp3`
do

eyeD3 --rename="%A - %a - %n - %t"  $file_name

done
```

---

### Post by Vaphell on 2012-02-02
we do not promote parsing ls output here
*for file_name in *.mp3* is 1. enough 2. better and safer
double-quoting $file_name wouldn't hurt either

---

### Post by Khayyam on 2012-02-03
[LEFT]LiamG .. your welcome.

I imagine the number of files exceeding 255 chars are few. If, as you said, they have copied without problem in the past then perhaps the problem lies elsewhere. Still, to be sure you can search for files >255 chars with the following oneliner:

```
find /path/to/directory | awk -F/ 'length($NF) >255 {print $NF}'
```If this returns nothing then all the files are less than, or equal to, 255 chars, and file length isn't what causes them to fail to copy.

HTH ..
[/LEFT]

---

### Post by LiamG on 2012-02-07
Thanks--this one will be very helpful!

---

### Post by imachavel on 2012-02-07
I get very lost in these threads, as I can never find the name of my back up drive in linux, I was looking through this though:

[http://www.basicconfig.com/linux/mount](http://www.basicconfig.com/linux/mount)

and it helped me quite a bit


cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: TSSTcorp Model: CDRW/DVD TSH492B Rev: TB06
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD5000AAKS-0 Rev: 05.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: WD       Model: 2500BEVExternal  Rev: 1.02
  Type:   Direct-Access                    ANSI  SCSI revision: 00


rescan-scsi-bus -l
Host adapter 0 (ata_piix) found.
Host adapter 1 (ata_piix) found.
Host adapter 2 (ata_piix) found.
Host adapter 3 (ata_piix) found.
Host adapter 4 (usb-storage) found.
Scanning SCSI subsystem for new devices
Scanning host 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, LUNs  0 1 2 3 4 5 6 7
Scanning for device 0 0 0 0 ... 
OLD: Host: scsi0 Channel: 00 Id: 00 Lun: 00
      Vendor: TSSTcorp Model: CDRW/DVD TSH492B Rev: TB06
      Type:   CD-ROM                           ANSI SCSI revision: 05
Scanning host 1 for  SCSI target IDs  0 1 2 3 4 5 6 7, LUNs  0 1 2 3 4 5 6 7
Scanning host 2 for  SCSI target IDs  0 1 2 3 4 5 6 7, LUNs  0 1 2 3 4 5 6 7
Scanning for device 2 0 0 0 ...                 
OLD: Host: scsi2 Channel: 00 Id: 00 Lun: 00
      Vendor: ATA      Model: WDC WD5000AAKS-0 Rev: 05.0
      Type:   Direct-Access                    ANSI SCSI revision: 05
Scanning host 3 for  SCSI target IDs  0 1 2 3 4 5 6 7, LUNs  0 1 2 3 4 5 6 7
Scanning host 4 for  SCSI target IDs  0 1 2 3 4 5 6 7, LUNs  0 1 2 3 4 5 6 7
Scanning for device 4 0 0 0 ...                 
OLD: Host: scsi4 Channel: 00 Id: 00 Lun: 00
      Vendor: WD       Model: 2500BEVExternal  Rev: 1.02
      Type:   Direct-Access                    ANSI SCSI revision: -1
0 new device(s) found.               
0 device(s) removed.                            
root@danel-Dimension-4700:/home/danel# Host adapter 0 (ata_piix) found.
bash: syntax error near unexpected token `('
root@danel-Dimension-4700:/home/danel# Host adapter 1 (ata_piix) found.
bash: syntax error near unexpected token `('
root@danel-Dimension-4700:/home/danel# Host adapter 2 (ata_piix) found.
bash: syntax error near unexpected token `('
root@danel-Dimension-4700:/home/danel# Host adapter 3 (ata_piix) found.
bash: syntax error near unexpected token `('
root@danel-Dimension-4700:/home/danel# Host adapter 4 (usb-storage) found.
bash: syntax error near unexpected token `('
root@danel-Dimension-4700:/home/danel# You need to run scsi-rescan-bus.sh as root
You: command not found


Anyway that is just to get started. That is weird, I was in root. Then if I could verify how to type the path, I'd use rsync, but then again it's not as though I need to. oh well....

---

### Post by SeijiSensei on 2012-02-07
Do any of the filenames have embedded spaces?  Unless you're careful, bash will treat a filename with a space in it as two separate positional parameters (bash uses space as the delimiter).

rsync usually has no problem in these situations, but if you're using a script to loop through the directory and don't embed the filenames in double-quotes, you'll get wonky results.  I think that was the second point in Vaphell's post.

---

