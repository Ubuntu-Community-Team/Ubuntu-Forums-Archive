---
title: "Bash scripting n00b, need help implementing a nested loop"
date: 2009-12-03
forum: General Help
---

### Post by EXrider on 2009-12-03
This is the first interactive Bash script I've ever written, so bare with me here...

As you can see below, the current solution is not very elegant and ends up forking child processes; or worse, just abruptly closing when invoked from a launcher into xfterm4!

I've been reading Bash tutorials off and on for several days, yet I still can't seem to figure out how to make this work in a loop correctly.  

```

#!/bin/bash
echo -E ****|sudo -S clear
echo
echo -E "Please insert a Zip disk and press any key to continue..."
read
echo -E "Waiting for Zip to spin up..."
sleep 5
echo
echo ***********CHECKING FOR EXISTING MOUNT************
echo 
sudo umount /dev/sdb4
sudo dmesg -c > /dev/null
echo 
echo
echo ************PARTITIONING DISK**************
echo
# Wipe out the first 33 blocks, which will take out any APM, MBR or GUID partition tables
sudo dd if=/dev/zero of=/dev/sdb bs=512 count=33 conv=sync
echo
# Wipe out the last 33 blocks, in case the disk is partitioned as GUID, this would be where the backup GPT is
sudo dd if=/dev/zero of=/dev/sdb bs=512 count=33 seek=196575 conv=sync
echo
# Write out a standard 4-partition (WTF? Yes.) Zip MBR partition table.  
# This is the only way Microtek likes it and the factory partitioning that Iomega loads "IBM Formatted" Zips with.
sudo dd if=~bbites/bcc1a-files/MBRZipPartitionTable.img of=/dev/sdb conv=sync
echo
# Make the kernel update its stat on the partition table
sudo partprobe -s /dev/sdb
echo
# Wipe the first block of our newly created partition according to sfdisk's documented recommendation
sudo dd if=/dev/zero of=/dev/sdb4 bs=512 count=1
echo
# Show the user the partition table we just wrote out
sudo /sbin/sfdisk -l /dev/sdb
echo
echo ************QuickFormat Started************
echo 
sudo /sbin/mkdosfs -v /dev/sdb4
echo
echo ************Mounting Zip************
echo 
sudo mount /dev/sdb4
echo
# This checks to see if the Zip actually mounted, if it didn't, it displays the I/O errors accumulated in dmesg for /dev/sdb, 
# notifies the user of the situation and offers the choice to try another Zip
ChkMount="`df | egrep -e "/dev/sdb4"`"
if [ "$ChkMount" = "" ]; then
	echo
	sudo dmesg -c >> /var/tmp/dmesgZipErrors.log && cat /var/tmp/dmesgZipErrors.log | egrep -i -e "error, dev sdb" -e "error on device sdb" && rm /var/tmp/dmesgZipErrors.log
	echo
        echo -E "The Zip disk FAILED to mount, this disk is probably defective,"
	echo -E "any I/O errors encountered are shown above."
	sudo eject /dev/sdb
        echo -E "Do you want to make another Zip disk?"
		select yn in "Yes" "No"; do
    			case $yn in
        			Yes ) (./LeftDriveMakeZip2PlusPartition.sh); exit; break;;
        			No ) exit;;
    			esac
		sudo -k
		done
        exit
else
echo 
echo *************Copying Files************
echo 
sudo cp -Rv ~bbites/bcc1a-files/bcc1a-2.3/* /media/Zip100
echo 
echo ************Syncing Disks************
sudo sync
echo
echo ************Copy Complete************
echo 
echo ************UNMOUNTING ZIP************
echo 
sudo umount /dev/sdb4
echo 
echo ************Checking File System Integrity************
echo 
sudo /sbin/dosfsck -avVw /dev/sdb4
echo 
echo ************File System Check Complete************
echo 
echo ************Syncing Disks Again************
echo 
sudo sync
echo
echo -E "************ Searching for Errors logged on Zip drive /dev/sdb ************"
echo
# Display any I/O errors accumulated in dmesg for /dev/sdb during the copy operation 
sudo dmesg -c >> /var/tmp/dmesgZipErrors.log && cat /var/tmp/dmesgZipErrors.log | egrep -i -e "error, dev sdb" -e "error on device sdb" && rm /var/tmp/dmesgZipErrors.log
echo
sudo eject -s /dev/sdb
sudo -k
echo
fi
echo -E "Do you want to make another Zip disk?"
select yn in "Yes" "No"; do
    case $yn in
        Yes ) (./LeftDriveMakeZip2PlusPartition.sh); exit; break;;
        No ) exit;;
    esac
done

```


If anyone can offer some insight, I'd be most appreciative.

---

### Post by diesch on 2009-12-03
```

while true; do
 do_something
 
 echo -E "Do you want to make another Zip disk?"
 select yn in "Yes" "No"; do
   if [ "$yn" = "No" ]; then
      echo "Bye."
      exit
   fi
 done
done
```

---

### Post by EXrider on 2009-12-04
> **diesch said:**
> ```

while true; do
 do_something
 
 echo -E "Do you want to make another Zip disk?"
 select yn in "Yes" "No"; do
   if [ "$yn" = "No" ]; then
      echo "Bye."
      exit
   fi
 done
done
```

and the result of that is:
```

*something*
Do you want to make another Zip disk?
1) Yes
2) No
#? 1
#? 1
#? 1
#? 1
#? 1
#? 2
Bye.
```

I'm missing something here.  Can you elaborate more?  Because that doesn't loop, and if I put "echo *something*" outside of the *if* statement, it does loop (as expected) but how do I re-do what's outside of the *if*?

Note that there are also **two *case* statements** in my script.  I want a *1* in either *case* to loop back to the top of the script and a *2* to *end* obviously.  

Sorry if the solution seems obvious to you, because it isn't to me. :confused:

---

### Post by diesch on 2009-12-04
Sorry, copied the wrong code. Should be

```
#!/bin/bash
while true; do
 do_something
 select yn in "Yes" "No"; do
     case $yn in
       Yes) break;;
       No) echo Bye.; exit;;
     esac
 done
done
```

Replace *do_something* with whatever you want to do.

---

### Post by EXrider on 2009-12-08
That worked great.  Thanks for your help!

---

