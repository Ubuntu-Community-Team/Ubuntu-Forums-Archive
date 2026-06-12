---
title: "scripting help"
date: 2011-11-04
forum: General Help
---

### Post by runny6play on 2011-11-04
Hey, Im writing a script that wil sync two document folders. one being my ubuntu documents folder and the other my flash drive documents folder

I need help figuring out how i can eather merge the files together or copy all files and all subdirectory... files... and each time run.. copy new subdirectorys and and update existening ones.
I dont want to use rsync. I much rather use my own script.

my first thoughts were to tar the documents folder on my computer
then move it to the flash drive.. add the other documents folder with the -u option. then make a copy of tar on the parent directory in which the documents folder lies.(on the harddrive) and then untar and force overwrite the existing files. but the tar arcive didnt merge the two documents directories like i hoped so i couldnt figure out what to do from there using this method.

my second plan. was to make a script that would find all of the sub directories (using find -type d) and output them to a file or standard in.
and then make a directory of each on the root of the drive. but i cant figure out how to exec everything in a manner where mkdir would read a single line at a time or something like cat would  input to mkdir one line. ( which i could just repeat the mkdir command how many every times nessary

---

### Post by galvatron408 on 2011-11-04
I remember when a Linux Systems Administrator was fired for not using rsync. ;)

---

### Post by oldfred on 2011-11-05
This is my backup script to another drive:

```
#!/bin/bash
# backup script - mybackup.sh
# a - archive, retain file settings equals -rlptgoD (no -H,-A,-X)
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
# -l, --links copy symlinks as symlinks
# -i, --itemize-changes
# -t, --times preserve modification times
# --exclude option to prevent copying things

# ! not 
if [ ! -d /mnt/Backup ]; then
     mkdir /mnt/Backup
fi
 
mount -t ext3 /dev/sda2 /mnt/Backup

echo "starting..."
# So I know additional sources
cp /etc/apt/sources.list ~/Documents/LinuxDocs/CurrentSys/sources.list.backup
# List of all installed applications
dpkg --get-selections > ~/Documents/LinuxDocs/CurrentSys/ubuntu-files
# System Boot Configuration
bash ~/Documents/LinuxDocs/CurrentSys/bootscripts/boot_info_script.sh

rsync -aruvlP /mnt/data/Documents /mnt/Backup
rsync -aruvlP /mnt/data/Projects /mnt/Backup
rsync -aurvlP --exclude '.thumbnails' /home /mnt/Backup
#rsync -auvP /share /mnt/Backup
#rsync -auvP /media/floppy /mnt/Backup
#rsync -auvP /etc /mnt/Backup
# Backup to date named versions
#rsync /path/from /path/to/backups --backup --suffix=_`date +%Y%m%d-%H%M%S` -Pitr
echo "done"
exit 0

```

Originally from:
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

---

### Post by prodigy_ on 2011-11-05
> **galvatron408 said:**
> I remember when a Linux Systems Administrator was fired for not using rsync. ;)
Talk about incompetent management...

P.S. Nothing against rsync here but it's definitely NOT the only solution. ;)

---

### Post by gsmanners on 2011-11-05
> **prodigy_ said:**
> P.S. Nothing against rsync here but it's definitely NOT the only solution. ;)

No, there's also zsync, csync, grsync, isync, obsync, etc. (okay maybe that joke isn't all that good).

---

### Post by mendhak on 2011-11-05
> **runny6play said:**
> Hey, Im writing a script that wil sync two document folders. one being my ubuntu documents folder and the other my flash drive documents folder

I need help figuring out how i can eather merge the files together or copy all files and all subdirectory... files... and each time run.. copy new subdirectorys and and update existening ones.
I dont want to use rsync. I much rather use my own script.

my first thoughts were to tar the documents folder on my computer
then move it to the flash drive.. add the other documents folder with the -u option. then make a copy of tar on the parent directory in which the documents folder lies.(on the harddrive) and then untar and force overwrite the existing files. but the tar arcive didnt merge the two documents directories like i hoped so i couldnt figure out what to do from there using this method.

my second plan. was to make a script that would find all of the sub directories (using find -type d) and output them to a file or standard in.
and then make a directory of each on the root of the drive. but i cant figure out how to exec everything in a manner where mkdir would read a single line at a time or something like cat would  input to mkdir one line. ( which i could just repeat the mkdir command how many every times nessary
Is there a reason you don't want to use rsync? It's basically doing what you want, so you'll end up reinventing the proverbial wheel to some extent.  

You do have the option of looking at the [rsync source code]("http://rsync.samba.org/download.html") to emulate what they are doing.

---

### Post by runny6play on 2011-11-06
thanks everyone. And I realise I'd be reinventing the wheel but i need to get better at scripting. So far I know bash and some python. I like problem soving and am looking for some experience. I very well could use rsync. But I like the idea of making a tool to sync these two folders myself. Im kind of an extreme do it yourselfer.
I think ive kind of come up with a way to do it. But i need to know if you can recurively extract a tar file and only overwrite existing files if there newer?
ive seen options for this but their only for adding folders to the archive.. not extracting them.

---

### Post by Habitual on 2011-11-06
I use unison for this very same task.
Mirror my /home/jj directory to my 3TUSB Device.

install ```
sudo apt-get install -y unison
``` it.
```
vi .unison/default.prf
```
# Unison preferences file
root = /home/jj
root = /media/Keepers

and I run it with:
```
unison default -batch -ui text -auto
```

flawless 1-for-1 copy.

Description: A file-synchronization tool for Unix and Windows
 Unison is a file-synchronization tool for Unix and Windows, written
 in OCaml. It allows two replicas of a collection of files and
 directories to be stored on different hosts (or different disks
 on the same host), modified separately, and then brought up to
 date by propagating the changes in each replica to the other.

HTH.

---

