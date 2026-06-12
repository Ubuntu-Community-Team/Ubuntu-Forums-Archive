---
title: "A script to tune RAID (should work with types of RAID)"
date: 2012-01-28
forum: General Help
---

### Post by alfonso78 on 2012-01-28
Hi,

I've been learning a lot in these past weeks on tuning RAID so I decided to write a script that should find from actual tests which are the best settings for your system.
Please run it without any other kind of load on the CPU and disks to have a realistic measure.

It's far from perfect. For sure it won't harm your system (any change done is lost after reboot if you don't edit manually /etc/rc.local). So feel free to test it and let me know if it brings any increase in performances!

It must run as root and it takes a few hours to finish (a suggest running it overnight).

For the sake of explanation, the script is for sure sub-optimal since it tests only 9 * 4 settings instead of 9 * 9 * 9 * 9 but the script would probably need days to find "the optimal settings" plus I notice there is a certain fluctuation in results anyway, so I think this is a good enough approximation.

I don't think my results will be useful for you, but just to share my results, this is the outcome of the script (don't forget to adapt to the name of your md and your sdX):

```
echo 8192 > /sys/block/md0/md/stripe_cache_size
echo 256 > /sys/block/sdb/queue/max_sectors_kb
echo 256 > /sys/block/sdc/queue/max_sectors_kb
echo 256 > /sys/block/sdd/queue/max_sectors_kb
echo 256 > /sys/block/sde/queue/max_sectors_kb
blockdev --setra 64 /dev/sd[bcde]
blockdev --setra 16384 /dev/md0
```

I re-utilized a lot of ideas from [this other post]("http://ubuntuforums.org/showthread.php?t=1494846") about tuning but the approach is totally different: I don't use formulas, I test what really makes reading and writing faster!

the script:

```
#!/bin/bash
#
# Please note this test requires 30 GB of free space
# in your RAID md device
#
# The aim of this script is to find the best settings for performance 
# of your RAID by testing each setting separately.
# This script does make some system modification, but if you don't
# make these changes permanent (e.g. write them in /etc/rc.local)
# At the next boot all the changes will be lost, 
# so fill free to play with it!
#
# developed by alfonso / Jan 2012
#
#
# this is your mount point for the RAID
# PLEASE NOTE the script will REMOVE any file called testfile*.out in this folder!!
MNT=/storage
# this is device from which to get input
# no need to change this
INPUT=/dev/zero

# test for priviledges
if [ "$(whoami)" != 'root' ]
then
  echo Need to be root!
  echo ABORT
  exit 1
fi

if ! [ -d $MNT/lost+found ]
then
  echo
  echo "$MNT is not a file system! Something went wrong?"
  echo ABORT
  exit 1
fi

# find out which one is your md
# note that the script only works for one md. If you have more than one 
# just uncomment the line below and type something like MDDEV=md0
MDDEV="`cat /proc/mdstat | grep md | head -1 | awk '{print $1}'`"
# MDDEV=md0

if [ -z "$MDDEV" ]
then
  echo
  echo "I can\'t find any md"
  echo ABORT
  exit 1
fi

#
# get the letter of all devices from cat /proc/mdstat
#
# this expression takes the output of /proc/mdstat
# then takes the line of our md
# then changes spaces into new lines
# then takes only lines starting with sd
# then take the 3rd character (a for sda1, etc)
# and then remove new lines to make a single string
DEVS="`cat /proc/mdstat | grep $MDDEV | tr " " "\n" | grep '^sd' | awk '{print substr($0,3,1)}' | tr -d "\n"`"
echo "These are devices found in $MDDEV: $DEVS"

function test_write()
{
# writing tests:

  echo -n .
  hdparm -f /dev/sd[$DEVS] > /dev/null
  WRTE1=`dd if=$INPUT of=$MNT/testfile1.out bs=100kB count=100000 2>&1 | grep copied`
  WRUN1=`echo $WRTE1 | awk ' { print ( $(NF) ) }'`
  WRSP1=`echo $WRTE1 | awk ' { print ( $(NF-1) ) }'`
  if [ $WRUN1 != "MB/s" ];
  then
    echo
    echo "This script was created for all speeds measured in MB/s"
    echo ABORT
    exit 1
  fi
  
  echo -n .
  hdparm -f /dev/sd[$DEVS] > /dev/null
  WRTE2=`dd if=$INPUT of=$MNT/testfile2.out bs=1MB count=10000 2>&1 | grep copied`
  WRUN2=`echo $WRTE2 | awk ' { print ( $(NF) ) }'`
  WRSP2=`echo $WRTE2 | awk ' { print ( $(NF-1) ) }'`
  if [ $WRUN2 != "MB/s" ];
  then
    echo
    echo "This script was created for all speeds measured in MB/s"
    echo ABORT
    exit 1
  fi
  
  echo -n .
  hdparm -f /dev/sd[$DEVS] > /dev/null
  WRTE3=`dd if=$INPUT of=$MNT/testfile3.out bs=10MB count=1000 2>&1 | grep copied`
  WRUN3=`echo $WRTE3 | awk ' { print ( $(NF) ) }'`
  WRSP3=`echo $WRTE3 | awk ' { print ( $(NF-1) ) }'`
  if [ $WRUN3 != "MB/s" ];
  then
    echo
    echo "This script was created for all speeds measured in MB/s"
    echo ABORT
    exit 1
  fi
  
  AVG_WRITE=`echo "($WRSP1+$WRSP2+$WRSP3)*100/3" | bc`
    
  #echo " Average write is $AVG_WRITE MB/s NOTE: there should be a dot before the last 2 digits"
  echo " average write is `echo "scale=2; $AVG_WRITE / 100;" | bc` MB/s"
  
#  echo $WRTE1
#  echo $WRTE2
#  echo $WRTE3
}

function test_read()
{

# reading tests:

  echo -n .
  hdparm -f /dev/sd[$DEVS] > /dev/null
  READ1=`dd if=$MNT/testfile1.out of=/dev/null bs=100kB count=100000 2>&1 | grep copied`
  RDUN1=`echo $READ1 | awk ' { print ( $(NF) ) }'`
  RDSP1=`echo $READ1 | awk ' { print ( $(NF-1) ) }'`
  if [ $RDUN1 != "MB/s" ];
  then
    echo
    echo "This script was created for all speeds measured in MB/s"
    echo ABORT
    exit 1
  fi
  
  echo -n .
  hdparm -f /dev/sd[$DEVS] > /dev/null
  READ2=`dd if=$MNT/testfile2.out of=/dev/null bs=1MB count=10000 2>&1 | grep copied`
  RDUN2=`echo $READ2 | awk ' { print ( $(NF) ) }'`
  RDSP2=`echo $READ2 | awk ' { print ( $(NF-1) ) }'`
  if [ $RDUN2 != "MB/s" ];
  then
    echo
    echo "This script was created for all speeds measured in MB/s"
    echo ABORT
    exit 1
  fi
  
  echo -n .
  hdparm -f /dev/sd[$DEVS] > /dev/null
  READ3=`dd if=$MNT/testfile3.out of=/dev/null bs=10MB count=1000 2>&1 | grep copied`
  RDUN3=`echo $READ3 | awk ' { print ( $(NF) ) }'`
  RDSP3=`echo $READ3 | awk ' { print ( $(NF-1) ) }'`
  if [ $RDUN3 != "MB/s" ];
  then
    echo
    echo "This script was created for all speeds measured in MB/s"
    echo ABORT
    exit 1
  fi
  
  AVG_READ=`echo "($RDSP1+$RDSP2+$RDSP3)*100/3" | bc`
  
  #echo " Average read is $AVG_READ MB/s NOTE: there should be a dot before the last 2 digits"
  echo " average read is `echo "scale=2; $AVG_READ / 100;" | bc` MB/s"
  
  #echo $READ1
  #echo $READ2
  #echo $READ3
}

echo 
echo CURRENT SYSTEM SETTINGS
echo your current value of /sys/block/$MDDEV/md/stripe_cache_size is `cat /sys/block/$MDDEV/md/stripe_cache_size`
echo your current value of disk readahead is `blockdev --getra /dev/sd[$DEVS]`
echo your current value of md readahead is `blockdev --getra /dev/$MDDEV`
DEVINDEX=0
NUMDEVS=${#DEVS}
until [ $DEVINDEX -ge $NUMDEVS ]
do
  DEVLETTER=${DEVS:$DEVINDEX:1}
  echo your current value of /sys/block/sd$DEVLETTER/queue/max_sectors_kb is `cat /sys/block/sd$DEVLETTER/queue/max_sectors_kb`
  DEVINDEX=$[$DEVINDEX+1]
done
echo

for i in 1 2 3 4
#for i in 1 
# 1 when testing /sys/block/$MDDEV/md/stripe_cache_size
# 2 when testing disk readahead
# 3 when testing md readahead
# 4 when testing /sys/block/sdX/queue/max_sectors_kb
do
  BEST_WRITE=0
  BEST_WRITE_ID=0
  WORST_WRITE=0
  WORST_WRITE_ID=0
  BEST_READ=0
  BEST_READ_ID=0
  WORST_READ=0
  WORST_READ_ID=0
  for j in 64 128 256 512 1024 2048 4096 8192 16384
#  for j in 64 16384
  do
    #echo 
    #echo SYSTEM SETTINGS
    #echo your current value of /sys/block/$MDDEV/md/stripe_cache_size is `cat /sys/block/$MDDEV/md/stripe_cache_size`
    #echo your current value of disk readahead is `blockdev --getra /dev/sd[$DEVS]`
    #echo your current value of md readahead is `blockdev --getra /dev/$MDDEV`
    #DEVINDEX=0
    #NUMDEVS=${#DEVS}
    #until [ $DEVINDEX -ge $NUMDEVS ]
    #do
    #  DEVLETTER=${DEVS:$DEVINDEX:1}
    #  echo your current value of /sys/block/sd$DEVLETTER/queue/max_sectors_kb is `cat /sys/block/sd$DEVLETTER/queue/max_sectors_kb`
    #  DEVINDEX=$[$DEVINDEX+1]
    #done
    #echo
	case "$i" in
    1)  echo "We are testing md stripe_cache_size"
	    echo $j > /sys/block/$MDDEV/md/stripe_cache_size
        echo "step 1/4: NOW your current value of /sys/block/$MDDEV/md/stripe_cache_size is `cat /sys/block/$MDDEV/md/stripe_cache_size`"
        ;;
    2)  echo "We are testing disks readahead"
        blockdev --setra $j /dev/sd[$DEVS]
        echo "step 2/4: NOW your current value of disk readahead is `blockdev --getra /dev/sd[$DEVS]`"
        ;;
    3)  echo "We are testing md readahead"
        blockdev --setra $j /dev/$MDDEV
        echo "step 3/4 NOW your current value of md readahead is `blockdev --getra /dev/$MDDEV`"
        ;;
    4)  echo "We are testing disks max_sectors_kb"
        DEVINDEX=0
        NUMDEVS=${#DEVS}
        until [ $DEVINDEX -ge $NUMDEVS ]
        do
          DEVLETTER=${DEVS:$DEVINDEX:1}
          echo $j > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
          echo "step 4/4 NOW your current value of /sys/block/sd$DEVLETTER/queue/max_sectors_kb is `cat /sys/block/sd$DEVLETTER/queue/max_sectors_kb`"
          DEVINDEX=$[$DEVINDEX+1]
        done
        ;;
    *)  echo "This text should never appear"
	    echo ABORT
        exit 1
        ;;
    esac
    rm $MNT/testfile*.out 2> /dev/null
	test_write
	if [ "$BEST_WRITE" -eq "0" ]
	then
	  #echo 1st test BEST_WRITE
	  BEST_WRITE=$AVG_WRITE
	  BEST_WRITE_ID=$j
	fi
	if [ "$WORST_WRITE" -eq "0" ]
	then
	  #echo 1st test WORST_WRITE
	  WORST_WRITE=$AVG_WRITE
	  WORST_WRITE_ID=$j
	fi
	if [ "$AVG_WRITE" -ge "$BEST_WRITE" ]
	then
	  echo "found new best write - old: `echo "scale=2; $BEST_WRITE / 100;" | bc` new: `echo "scale=2; $AVG_WRITE / 100;" | bc`"
	  #echo "old: $BEST_WRITE new: $AVG_WRITE"
	  BEST_WRITE=$AVG_WRITE
	  BEST_WRITE_ID=$j
	fi
	if [ "$AVG_WRITE" -le "$WORST_WRITE" ]
	then
	  echo "found new worst write - old: `echo "scale=2; $WORST_WRITE / 100;" | bc` new: `echo "scale=2; $AVG_WRITE / 100;" | bc`"
	  #echo old: $WORST_WRITE new: $AVG_WRITE
	  WORST_WRITE=$AVG_WRITE
	  WORST_WRITE_ID=$j
	fi
	test_read
	if [ "$BEST_READ" -eq "0" ]
	then
	  #echo 1st test BEST_READ
	  BEST_READ=$AVG_READ
	  BEST_READ_ID=$j
	fi
	if [ "$WORST_READ" -eq "0" ]
	then
	  #echo 1st test WORST_READ
	  WORST_READ=$AVG_READ
	  WORST_READ_ID=$j
	fi
	if [ "$AVG_READ" -ge "$BEST_READ" ]
	then
	  echo "found new best read - old: `echo "scale=2; $BEST_READ / 100;" | bc` new: `echo "scale=2; $AVG_READ / 100;" | bc`"
	  #echo old: $BEST_READ new: $AVG_READ
	  BEST_READ=$AVG_READ
	  BEST_READ_ID=$j
	fi
	if [ "$AVG_READ" -le "$WORST_READ" ]
	then
	  echo "found new worst read - old: `echo "scale=2; $WORST_READ / 100;" | bc` new: `echo "scale=2; $AVG_READ / 100;" | bc`"
	  #echo old: $WORST_READ new: $AVG_READ
	  WORST_READ=$AVG_READ
	  WORST_READ_ID=$j
	fi
    rm $MNT/testfile1.out
    rm $MNT/testfile2.out
    rm $MNT/testfile3.out

  done
  echo BEST_WRITE is $BEST_WRITE
  echo BEST_WRITE_ID is $BEST_WRITE_ID
  echo WORST_WRITE is $WORST_WRITE
  echo WORST_WRITE_ID is $WORST_WRITE_ID
  echo BEST_READ is $BEST_READ
  echo BEST_READ_ID is $BEST_READ_ID
  echo WORST_READ is $WORST_READ
  echo WORST_READ_ID is $WORST_READ_ID
  # now we want to understand if this test affected more READ or WRITE performances
  DIFF_WRITE=$[ BEST_WRITE - WORST_WRITE ]
  DIFF_READ=$[ BEST_READ - WORST_READ ]
  if [ "$DIFF_READ" -gt "$DIFF_WRITE" ]
  then
    echo this test affected more READ than WRITE
	BEST_OVERALL_ID=$BEST_READ_ID
	WORST_OVERALL_ID=$WORST_READ_ID
  else
    echo this test affected more WRITE than READ
	BEST_OVERALL_ID=$BEST_WRITE_ID
	WORST_OVERALL_ID=$WORST_WRITE_ID
  fi
  case "$i" in
  1)  echo "$BEST_OVERALL_ID is the OPTIMAL value for md stripe_cache_size"
	  BEST_1_ID=$BEST_OVERALL_ID
      echo $BEST_OVERALL_ID > /sys/block/$MDDEV/md/stripe_cache_size
      ;;
  2)  echo "$BEST_OVERALL_ID is the OPTIMAL value for disks readahead"
	  BEST_2_ID=$BEST_OVERALL_ID
      blockdev --setra $BEST_OVERALL_ID /dev/sd[$DEVS]
      ;;
  3)  echo "$BEST_OVERALL_ID is the OPTIMAL value for md readahead"
	  BEST_3_ID=$BEST_OVERALL_ID
      blockdev --setra $BEST_OVERALL_ID /dev/$MDDEV
      ;;
  4)  echo "$BEST_OVERALL_ID is the OPTIMAL value for max_sectors_kb"
	  BEST_4_ID=$BEST_OVERALL_ID
      DEVINDEX=0
      NUMDEVS=${#DEVS}
      until [ $DEVINDEX -ge $NUMDEVS ]
      do
        DEVLETTER=${DEVS:$DEVINDEX:1}
        echo $BEST_OVERALL_ID > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
        DEVINDEX=$[$DEVINDEX+1]
      done
      ;;
  *)  echo "This text should never appear"
      echo ABORT
      exit 1
      ;;
  esac
done

echo the best for md stripe_cache_size is $BEST_1_ID
echo the best for disks readahead is $BEST_2_ID
echo the best for md readahead is $BEST_3_ID
echo the best for max_sectors_kb is $BEST_4_ID
echo
echo "Add the following lines to your /etc/rc.local"
echo 
echo "echo $BEST_1_ID > /sys/block/$MDDEV/md/stripe_cache_size"
echo "blockdev --setra $BEST_2_ID /dev/sd[$DEVS]"
echo "blockdev --setra $BEST_3_ID /dev/$MDDEV"
DEVINDEX=0
NUMDEVS=${#DEVS}
until [ $DEVINDEX -ge $NUMDEVS ]
do
  DEVLETTER=${DEVS:$DEVINDEX:1}
  echo "echo $BEST_4_ID > /sys/block/sd$DEVLETTER/queue/max_sectors_kb"
  DEVINDEX=$[$DEVINDEX+1]
done

exit 0
```

---

### Post by Sab3r on 2012-01-28
I tried it out on my newly created 4x2TB raid-5 array on my fresh Ubuntu Server 11.10 and I get the following error: 

```

line 22: $'\r': command not found
line 65: syntax error near unexpected token `$'\r''
line 65: `function test_write()

```

---

### Post by alfonso78 on 2012-01-28
> **Sab3r said:**
> I tried it out on my newly created 4x2TB raid-5 array on my fresh Ubuntu Server 11.10 and I get the following error: 

```

line 22: $'\r': command not found
line 65: syntax error near unexpected token `$'\r''
line 65: `function test_write()

```

Hi! thanks for trying this script.
Can you please tell me which is line 22 for you? you didn't cut and paste the whole script as it is in my post since line 22 is empty...

I tried again to test the script I posted and it's running just fine on my server right now.

Can you write exactly what you did?

alfonso

---

### Post by Sab3r on 2012-01-29
The script is a complete copy/paste of your code. I'm a Linux noob and must be doing something wrong. I put it in my home directory and ran it with this command: 
```

bash ./tuneraid.sh

```

Am I doing it wrong?

---

### Post by alfonso78 on 2012-01-29
> **Sab3r said:**
> The script is a complete copy/paste of your code. I'm a Linux noob and must be doing something wrong. I put it in my home directory and ran it with this command: 
```

bash ./tuneraid.sh

```

Am I doing it wrong?

I think I got it...

try this:
```
sudo apt-get install dos2unix
dos2unix tuneraid.sh

```

and run the script again.

beware, it takes a few hours.

Also there was errors in what the script was writing on the screen, please cut and paste it again (I fixed them).

Now you should be able to follow on screen what's going on.

run it from command line directly on the computer (so no telnet or ssh) otherwise you will have to start again if the connection resets.

let me know how it goes!

Also, this script only takes care of few aspects. Please make sure about your partition alignment and RAID chunk:
[http://ubuntuforums.org/showthread.php?t=1915740](http://ubuntuforums.org/showthread.php?t=1915740)

---

### Post by Sab3r on 2012-01-29
Now I get the following error: 
```

/storage is not a file system! Something went wrong?
ABORT

``` 

Does the raid array need to be mounted at /storage ?

---

### Post by Cheesemill on 2012-01-29
You have to change the line
```
MNT=/storage
```

To wherever your RAID is mounted.

---

### Post by Sab3r on 2012-01-29
What if I have two partitions on my raid array? Will it be enough to mount only the largest partition or do I need to remove my partitions and create one partition that covers the whole array?

---

### Post by alfonso78 on 2012-01-29
> **Sab3r said:**
> What if I have two partitions on my raid array? Will it be enough to mount only the largest partition or do I need to remove my partitions and create one partition that covers the whole array?

how can you have two partitions?
do you use LVM?
or do you mean you have two RAID arrays?

just write whatever is one of your mount points instead of:

```
MNT=/storage
```

e.g.

```
MNT=/mnt/raid
```

the script looks for /mnt/raid/lost+found to make sure it's a file system

---

### Post by Sab3r on 2012-01-29
What do you mean how can I have two partitions? I made an md0 array out of four disks, then used parted to make a gpt label/partition table and gdisk to make two ext4 partitions on it. 

A raid array is effectively a singular device (like a hard drive), right?

---

### Post by alfonso78 on 2012-01-29
> **Sab3r said:**
> What do you mean how can I have two partitions? I made an md0 array out of four disks, then used parted to make a gpt label/partition table and gdisk to make two ext4 partitions on it. 

A raid array is effectively a singular device (like a hard drive), right?

true. sorry. What I said made no sense. Forget it.

So yes, choose any of your devices mount points. The "findings" of the script will affect all partitions.

Anyway the script tests physical parameters of the disks and of the md device so how many partitions you create shouldn't matter.

good luck!

---

### Post by Sab3r on 2012-01-29
Thanks. I'll run it tonight.

---

### Post by Sab3r on 2012-01-30
It worked. Boosted my write performance from around 80MB/s to roughly 110MB/s. Read speed was and still is around 220MB/s. Measurements according to your script.

Thanks again.

---

### Post by alfonso78 on 2012-01-30
> **Sab3r said:**
> It worked. Boosted my write performance from around 80MB/s to roughly 110MB/s. Read speed was and still is around 220MB/s. Measurements according to your script.

Thanks again.

thank you for being the 1st beta tester ;-)
I hope others will find it useful as well!

---

### Post by alfonso78 on 2012-01-30
> **Sab3r said:**
> It worked. Boosted my write performance from around 80MB/s to roughly 110MB/s. Read speed was and still is around 220MB/s. Measurements according to your script.

Thanks again.

Ah, sorry, I forgot! I'd like to see if there is a pattern.

Can you please post the final part of the script (the part which you added in /etc/rc.local?)

---

### Post by Sab3r on 2012-01-30
> **alfonso78 said:**
> Can you please post the final part of the script (the part which you added in /etc/rc.local?)

```


echo 4096 > /sys/block/md0/md/stripe_cache_size
blockdev --setra 64 /dev/sd[bcde]
blockdev --setra 16384 /dev/md0
echo 64 > /sys/block/sdb/queue/max_sectors_kb
echo 64 > /sys/block/sdc/queue/max_sectors_kb
echo 64 > /sys/block/sdd/queue/max_sectors_kb
echo 64 > /sys/block/sde/queue/max_sectors_kb

```

---

### Post by Wittifred on 2012-03-04
I get lots of AWK-related errors when running the script:

```
.awk: (FILENAME=- FNR=1) <Fatal: Tried to access Field> -1.
./raidcheck.sh: Line 74: [: !=: <Unary operand expected>
```(basically all lines where AWK is called. Some post suggested embracing all variable names in double quotes might help. Is that true? I never understood AWK first place...

All I did was reducing the blocks by factor 10 to see the overall outcome of the test.

In addition, looking if "lost+found" exists is only successful für ext4 Filesystems.
I am using XFS so I added:

```
if ! [ -d $MNT/lost+found ] | [ -d $MNT/.Trash-1000 ]
then
  echo
  echo "$MNT is not a file system! Something went wrong?"
  echo ABORT
  exit 1
fi

```with the idea that most Ubuntu's will have a .Trash of the first user of the system...

How can I get around the AWK errors?

EDIT: "grep copied" is language specific ...  -> Can you try to replace the AWK line with something language-independant? Also, the - in my case -german decimal separator of "," is NOT very much liked by bc.

---

### Post by alfonso78 on 2012-03-04
> **Wittifred said:**
> I get lots of AWK-related errors when running the script:

```
.awk: (FILENAME=- FNR=1) <Fatal: Tried to access Field> -1.
./raidcheck.sh: Line 74: [: !=: <Unary operand expected>
```

hi, the script works since also an other user of the forum used it...
and I'm not a great expert on awk...

what happens if you write this:

```
cat /proc/mdstat | grep md | head -1 | awk '{print $1}'
```

---

### Post by langbach on 2012-04-09
I also get all kinds of awk errors...

running: cat /proc/mdstat | grep md | head -1 | awk '{print $1}'
gives me: md127


After replacing $WRUN1,2,3 with "$WRUN1",2,3 the problem hit me; you assume a specific language seting...
So i added LANG=en_us_8859_1 to the top of the script and the script is now running..

---

### Post by alfonso78 on 2012-04-10
> **langbach said:**
> I also get all kinds of awk errors...

running: cat /proc/mdstat | grep md | head -1 | awk '{print $1}'
gives me: md127


After replacing $WRUN1,2,3 with "$WRUN1",2,3 the problem hit me; you assume a specific language seting...
So i added LANG=en_us_8859_1 to the top of the script and the script is now running..

wow! thank you! I have no idea how the language setting influence the script. If you have time, I'd love to learn. can you explain?

thanks!

---

### Post by langbach on 2012-04-12
You do:
dd if=$INPUT of=$MNT/testfile1.out bs=100kB count=100000 2>&1 | grep copied

and expect the output to be "copied", but when language settings are in danish i get the following sent to grep:
0+0 blokke ind
0+0 blokke ud
0 byte (0 B) kopieret, 4,6322e-05 s, 0,0 kB/s

---

### Post by Zeggi on 2012-04-21
alfonso78
I ran the script you posted on this thread,
[http://ubuntuforums.org/showthread.php?t=1494846&page=3](http://ubuntuforums.org/showthread.php?t=1494846&page=3)

im just wondering what speeds you got with your script your runing on this thread.

I got 7 x 2TB (WD20EARS/WD20EARX)
all disks are alligned according to the 2048-2847 sector mod.

with the script you posted on that earlier post i get the following speeds,

Read,
Minimum: 266,8MB/S
Maximum: 619,1MB/S
Average: 466,7MB/S

Im just curious if the script you have on this thread is "better"
Edit: Im runing a raid 5 array.

---

### Post by tmittelstaedt on 2012-08-03
I get the following:
 

We are testing md stripe_cache_size
./tuneraid.sh: line 223: /sys/block/md0/md/stripe_cache_size: No such file or directory
cat: /sys/block/md0/md/stripe_cache_size: No such file or directory
step 1/4: NOW your current value of /sys/block/md0/md/stripe_cache_size is
.
 
this is a mirrored raid array not a striped array.

---

### Post by soomon on 2012-11-29
hey alfonso,

thanks VERY much for your script.
i was able to double my write speed :)
great job :guitar:

---

### Post by szafran on 2012-12-24
Nice job.
But the results of this script should be fed to a second script that is started at boot.
You can't (well you can - but you shouldn't) write scripts based on /dev/sd[abcd] - any changes on most of the controllers on your MoBo and the results of this script are useless. Sometimes you don't even have to change anything in the disk config of your system, and the letters will be changed after a reboot.

For eg. my NAS's MoBo drives under Ubuntu Server get listed in this order:
1st integrated SATA controller
2nd integrated SATA controller
Integrated PATA controller
Integrated USB 2.0 controller
Integrated USB 3.0 controller
PCI-e SATA controller

Now if anything is connected during boot to let's say USB 2.0 controller then the drives connected to all controllers initilized after that controller get a letter bump.
Tested it with a lot of scripts - sooner or later any script that was based on drive letters got kicked out for not working like it should, or (even worse) screwing something up in my system.

I think the best thing here would be to connect your script with this script: [http://ubuntuforums.org/showthread.php?t=1494846](http://ubuntuforums.org/showthread.php?t=1494846)

---

### Post by SaturnusDJ on 2013-03-08
> **alfonso78 said:**
> Hi,

I've been learning a lot in these past weeks on tuning RAID so I decided to write a script that should find from actual tests which are the best settings for your system.

Thanks for the post.

> **szafran said:**
> 
You can't write scripts based on /dev/sd[abcd] - any changes on most of the controllers on your MoBo and the results of this script are useless.

Agree. I think the best fix is to use /dev/sd* <--> UUID transformations.


I'm having strange behavior for "blockdev --setra X /dev/sd*" aka read ahead. 
[IMG]http://members.home.nl/saturnusdj/tech/read_ahead.png[/IMG]

Looks like disabling gives the best performance. :o

To everybody reading this:
Seeing the performance increase after running scripts like this and [this]("http://ubuntuforums.org/showthread.php?t=1494846")...it would be insane to let this go. What about starting a project to create a more user friendly tuning program? May still be terminal based, but some options should be added (test select, custom parameter range per test, amount of tests, testfile size).
If I could I would really build this. Unfortunately my Shell script experience is not much. I'm great in thinking of new usability, improving user experience, new features, etc...so if someone wants to start the project, PM me, I'm in!

---

