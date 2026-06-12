---
title: "Missing packages when running job from cron"
date: 2011-05-24
forum: General Help
---

### Post by krumpy on 2011-05-24
I just want to run a simple backup script from the cron.  The script works fine when I run it using sudo backup.sh, but fails under the cron.  Specifically another script that my script is running fails.

backup.sh
#!/bin/bash
#Commands to run in conjunction with backup
DATE=`date +%d_%m_%y`
[B]bash /usr/local/bin/boot_info_script055.sh
[/B]cp /etc/apt/sources.list /home/matt/Documents/LinuxDocs/CurrentSys/$DATE.sources.list.backup
dpkg --get-selections > /home/matt/Documents/LinuxDocs/CurrentSys/$DATE.ubuntu.packages
#synch with network drive
rsync -arv --delete-after --exclude=/matt/.gvfs/ --exclude=**/*cache*/ --exclude=**/*Cache*/ --exclude=**/*Trash*/ --exclude=**/*trash*/ /home/matt /media/netdrive/UbuntuBackup/

for some reason when I try to run it from the cron the boot_info_script055.sh throws several errors about missing packages:

"blkid" could not be found.
"fdisk" could not be found.
"filefrag" could not be found.
"losetup" could not be found.
Please install the  missing program(s) and run boot_info_script again.

boot_info_script055 is a script that I'd seen several other people on here using in their backup jobs.  The relevant section of boot_info_script055 is below:

Programs="
    awk
    basename
    blkid
    cat
    dd
    dirname
    expr
    fdisk
    filefrag
    fold
    grep
    hexdump
    losetup
    ls
    mkdir
    mount
    pwd
    rm
    sed
    sort
    umount
    wc
    whoami"

Check_Prog=1;

for Program in $Programs ; do

    if ! type $Program > /dev/null 2>&1 ; then
    echo \"$Program\" could not be found. >&2
    Check_Prog=0;
    fi
done

if [ $Check_Prog -eq 0 ];
then
   echo "Please install the  missing program(s) and run boot_info_script again." >&2
   exit 1;
fi;

I guess I don't understand why this would fail when run under the cron.  I wasn't familiar with "type", but after looking at it I think it just tells you whether a package is installed (and its location) and if it isn't found it throws an error, which the script is capturing.  Any ideas would be appreciated.

---

### Post by matt_symes on 2011-05-24
Hi

Try adding this to the start of your script before you all the boot info script.

```
export PATH=$PATH:/sbin
```

Kind regards

---

### Post by krumpy on 2011-05-24
That fixed everything except filefrag, which is under usr/sbin?

---

### Post by matt_symes on 2011-05-24
Hi

> **krumpy said:**
> That fixed everything except filefrag, which is under usr/sbin?
[FONT=monospace]
[/FONT]```
[FONT=monospace]export PATH=$PATH:/sbin:/usr/sbin[/FONT]
```[FONT=monospace]

Kind regards
[/FONT]

---

### Post by krumpy on 2011-05-24
Works perfectly now - thank you.  Could you provide a brief explanation as I'm pretty new to Linux.  It didn't seem like **type** had any sort of path dependency when I was running it from the command line.

---

### Post by blind2314 on 2011-05-24
That's because from the command line you had your environment variable, PATH, available to you and your shell. Cron doesn't recognize those environment variables, which is why pathing to your script/commands wasn't working properly. 
 
When you followed the advice of the poster above, and explicitly exported your PATH from within the script, that allowed the commands to be ran. Basically, when running something from Cron, make sure everything is fully pathed or export as you did above.

---

### Post by matt_symes on 2011-05-24
Hi

> **krumpy said:**
> Works perfectly now - thank you.  Could you provide a brief explanation as I'm pretty new to Linux.  It didn't seem like **type** had any sort of path dependency when I was running it from the command line.

Cron does not have your environment. It has roots.

Your environment defines many things including paths to look through to find programs in the file system. 

Your paths were different from the paths cron looks through so it could not find the programs to run. Hence the error messages.
```
export PATH=$PATH:/sbin:/usr/sbin
```Adding this line to your script tells cron to look at the 2 new paths as well as its own. The export keyword will export the new paths so that child processes (i.e the boot script you script calls) also get to see the new paths.

Have a read of this for a general overview of cron.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Kind regards

---

### Post by krumpy on 2011-05-24
I think I understand.  The CronHowto page says, "Depending on the commands being run, you may need to  expand the root users PATH variable by putting the following line at the  top of their crontab file: PATH=/usr/sbin:/usr/bin:/sbin:/bin"[FONT=monospace]

[/FONT]I fixed it by adding the path to my script but it seems like I should probably add it to my crontab.  Is there anything else that should be in the "standard" crontab?

---

### Post by matt_symes on 2011-05-24
Hi

As a general rule, i add paths and other environmental variables to scripts and not to the cron tab itself.

This allows fine grained control over which scripts gets which variables and also makes the scripts self contained. This is personal preference though. 

If you ever display anything on X you will also need to set up the DISPLAY variable.

Kind regards

---

