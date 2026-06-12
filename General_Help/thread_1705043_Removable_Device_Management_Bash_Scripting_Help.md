---
title: "Removable Device Management Bash Scripting Help"
date: 2011-03-11
forum: General Help
---

### Post by TobalJackson on 2011-03-11
Hello there.

I'm somewhat new to ubuntu, but fairly competent with computers in general. I have a somewhat specific task I'd like to accomplish with Bash Scripting involving the automation of a series of tasks.  The most important aspect of the whole process is that the thumbdrive gets fully reformatted just in case there are any lingering Windows-Infections (like autorun.inf rootkits/viruses or even MBR Bootkits) to get the drives ready to be used on Infected windows machines.

I'd like to be able to manually launch the script, which will populate attached removable disks (using something like lsusb or blkid) and match them to a list of known UUID's.  Then if the devices' UUIDs match one of the 8-10 UUID's on the script's internal list (or referenced list) it will run the commands to Format each disk as vfat (sudo mkfs -t vfat) while maintaining the disk's previous label (LABEL=TDrive01, Tdrive02, ...Tdrive10) then copy a local directory's contents (/dev/sda1/Thumbdrive_Image) to each thumbdrive.

Can anyone point me in the right direction to getting something like this working?  I can imagine a very uncomplicated looking script, but I'm just not familiar enough with ubuntu to know how to work with FSTAB/UUIDS/LABELS/Mount points.  I've read that working with the generic device name/mount point (like /dev/sda#) isn't specific enough anymore as device insertion order can affect it.

I'd like to be able to do the following in programmatic/bash script form:
#Somehow get the UUID's and Labels of each attached drive (usually 4 - 5 attached at once) and save the labels for use later after formatting each drive
$sudo blkid
#here I'd like to make sure the devices the script will format are NONE OTHER than the ones defined explicitly in the script:
$if UUID=["AE5E-844F", "XXXX-XX01", "XXXX-XX02"
    {mkfs -t vfat}
#after each drive is formatted/blanked, copy a local directory with files/folders to each attached thumbdrive on the list:
$cp -r /home/tobaljackson/ThumbDriveImage/ /dev/UUID="AE5E-844F" & /dev/UUID="XXXX-XX01" & /dev/UUID="XXXX-XX02" #etc...

and that's pretty much it.  I know this can become waaay more complicated than I really "need" but I'd like to at least just have a minimum functionality of being able to wipe a group of removable devices and not others; and then copy a local directory onto each of those devices. If anyone could show me some example commands or even just list the commands/scripting guides I need to read up on, that'd be great too.  I'm looking forward to hearing how you guys approach this scenario, Thanks!

---

### Post by TobalJackson on 2011-03-15
Ok so I've gotten somewhere through irc and online guides.  My script looks like this so far: 

```
#!/bin/bash
count=1
total=`blkid | sed -n '$='`
until [ $count -gt $total ]; do
    list=`blkid | sed -n "$count"p| cut -c 1-9`
    echo $list
    echo $count
    #I want the next line to say "let drive$count=list"    
    let drive$count=count
    let count=count+1
done

echo $drive1
echo $drive2
echo $drive3
#I want these last 3 lines to echo "/dev/sda1" "/dev/sda2" etc.
```when run the output looks like this: 

```
$ sudo ./herp.sh
/dev/sda1
1
/dev/sda2
2
/dev/sda4
3
/dev/sda5
4
/dev/sdb1
5
1
2
3

```What I want is to change the line "let drive$count=count" to "let drive$count=list" so that I get

```

$ sudo ./herp.sh
/dev/sda1
1
/dev/sda2
2
/dev/sda4
3
/dev/sda5
4
/dev/sdb1
5
/dev/sda1
/dev/sda2
/dev/sda4
```But instead I get the error: 
 ```
$ sudo ./herp.sh
/dev/sda1
1
./herp.sh: line 9: let: /dev/sda1: syntax error: operand expected (error token is "/dev/sda1")
/dev/sda2
2
./herp.sh: line 9: let: /dev/sda2: syntax error: operand expected (error token is "/dev/sda2")
/dev/sda4
3
./herp.sh: line 9: let: /dev/sda4: syntax error: operand expected (error token is "/dev/sda4")
/dev/sda5
4
./herp.sh: line 9: let: /dev/sda5: syntax error: operand expected (error token is "/dev/sda5")
/dev/sdb1
5
./herp.sh: line 9: let: /dev/sdb1: syntax error: operand expected (error token is "/dev/sdb1")



```Can anyone tell me why I get the error and how to get it to do what I want it to do?

---

### Post by TobalJackson on 2011-03-15
Alright, I have more progress. An aside- Should I move this thread to another section?

Anyway, this is how my script looks now, and I'm almost satisfied with it except for the last key features it needs to have.


```
#!/bin/bash
echo "I'm going to format these devices:" 
count=1 #sets the until counter
#number=0
total=`blkid | grep -i hd | sed -n '$='` #counts the number of devices matching the pattern 'HD' and stores the integer in total
if [ $total ]; then #makes sure there are devices are attached to format
	until [ $count -gt $total ]; do #repeat for each device
		list=`blkid | grep -i hd | sed -n "$count"p | cut -c 1-9` #grabs the device name
		let count=count+1
		#let number=number+1
		echo $list #shows list of drives to be formatted
		#eval drive${number}=$list
		done
else
	echo "no drives detected"
	exit
fi

read choice
if [ $choice = y ] || [ $choice = Y ]; then
	echo "choice is Yes!"
	echo "formatting drives..."
	count=1
	echo "" > format.txt #initializes file with list of devices
	until [ $count -gt $total ]; do
		format=`blkid | grep -i hd | sed -n "$count"p | cut -c 1-9`
		let count=count+1
		echo $format >> format.txt
		umount $format
		mkdosfs $format
		echo "done formatting" $format
	done
else
echo "choice is not yes..."
fi

```

Sorry for the sloppy comments.  At this point the script will show all drives with a label containing HD, prompt the user to format all with y/n, and then proceeds to format them as fat, keeping the label and uids intact.  

At this point all I really would like help with is implementing the next part of the script.  After each drive is formatted, I'd like to issue a command to copy a single local directory recursively to each of the formatted drives in parallel. 

I don't quite know how to do this as thus far i've been using until loops to get things done.  I'd use the same loop method and do things inline, except that the local image is ~1gb, and i'd like to be able to invoke a copy mechanism that transfers from a single source to all targets simultaneously.  

I've read that the "tee" program can do this, but I'm not sure how to implement that in my script, as well as the xargs command to spawn multiple cp processes.  I think either of these methods should work, i'm just unsure of how to format my script to pass the $format/$list output to the cp or tee programs.  

The current approach is I've used  echo "" > format.txt and echo $format >> format.txt to make a file with a list of devices, but I don't know how to pass this into the tee/cp(xargs) program(s).  

Any help is greatly appreciated!

---

### Post by TobalJackson on 2011-03-16
lol ok, so, I've finished my script!  Even though nobody replied to this topic, I was able to find all the answers I needed by using Google.  I'll leave it here just in case anyone else was wondering about the same things I was having issues with.  I know it may look ugly, but it works like a charm!

```
#!/bin/bash
#Coded and tested by None Other than TobalJackson.  First bash script, so enjoy XD
echo "Hello and welcome to Herp! Please make sure there is only 1 instance of this script running at a time.  If you're unsure, open terminal and type \"sudo ps -a\" without the quotes, and make sure you only see 1 \"herp\" running. Otherwise you'll need to answer \"n\" to the following question and stop Derping so you can Herp."
echo "I'm going to format these devices:" 
count=1
total=`blkid -o list| grep -i hd | wc -l`
until [ $count -gt $total ]; do
    list=`blkid -o list | grep -i hd | sed -n "$count"p`
    let count=count+1
    echo $list
done
echo "Do you want me to? y/n"
read choice
if [ $choice = y ] || [ $choice = Y ]; then
    echo "You chose Yes!"
    echo "Formatting drives..."
    count=1
    echo "" > format.txt
    until [ $count -gt $total ]; do
        multicopy=`blkid -o list | grep -i hd | sed -n "$count"p | cut -c 20-23`
        format=`blkid -o list | grep -i hd | sed -n "$count"p | cut -c 1-9`
        let count=count+1
        umount $format
        mkdosfs -n "$multicopy" $format
        echo "done formatting" $format
    done
else
echo "Choice was not affirmative, exiting."
exit
fi

count=1
until [ $count -gt $total ]; do
        multicopy=`blkid -o list | grep -i hd | sed -n "$count"p | cut -c 20-23`
        devices=`blkid -o list | grep -i hd | sed -n "$count"p | cut -c 1-9`
function copyfiles {
cp -r /media/MASTER_THUM/* "/media/$multicopy"
sleep 4
umount -f $devices
echo "Finished copying to" $devices $multicopy "and unmounted the drive!"
exit
}
        let count=count+1
        rm -r "/media/$multicopy"
        mkdir "/media/$multicopy"
        mount -t vfat $devices "/media/$multicopy"
        echo "Now copying to $multicopy, Please wait for the message \"Finished copying to $multicopy\" to remove the drive. Thanks!"
        copyfiles &
done
exit
```Like I said at the beginning of this thread, this script will automatically format any and all removable disks attached to the machine with volume labels containing "HD" and then copy a local file repository back on to each drive (simultaneously, in parallel).

I had a tough time discovering that adding the "&" to the end of any command would spawn it as a new process, meaning the script will not wait for it to finish before continuing.  Searching google only yielded pages and pages of results telling me to use cp with xargs or the "tee" command.  I ended up seeing it in an "advanced bash" scripting guide as a part of bash Special Characters.

---

### Post by TobalJackson on 2011-03-22
hello there. One last update I've made to the script finalizes it as follows:

```
#!/bin/bash
#Coded and tested by None Other than TobalJackson.  First bash script, so enjoy XD
function checkdupes {
	count=1
	total=`blkid -o list| grep -i hd | wc -l`
	if [ $total -eq 0 ]; then
		echo "No drives detected! Seems like you derped when you should've herped...Please fix the drive labels (must contain \"HD\" and a letter, e.g. \"HD G\".) Exiting due to lack of materials to work with."
		exit
	else
		until [ $count -gt $total ]; do
			probe=`blkid -o list | grep -i hd | sed -n "$count"p | cut -c 20-23`
			let count=count+1
			result=`blkid -o list|grep -c "$probe"`
			if [ $result -gt 1 ]; then
				echo "The drive label" $probe "appears more than once! To correct this, open the disk utility, unmount one of the drives labeled" $probe ", and assign the drive a new label containing (capital) HD and a letter, e.g. \"HD G\".  Exiting herp."
				exit
			fi
		done
	fi
}
checkdupes

echo "Hello and welcome to Herp! Please make sure there is only 1 instance of this script running at a time.  If you're unsure, open terminal and type \"sudo ps -a\" without the quotes, and make sure you only see 1 \"herp\" running. Otherwise you'll need to answer \"n\" to the following question and stop Derping so you can Herp."

echo "I'm going to format these devices:" 
count=1
total=`blkid -o list| grep -i hd | wc -l`
until [ $count -gt $total ]; do
	list=`blkid -o list | grep -i hd | sed -n "$count"p`
	let count=count+1
	echo $list
done
echo "Do you want me to? y/n"
read choice
if [ $choice = y ] || [ $choice = Y ]; then
	echo "You chose Yes!"
	echo "Formatting drives..."
	count=1
	until [ $count -gt $total ]; do
		multicopy=`blkid -o list | grep -i hd | sed -n "$count"p | cut -c 20-23`
		format=`blkid -o list | grep -i hd | sed -n "$count"p | cut -c 1-9`
		let count=count+1
		umount $format
		mkdosfs -n "$multicopy" $format
		echo "done formatting" $format
	done
else
echo "Choice was not affirmative, exiting."
exit
fi

count=1
until [ $count -gt $total ]; do
		multicopy=`blkid -o list | grep -i hd | sed -n "$count"p | cut -c 20-23`
		devices=`blkid -o list | grep -i hd | sed -n "$count"p | cut -c 1-9`
function copyfiles {
cp -r /media/MASTER_THUM/* "/media/$multicopy"
sleep 4
umount -f $devices
echo "Finished copying to" $devices $multicopy "and unmounted the drive!"
exit
}
		let count=count+1
		rm -r "/media/$multicopy"
		mkdir "/media/$multicopy"
		mount -t vfat $devices "/media/$multicopy"
		echo "Now copying to $multicopy, Please wait for the copy operation to finish. Thanks!"
		copyfiles &
done
exit
```

I implemented a little duplicate-checker routine at the beginning to ensure there aren't multiple drives with the same label, and prompts the user to change it if there are.  Thanks for looking, and please if you have any comments or suggestions, post them here!

---

