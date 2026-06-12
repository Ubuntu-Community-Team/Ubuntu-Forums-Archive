---
title: "drive mounts as /media/286CC2A6397A0F2A"
date: 2010-02-08
forum: General Help
---

### Post by rock4christ on 2010-02-08
Instead of mounting as something normal(like sda1), one of my drives mounts as /media/286CC2A6397A0F2A and(presumable because of this) doesnt show up in Storage Device Manager, so I can't auto mount

---

### Post by falconindy on 2010-02-08
It has no label, so it's being mounted according to its UUID.

---

### Post by rock4christ on 2010-02-08
> **falconindy said:**
> It has no label, so it's being mounted according to its UUID.

can I add a label?

---

### Post by switch10 on 2010-02-08
you can set a label with palimpsest.  here is how to install it. [http://www.webupd8.org/2009/08/how-to-install-palimpsest-disk-utility.html](http://www.webupd8.org/2009/08/how-to-install-palimpsest-disk-utility.html)

...Or it may be in synaptic under "disk utility"

---

### Post by switch10 on 2010-02-08
Yeah, if you search "disk utility" in "ubuntu software center" its the first thing that comes up.

click on the partition , and there is an option on the bottom to change the label

---

### Post by rock4christ on 2010-02-08
Error changing fslabel: helper exited with exit code 1: fstype ntfs not supported

---

### Post by switch10 on 2010-02-08
You have to change it with Windows if it is NTFS or FAT.

---

### Post by rock4christ on 2010-02-08
I gave it a label, but it still does not show up in pysdm

---

### Post by dcstar on 2010-02-08
> **rock4christ said:**
> Error changing fslabel: helper exited with exit code 1: fstype ntfs not supported

Install the **ntfsprogs** package.

---

### Post by rock4christ on 2010-02-08
any solutions for how i can make it work? it still refuses to show up in Storage Device Manager. any other way to make it automount?

---

### Post by K7522 on 2010-02-10
I use a script for auto mounting and auto starting files that I made a while back. It's on my diary here: [http://ubuntuforums.org/showthread.php?p=8712700](http://ubuntuforums.org/showthread.php?p=8712700)

For convenience, here's how I've done it and I removed the file starting section of the script. If you want that functionality just go to the link provided above.

Save the script wherever you'd like. Don't forget to Right Click -> Properties -> Permissions and check "Allow executing file as program" check box. For convenience, I'll assume you've placed it at ~/Scripts/startup.sh. You will also need to create a 'logs' folder inside Scripts for the log to work properly.

Lines 5 and 6 need to be edited, and mntSrc, mntDest, mntPart all need to be edited to your own uses. Make sure mntEnd is greater than or equal to your last number. The reason I did it this way is so you can mount anywhere from 1 to 100,000 drives or folders to different places without the code crapping out if you comment out one mount.

```
#!/bin/bash

## Setting Environment Variables.
## The sudo password for proper function of script. I believe this is only required if you're running it manually.
export password="SUDOPASSWORD"
export logFile="/home/USERNAME/Scripts/logs/startup.log"

function mountFolders {
## Variables for the mountFolders function.
## WARNING! If you are not mounting a hard drive, do not include mntPart variable.
mntVar="1" ## 0 to disable function, 1 to enable function
mntEnd="4"

mntSrc1="/dev/sda2"
mntDest1="/media/winpart"
mntPart1="ntfs"

mntSrc2="/dev/sda3"
mntDest2="/media/data"
mntPart2="ntfs"

# mntSrc3="/opt/lampp/htdocs"
# mntDest3="/home/kayjor/htdocs"

mntSrc4="/opt/lampp/htdocs/jackstack"
mntDest4="/home/jackstack/htdocs"

## Here we mount the listed folders if they are not already mounted.
while [ $mntVar -gt "0" ] && [ $mntVar -le $mntEnd ]
do
	echo "Current fuction is at $mntVar out of $mntEnd." >> $logFile
	## The reason we have to run the next two parts is because we want to go down the list, doing
	## mntSrc1, then mntSrc2, etc. This was the easiest way to accomplish the task. The next two
	## lines are a bit confusing to the basic user. This creates a variable named mntS and give
	## it a value. That value is mntSrc plus the value of $mntVar at the end. The
	## beginning of the script has the value set to one, so mntS is mntSrc1. You can see that's
	## one of our variables that we need, but it's just the name.
	mntS="mntSrc`echo $mntVar`"
	mntD="mntDest`echo $mntVar`"
	mntP="mntPart`echo $mntVar`"
	## Now that mntS has the name of the variable we are going to use, we have to get the value of
	## that variable, the following command creates a new variable. The value of that variable is
	## the value of the variable named in mntS. In the case of the beginning of the script, If 
	## mntSrc1 is 'hello' then mntSGet will also be 'hello'.
	mntSGet=${!mntS}
	mntDGet=${!mntD}
	mntPGet=${!mntP}
	## If the function does not exist, there is no reason to attempt to run it, so we skip it and
	## go to the next one (up to and including $mntEnd, see the while statement).
	if [ -z "$mntSGet" ]
	then
		echo "skipping mntVar number $mntVar, does not exist." >> $logFile
		mntVar=$[$mntVar+1]
	else
		## Here, we know that there is a variable, it does exist and it does have a value. So we need
		## to continue with our function and see if these folders are already mounted to their proper
		## places. If they are not mounted, we need to go ahead and do so.
		if [ $(mount | grep -c $mntDGet) != 1 ]
		then
			echo "$mntDGet is not mounted." >> $logFile
			## The mount does not exist, now we need to check if the destination folder exists.
			if [ ! -x $mntDGet ]
			then
				## The folder does not exist, create it.
				echo "$mntDGet folder does not exist. Creating." >> $logFile
				echo $password | sudo -S mkdir $mntDGet
			else
				## The folder exists, move on.
				echo "$mntDGet folder exists." >> $logFile
			fi
			## We have ensured that the directory is not mounted. We have ensured that the
			## folder does indeed exist. Now we need to mount the directory to the folder.
			## We need to check if this is a mounted folder or a mounted drive.
			if [ -z "$mntPGet" ]
			then
				echo "Mount is a folder, mounting $mntSGet to $mntDGet." >> $logFile
				echo $password | sudo -S mount --bind $mntSGet $mntDGet
			else
				echo "Mount is a drive, mounting $mntSGet to $mntDGet." >> $logFile
				echo $password | sudo -S mount -t $mntPGet $mntSGet $mntDGet
			fi
		else
		echo "$mntDGet is already mounted." >> $logFile
		fi
		## To make sure we don't try to mount the same thing over and over, we add one to the
		## value of mntVar here. This has to be within this if statement to ensure that the script
		## does not loop with no end.
		mntVar=$[$mntVar+1]
	fi		
done
}

mountFolders

echo "Finished Loading" >> $logFile
echo "--------------------" >> $logFile
exit 0
```

Once you've done that, you have your startup script and you need to set it to auto run on startup. You do so as follows:

```
sudo nano /etc/rc.local
```

Add this line above the exit line:

```
/home/USERNAME/Scripts/startup.sh
```

---

### Post by rock4christ on 2010-02-11
didn't work. anyway to make it show up in pysdm?

---

### Post by rock4christ on 2010-02-12
found a simple solution. I just added an entry into fstab.

---

