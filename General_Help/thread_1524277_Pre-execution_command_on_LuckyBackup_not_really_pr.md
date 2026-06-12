---
title: "Pre-execution command on LuckyBackup not really pre-execution"
date: 2010-07-05
forum: General Help
---

### Post by Ralph L on 2010-07-05
I want to put a pre-execution zenity function (zenity --question --text "Please mount backup disk.") in LuckyBackup.  I am able to do this, but part of the LuckyBackup backup task is executed before the zenity function is executed.  In particular the oldest snapshot and log files are deleted, before the zenity check to see that the backup disk is mounted.  If the user clicks "no" the backup is not executed, but the snapshot and log are already deleted.  If this is done several times all the snapshots are deleted with no new backup taking place.

Can anyone suggest a way to do the zenity disk mounted test, and allow a "no" answer without loosing the snapshot and log files?

Thanks

Ralph

---

### Post by Ralph L on 2010-07-19
I solved this by writing a script that uses zenity to ask if the backup disk is mounted and, depending on the answer, either exit or execute the appropriate luckybackup profile.  I also set the -AX parameters in the luckybackup User Defined Command Options.  This causes luckybackup (rsync) to dump Access Control Lists (ACLs) and Extended Attributes, which I want to use. The script is as follows:

#! /bin/bash
zenity --question --text "Is Backup Disk Mounted??"
# If the person said cancel, then tell them. If they said ok, then tell them that.
if [ "$?" == "1" ] ; then
    echo "You clicked cancel."
    exit
fi
if [ "$?" == "0" ] ; then
    echo "You clicked OK."
    luckybackup ~/.luckyBackup/profiles/lbprofile1.profile
    exit
fi
else echo "Input was neither a 0 nor a 1.  Something is wrong."
fi

I installed it in /usr/local/myprograms/luckybackup_scripts.  I then put a symbolic link to it in /usr/local/bin.  This structure allowed me to make the script available to all users, to keep my programs separate from others, and to allow the script to be executed by merely specifying the file name of the script (bash searches /usr/local/bin automatically so the complete path is not needed.

Hope this can be of help to somebody.

Ralph

---

