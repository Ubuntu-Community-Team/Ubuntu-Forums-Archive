---
title: "Script to tune mdadm raid5 (others too, maybe)"
date: 2010-05-27
forum: General Help
---

### Post by apeganz on 2010-05-27
edit: new version of the script, you now have to do less adjustments. should be pretty save to run on almost any system. regards, alex

I just wrote a script to improve my mdadm-raid's performance and felt like sharing. Maybe someone else can use it or get some inspiration from it.

Happy tuning,
Alex

PS: do NOT just run it, depending on your configuration it might seriously screw up your system if you don't alter it accordingly!

```
#!/bin/bash
###############################################################################
#  simple script to set some parameters to increase performance on a mdadm
# raid5 or raid6. Ajust the ## parameters ##-section to your system!
#
#  WARNING: depending on stripesize and the number of devices the array might
# use QUITE a lot of memory after optimization!
#
#  27may2010 by Alexander Peganz
###############################################################################


## parameters ##
MDDEV=md51              # e.g. md51 for /dev/md51
CHUNKSIZE=1024          # in kb
BLOCKSIZE=4             # of file system in kb
NCQ=disable             # disable, enable. ath. else keeps current setting
NCQDEPTH=31             # 31 should work for almost anyone
FORCECHUNKSIZE=true     # force max sectors kb to chunk size > 512
DOTUNEFS=false          # run tune2fs, ONLY SET TO true IF YOU USE EXT[34]
RAIDLEVEL=raid5         # raid5, raid6


## code ##
# test for priviledges
if [ "$(whoami)" != 'root' ]
then
  echo $(date): Need to be root >> /data51/smbshare1/#tuneraid.log
  exit 1
fi

# set number of parity devices
NUMPARITY=1
if [[ $RAIDLEVEL == "raid6" ]]
then
  NUMPARITY=2
fi

# get all devices
DEVSTR="`grep \"^$MDDEV : \" /proc/mdstat` eol"
while \
 [ -z "`expr match \"$DEVSTR\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\? \)'`" ]
do
  DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done

# get active devices list and spares list
DEVS=""
SPAREDEVS=""
while [ "$DEVSTR" != "eol" ]; do
  CURDEV="`echo $DEVSTR|cut -f -1 -d \ `"
  if [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\)'`" ]
  then
    SPAREDEVS="$SPAREDEVS${CURDEV:2:1}"
  elif [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\)'`" ]
  then
    DEVS="$DEVS${CURDEV:2:1}"
  fi
  DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done
NUMDEVS=${#DEVS}
NUMSPAREDEVS=${#SPAREDEVS}

# test if number of devices makes sense
if [ ${#DEVS} -lt $[1+$NUMPARITY] ]
then
  echo $(date): Need more devices >> /data51/smbshare1/#tuneraid.log
  exit 1
fi

# set read ahead
RASIZE=$[$NUMDEVS*($NUMDEVS-$NUMPARITY)*2*$CHUNKSIZE]   # in 512b blocks
echo read ahead size per device: $RASIZE blocks \($[$RASIZE/2]kb\)
MDRASIZE=$[$RASIZE*$NUMDEVS]
echo read ahead size of array: $MDRASIZE blocks \($[$MDRASIZE/2]kb\)
blockdev --setra $RASIZE /dev/sd[$DEVS]
blockdev --setra $RASIZE /dev/sd[$SPAREDEVS]
blockdev --setra $MDRASIZE /dev/$MDDEV

# set stripe cache size
STRCACHESIZE=$[$RASIZE/8]                               # in pages per device
echo stripe cache size of devices: $STRCACHESIZE pages \($[$STRCACHESIZE*4]kb\)
echo $STRCACHESIZE > /sys/block/$MDDEV/md/stripe_cache_size

# set max sectors kb
DEVINDEX=0
MINMAXHWSECKB=$(cat /sys/block/sd${DEVS:0:1}/queue/max_hw_sectors_kb)
until [ $DEVINDEX -ge $NUMDEVS ]
do
  DEVLETTER=${DEVS:$DEVINDEX:1}
  MAXHWSECKB=$(cat /sys/block/sd$DEVLETTER/queue/max_hw_sectors_kb)
  if [ $MAXHWSECKB -lt $MINMAXHWSECKB ]
  then
    MINMAXHWSECKB=$MAXHWSECKB
  fi
  DEVINDEX=$[$DEVINDEX+1]
done
if [ $CHUNKSIZE -le $MINMAXHWSECKB ] &&
  ( [ $CHUNKSIZE -le 512 ] || [[ $FORCECHUNKSIZE == "true" ]] )
then
  echo setting max sectors kb to match chunk size
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMDEVS ]
  do
    DEVLETTER=${DEVS:$DEVINDEX:1}
    echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
    DEVINDEX=$[$DEVINDEX+1]
  done
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMSPAREDEVS ]
  do
    DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
    echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
    DEVINDEX=$[$DEVINDEX+1]
  done
fi

# enable/disable NCQ
DEVINDEX=0
if [[ $NCQ == "enable" ]] || [[ $NCQ == "disable" ]]
then
  if [[ $NCQ == "disable" ]]
  then
    NCQDEPTH=1
  fi
  echo setting NCQ queue depth to $NCQDEPTH
  until [ $DEVINDEX -ge $NUMDEVS ]
  do
    DEVLETTER=${DEVS:$DEVINDEX:1}
    echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
    DEVINDEX=$[$DEVINDEX+1]
  done
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMSPAREDEVS ]
  do
    DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
    echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
    DEVINDEX=$[$DEVINDEX+1]
  done
fi

# tune2fs
if [[ $DOTUNEFS == "true" ]]
then
  STRIDE=$[$CHUNKSIZE/$BLOCKSIZE]
  STRWIDTH=$[$CHUNKSIZE/$BLOCKSIZE*($NUMDEVS-$NUMPARITY)]
  echo setting stride to $STRIDE blocks \($CHUNKSIZEkb\)
  echo setting stripe-width to $STRWIDTH blocks \($[$STRWIDTH*$BLOCKSIZE]kb\)
  tune2fs -E stride=$STRIDE,stripe-width=$STRWIDTH /dev/$MDDEV
fi

# exit
echo $(date): Success >> /data51/smbshare1/#tuneraid.log
exit 0
```

---

### Post by carpenike on 2010-10-24
Thanks much for sharing your script. I've run it on my new Arch Linux system and it works great. 

I edited out:


#blockdev --setra $RASIZE /dev/sd[$SPAREDEVS]


As I have no spare devices; though I don't think that really mattered in the end anyway.

---

### Post by fackamato on 2010-10-27
Any benchmarks? ;)

---

### Post by nosebreaker on 2011-03-30
This worked for me with my seagate 2tb drives in a raid5 array.

I did have to modify some lines in the script, the lines where it is expecting /dev/sd[a-z]1 in my case needed to be changed to /dev/sd[a-z]3 and then it ran.

Before:
Write speed 55 MB/s
Read speed 115 MB/s

After
Write speed is 107 MB/s
Read speed is 164 MB/s

A significant improvement!

---

### Post by drnick79 on 2011-05-04
I came across this post while searching for a way to change the stripe cache size and read ahead values in my RAID 5 array (10.4 desktop). 
 
A few questions:
 
If I put this script in /etc/init.d and then execute an update rc.d defaults command, should this change these parameters every time the system boots up? I've tried to manually set them in the rc.local file, but it doesn't appear to work. I've read a few posts which inquire how to make these parameter changes permanent, and there don't seem to be any definitive solutions. 
 
How does one find out the chunk size and block size of one's array? Would the disk utility provide this info?
 
And finally, what is the algorithm for setting these parameters in this script based upon? 
 
Thanks in advance for any answers to my queries,
 
Nick
 
PS  Also thanks to the OP for sharing this script!:)

---

### Post by nipennem on 2011-07-31
This is a nice script, but it is lacking some documentation.

[LIST=1]
[*]How did you get to the 'formulas' to calculate the read ahead size for the component drives and the entire array?

```
RASIZE=$[$NUMDEVS*($NUMDEVS-$NUMPARITY)*2*$CHUNKSIZE]   # in 512b blocks
echo read ahead size per device: $RASIZE blocks \($[$RASIZE/2]kb\)
MDRASIZE=$[$RASIZE*$NUMDEVS]
echo read ahead size of array: $MDRASIZE blocks \($[$MDRASIZE/2]kb\)
```

This formula works great for me on a 7-disk RAID-6 array, but I'd like to understand it.

I guess you wrote 512-byte blocks, because you assume that the logical sector size for all components is 512 bytes?

[*]The stripe cache size formula reduces the read and write performance of my array. I've checked the kernel documentation for MD but it doesn't give much information. For sequential read/write throughput I'm better off setting it to 32768. Are there any obvious disadvantages to setting it to the maximum value?

[*]What is 'set max sectors kb' about and is there a reason to not increase it above 512 kB (since you have a specific FORCECHUNKSIZE variable for that)?

[/LIST]

---

### Post by fackamato on 2011-07-31
I modified the script a little;

* More verbose
* "Fix" indent

Tested on a 7 drive RAID6 array (ext4), output:

```
 $ sudo ./tuneraid.sh
Using 2 parity devices (raid6)
Found 7 devices with 0 spares
read ahead size per device: 4480 blocks (2240kb)
read ahead size of array: 31360 blocks (15680kb)
stripe cache size of devices: 560 pages (2240kb)
Setting max sectors KB to match chunk size
Set max sectors KB to 64 on h
Set max sectors KB to 64 on g
Set max sectors KB to 64 on f
Set max sectors KB to 64 on e
Set max sectors KB to 64 on d
Set max sectors KB to 64 on b
Set max sectors KB to 64 on c
Setting NCQ queue depth to 31 on h
Setting NCQ queue depth to 31 on g
Setting NCQ queue depth to 31 on f
Setting NCQ queue depth to 31 on e
Setting NCQ queue depth to 31 on d
Setting NCQ queue depth to 31 on b
Setting NCQ queue depth to 31 on c
setting stride to 16 blocks (64 KB)
setting stripe-width to 80 blocks (320 KB)
tune2fs -E stride=16,stripe-width=80 /dev/md
```

The script:

```
#!/bin/bash
###############################################################################
#  simple script to set some parameters to increase performance on a mdadm
# raid5 or raid6. Ajust the ## parameters ##-section to your system!
#
#  WARNING: depending on stripesize and the number of devices the array might
# use QUITE a lot of memory after optimization!
#
#  27may2010 by Alexander Peganz
#  31jul211 modified by Mathias B
###############################################################################


## parameters ##
MDDEV=md0		# e.g. md51 for /dev/md51
CHUNKSIZE=64		# in KB
BLOCKSIZE=4		# of file system in KB
NCQ=enable		# disable, enable. ath. else keeps current setting
NCQDEPTH=31		# 31 should work for almost anyone
FORCECHUNKSIZE=true	# force max sectors kb to chunk size > 512
DOTUNEFS=true		# run tune2fs, ONLY SET TO true IF YOU USE EXT[34]
RAIDLEVEL=raid6		# raid5, raid6


## code ##
# test for priviledges
if [ "$(whoami)" != 'root' ]; then
	echo $(date): Need to be root >> /#tuneraid.log
	exit 1
fi

# set number of parity devices
NUMPARITY=1
[[ $RAIDLEVEL == "raid6" ]] && NUMPARITY=2
echo "Using $NUMPARITY parity devices ($RAIDLEVEL)"
# get all devices
DEVSTR="`grep \"^$MDDEV : \" /proc/mdstat` eol"
while \
 [ -z "`expr match \"$DEVSTR\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\? \)'`" ]
do
	DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done

# get active devices list and spares list
DEVS=""
SPAREDEVS=""
while [ "$DEVSTR" != "eol" ]; do
	CURDEV="`echo $DEVSTR|cut -f -1 -d \ `"
	if [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\)'`" ]; then
		SPAREDEVS="$SPAREDEVS${CURDEV:2:1}"
	elif [ -n "`expr match \"$CURDEV\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\)'`" ]; then
		DEVS="$DEVS${CURDEV:2:1}"
	fi
	DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done

NUMDEVS=${#DEVS}
NUMSPAREDEVS=${#SPAREDEVS}

# test if number of devices makes sense
if [ ${#DEVS} -lt $[1+$NUMPARITY] ]; then
	echo $(date): Need more devices >> /#tuneraid.log
	exit 1
fi

echo "Found $NUMDEVS devices with $NUMSPAREDEVS spares"

# set read ahead
RASIZE=$[$NUMDEVS*($NUMDEVS-$NUMPARITY)*2*$CHUNKSIZE]   # in 512b blocks
echo read ahead size per device: $RASIZE blocks \($[$RASIZE/2]kb\)
MDRASIZE=$[$RASIZE*$NUMDEVS]
echo read ahead size of array: $MDRASIZE blocks \($[$MDRASIZE/2]kb\)
blockdev --setra $RASIZE /dev/sd[$DEVS]
#blockdev --setra $RASIZE /dev/sd[$SPAREDEVS]
blockdev --setra $MDRASIZE /dev/$MDDEV

# set stripe cache size
STRCACHESIZE=$[$RASIZE/8]                               # in pages per device
echo stripe cache size of devices: $STRCACHESIZE pages \($[$STRCACHESIZE*4]kb\)
echo $STRCACHESIZE > /sys/block/$MDDEV/md/stripe_cache_size

# set max sectors kb
DEVINDEX=0
MINMAXHWSECKB=$(cat /sys/block/sd${DEVS:0:1}/queue/max_hw_sectors_kb)
until [ $DEVINDEX -ge $NUMDEVS ]; do
	DEVLETTER=${DEVS:$DEVINDEX:1}
	MAXHWSECKB=$(cat /sys/block/sd$DEVLETTER/queue/max_hw_sectors_kb)
	if [ $MAXHWSECKB -lt $MINMAXHWSECKB ]; then
		MINMAXHWSECKB=$MAXHWSECKB
	fi
	DEVINDEX=$[$DEVINDEX+1]
done
if [ $CHUNKSIZE -le $MINMAXHWSECKB ] && ( [ $CHUNKSIZE -le 512 ] || [[ $FORCECHUNKSIZE == "true" ]] ); then
	echo Setting max sectors KB to match chunk size
	DEVINDEX=0
	until [ $DEVINDEX -ge $NUMDEVS ]; do
		DEVLETTER=${DEVS:$DEVINDEX:1}
		echo "Set max sectors KB to $CHUNKSIZE on $DEVLETTER"
		echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
		DEVINDEX=$[$DEVINDEX+1]
	done
	DEVINDEX=0
	until [ $DEVINDEX -ge $NUMSPAREDEVS ]; do
		DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
		echo "Set max sectors KB to $CHUNKSIZE on $DEVLETTER"
		echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
		DEVINDEX=$[$DEVINDEX+1]
	done
fi

# enable/disable NCQ
DEVINDEX=0
if [[ $NCQ == "enable" ]] || [[ $NCQ == "disable" ]]; then
	if [[ $NCQ == "disable" ]]; then
		NCQDEPTH=1
	fi
	until [ $DEVINDEX -ge $NUMDEVS ]; do
		DEVLETTER=${DEVS:$DEVINDEX:1}
		echo Setting NCQ queue depth to $NCQDEPTH on $DEVLETTER
		echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
		DEVINDEX=$[$DEVINDEX+1]
	done
	DEVINDEX=0
	until [ $DEVINDEX -ge $NUMSPAREDEVS ]; do
		DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
		echo Setting NCQ queue depth to $NCQDEPTH on $DEVLETTER
		echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
		DEVINDEX=$[$DEVINDEX+1]
	done
fi

# tune2fs
if [[ $DOTUNEFS == "true" ]]; then
	STRIDE=$[$CHUNKSIZE/$BLOCKSIZE]
	STRWIDTH=$[$CHUNKSIZE/$BLOCKSIZE*($NUMDEVS-$NUMPARITY)]
	echo setting stride to $STRIDE blocks \($CHUNKSIZE KB\)
	echo setting stripe-width to $STRWIDTH blocks \($[$STRWIDTH*$BLOCKSIZE] KB\)
	echo tune2fs -E stride=$STRIDE,stripe-width=$STRWIDTH /dev/$MDDEV
fi

# exit
echo $(date): Success >> /#tuneraid.log
exit 0

```

---

### Post by nipennem on 2011-07-31
fackamato, i noticed you are using a chunk size of 64k. How did you pick the chunk size for your array?

---

### Post by fackamato on 2011-07-31
> **nipennem said:**
> fackamato, i noticed you are using a chunk size of 64k. How did you pick the chunk size for your array?

I actually don't remember. This is running in an Atom board so I can't check the max performance anyway. It only hosts large ( >1GB) files, 3GB RAM.

---

### Post by jchung on 2011-09-11
Just wanted to revive this thread... I recently started using a software raid on my Ubuntu server and came across this thread to help tune an mdadm raid array.

Anyway.... I've rewritten the tuning script to be a bit more automated. I've only tested on my own system, so there might be bugs for others for situations that I haven't accounted for.

So... here are some differences:

1. auto detect the mdadm configured raid arrays
2. auto detect NCQ capable disks
3. does not currently tune the filesystems, but does echo out the command for tuning the filesystem
4. auto detect chunk size of array
5. auto detect raid level
6. Minor modification of stripe cache size calculation


Here is the script (obviously, same caveats as before, run at your own risk, modify as required) - 
```

#!/bin/sh

# NEED FOLLOWING UTILS
# -- hdparm
# -- lvm


# Add VM tuning stuff?
#vm.swappiness = 1               # set low to limit swapping
#vm.vfs_cache_pressure = 50      # set lower to cache more inodes / dir entries
#vm.dirty_background_ratio = 5   # set low on systems with lots of memory
                                 # Too HIGH on systems with lots of memory 
                                 # means huge page flushes which will hurt IO performance
#vm.dirty_ratio = 10             # set low on systems with lots of memory


# DEFAULTS
BLOCKSIZE=4		# of filesystem in KB (should I determine?)
FORCECHUNKSIZE=true	# force max  sectors KB to chunk size > 512
TUNEFS=true		# run tune2fs on filesystem if ext[3|4]
SCHEDULER=deadline      # cfq / noop / anticipatory / deadline
NR_REQUESTS=64          # NR REQUESTS
NCQDEPTH=31             # NCQ DEPTH
MDSPEEDLIMIT=200000     # Array speed_limit_max in KB/s



# ----------------------------------------------------------------------
# 
# BODY
# 
# ----------------------------------------------------------------------

# determine list of arrays
mdadm -Es | grep ARRAY | while read x1 x2 x3 x4 x5
do
    # INIT VARIABLES
    RAIDLEVEL=0
    NDEVICES=0
    CHUNKSIZE=0
    ARRAYSTATUS=0
    DISKS=""
    SPARES=""
    NUMDISKS=0
    NUMSPARES=0
    NUMPARITY=0
    NCQ=0
    NUMNCQDISKS=0

    RASIZE=0
    MDRASIZE=0
    STRIPECACHESIZE=0
    MINMAXHWSECKB=999999999

    STRIDE=0
    STRIPEWIDTH=0


    # GET DETAILS OF ARRAY
    ARRAY=`basename $x2`
    RAIDLEVEL=`echo $x3 | cut -d'=' -f2`

    case $RAIDLEVEL in
	"raid6") NUMPARITY=2 ;;
	"raid5") NUMPARITY=1 ;;
	"raid4") NUMPARITY=1 ;;
	"raid3") NUMPARITY=1 ;;
	"raid1") NUMPARITY=1 ;;
	"raid0") NUMPARITY=0 ;;
	*) 
	    echo "Unknown RAID level"
    esac

    echo ""
    echo "======================================================================"
    echo "FOUND ARRAY - $ARRAY / $RAIDLEVEL"
    CHUNKSIZE=`mdadm --detail /dev/$ARRAY | grep 'Chunk Size' | tr -d A-Za-z':'[:blank:]`

    echo "-- Chunk Size = $CHUNKSIZE KB"

    FOO1=`grep "$ARRAY : " /proc/mdstat`
    ARRAYSTATUS=`echo $FOO1 | cut -f 3`


    # GET LIST OF DISKS IN ARRAY
    echo ""
    echo "Getting active devices and spares list"
    for DISK in `echo $FOO1 | cut -f 5- -d \ `
    do
	LETTER=`echo $DISK | cut -c 1-3`
	echo $DISK | grep '(S)'
        RC=$?
	if [ $RC -gt 0 ]
	then
	    echo "-- $DISK - Active"
	    DISKS="$DISKS $LETTER"
	    NUMDISKS=$((NUMDISKS+1))
	else
	    echo "-- $DISK - Spare"
	    SPARES="$SPARES $LETTER"
	    NUMSPARES=$((NUMDISKS+1))
	fi
    done
    echo ""
    echo "Active Disks ($NUMDISKS) - $DISKS"
    echo "Spares Disks ($NUMSPARES) - $SPARES"

        
    # DETERMINE SETTINGS
    RASIZE=$(($NUMDISKS*($NUMDISKS-$NUMPARITY)*2*$CHUNKSIZE))  # Disk read ahead in 512byte blocks
    MDRASIZE=$(($RASIZE*$NUMDISKS))                            # Array read ahead in 512byte blocks
    STRIPECACHESIZE=$(($RASIZE*2/8))                           # in pages per device


    for DISK in $DISKS $SPARES
    do
	# check max_hw_sectors_kb
	FOO1=`cat /sys/block/$DISK/queue/max_hw_sectors_kb | awk '{print $1}'`
	if [ $FOO1 -lt $MINMAXHWSECKB ]
	then
	    MINMAXHWSECKB=$FOO1
	fi

	# check NCQ
	hdparm -I /dev/$DISK | grep NCQ >> /dev/null
	if [ $? -eq 0 ]
	then
	    NUMNCQDISKS=$((NUMNCQDISKS+1))
	fi
    done

    if [ $CHUNKSIZE -le $MINMAXHWSECKB ]
    then
	MINMAXHWSECKB=$CHUNKSIZE
    fi

    if [ $NUMNCQDISKS -lt $NUMDISKS ]
    then
	NCQDEPTH=1
	echo "WARNING! ONLY $NUMNCQDISKS DISKS ARE NCQ CAPABLE!"
    fi

    echo ""
    echo "TUNED SETTINGS"
    echo "-- DISK READ AHEAD  = $RASIZE blocks"
    echo "-- ARRAY READ AHEAD = $MDRASIZE blocks"
    echo "-- STRIPE CACHE     = $STRIPECACHESIZE pages"
    echo "-- MAX SECTORS KB   = $MINMAXHWSECKB KB"
    echo "-- NCQ DEPTH        = $NCQDEPTH"

    # TUNE ARRAY
    echo ""
    echo "TUNING ARRAY"
    blockdev --setra $MDRASIZE /dev/$ARRAY
    echo "-- $ARRAY read ahead set to $MDRASIZE blocks"

    echo "$STRIPECACHESIZE" > /sys/block/$ARRAY/md/stripe_cache_size
    echo "-- $ARRAY stripe_cache_size set to $STRIPECACHESIZE pages"

    echo $MDSPEEDLIMIT > /proc/sys/dev/raid/speed_limit_max
    echo "-- $ARRAY speed_limit_max set to $MDSPEEDLIMIT"

    # TUNE DISKS
    echo ""
    echo "TUNING DISKS"
    echo "Settings : "
    echo "        read ahead = $RASIZE blocks"
    echo "    max_sectors_kb = $MINMAXHWSECKB KB"
    echo "         scheduler = $SCHEDULER"
    echo "       nr_requests = $NR_REQUESTS"
    echo "       queue_depth = $NCQDEPTH"

    
    for DISK in $DISKS $SPARES
    do
	echo "-- Tuning $DISK"
	blockdev --setra $RASIZE /dev/$DISK
	echo $MINMAXHWSECKB > /sys/block/$DISK/queue/max_sectors_kb
	echo $SCHEDULER > /sys/block/$DISK/queue/scheduler
	echo $NR_REQUESTS > /sys/block/$DISK/queue/nr_requests
	echo $NCQDEPTH > /sys/block/$DISK/device/queue_depth
    done

    # TUNE ext3/exti4 FILESYSTEMS
    STRIDE=$(($CHUNKSIZE/$BLOCKSIZE))
    STRIPEWIDTH=$(($CHUNKSIZE/$BLOCKSIZE*($NUMDISKS-$NUMPARITY)))
    echo ""
    echo "TUNING FILESYSTEMS"
    echo "For each filesystem on this array, run the following command:"
    echo "  tune2fs -E stride=$STRIDE,stripe-width=$STRIPEWIDTH <filesystem>"
    echo ""

done

```

Something to note... with systems with lots of memory, you'll want to set vm.dirty_background_ratio and vm.dirty_ratio to a fairly low value, otherwise the page flushes will kill your write IO performance. I had mine set fairly high and my write performance would hover around 100MB/s (using dd to write a 20GB file). Setting the values to 5 and 10 respectively on my server (6GB RAM), I now get 180 MB/s with the same command.

My array - 
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdj[7] sdc[0] sde[2] sdf[3] sdd[1] sdg[4] sdi[6] sdh[5]
      5860574208 blocks level 6, 256k chunk, algorithm 2 [8/8] [UUUUUUUU]

```

All disks are 1TB Samsung disks.

Using dd to write a 20GB file -
```

5120+0 records in
5120+0 records out
21474836480 bytes (21 GB) copied, 117.421 s, 183 MB/s

```

Using dd to read in the same 20GB file -
```

5120+0 records in
5120+0 records out
21474836480 bytes (21 GB) copied, 44.612 s, 481 MB/s

```


Considering my numbers were ~ 90MB/s writes and 300MB/s reads when I started, I'm very pleased with the results.

Many thanks to the OP for providing a starting point for me.

Joo

---

### Post by exobuzz on 2011-10-12
> **jchung said:**
> Just wanted to revive this thread... I recently started using a software raid on my Ubuntu server and came across this thread to help tune an mdadm raid array.

I had to tweak your script a bit to get it working on Oneiric (didn't test on natty)

mdadm needed --verbose or it didn't print the raid level.
it also returns a symlink to the md device (in the format /dev/md/1), so I did

ARRAY=`readlink -f $x2`
ARRAY=`basename $ARRAY`

to get the old md1 name

your script sets a much larger readahead than i used. id be interested in seeing benchmarks for random access, as when I previous tested, I decided to use lower values for improved random access.

---

### Post by MikeBuzz on 2011-10-19
> **exobuzz said:**
> I had to tweak your script a bit to get it working on Oneiric (didn't test on natty)

mdadm needed --verbose or it didn't print the raid level.
it also returns a symlink to the md device (in the format /dev/md/1), so I did

ARRAY=`readlink -f $x2`
ARRAY=`basename $ARRAY`

to get the old md1 name

your script sets a much larger readahead than i used. id be interested in seeing benchmarks for random access, as when I previous tested, I decided to use lower values for improved random access.

Would you be able to upload your version, i am using Oneiric with raid5 and would like to see if i can improve the raid performance

Cheers

---

### Post by MikeBuzz on 2011-10-24
> **exobuzz said:**
> I had to tweak your script a bit to get it working on Oneiric (didn't test on natty)

mdadm needed --verbose or it didn't print the raid level.
it also returns a symlink to the md device (in the format /dev/md/1), so I did

ARRAY=`readlink -f $x2`
ARRAY=`basename $ARRAY`

to get the old md1 name

your script sets a much larger readahead than i used. id be interested in seeing benchmarks for random access, as when I previous tested, I decided to use lower values for improved random access.

i have tried editing the script to match the above changes but cant seem to get it to see the device as /dev/md0

any ideas??

---

### Post by drdabbles on 2011-10-28
I rewrote the script a bit to be more consistent, and use one source of data (mdadm). Currently, if you operate against a RAID10 array, you will get an error when the script attempts to modify the stripe_cache_size.

I also cleaned up the code to detect the number of disks in an array. There's no need to have a counter variable since mdadm will tell you the number of disks already.

Finally, I call mdadm once at the beginning of the script to make sure the data I operate on is the same throughout the execution of the script file itself. This is simply in case someone is modifying the array while we're running the script. It won't prevent anything bad from happening, it's just for the script's sanity.

Hope this helps!

BTW: MDSPEEDLIMIT should be modified based on the number of devices you have in your array and how much bandwidth you want a rebuild process to take. 200000 KB/s is basically 2/3 of a single SATA-II drive's maximum bus bandwidth. With large RAID10 pools you can easily hit 1000000 KB/s. Just something to keep in mind.


```

#!/bin/bash

# NEED FOLLOWING UTILS
# -- hdparm
# -- lvm

# Add VM tuning stuff?
#vm.swappiness = 1		# set low to limit swapping
#vm.vfs_cache_pressure = 50	# set lower to cache more inodes / dir entries
#vm.dirty_background_ratio = 5	# set low on systems with lots of memory
				# Too HIGH on systems with lots of memory 
				# means huge page flushes which will hurt IO performance
#vm.dirty_ratio = 10		# set low on systems with lots of memory

# DEFAULTS
BLOCKSIZE=4		# of filesystem in KB (should I determine?)
FORCECHUNKSIZE=true	# force max sectors KB to chunk size > 512
TUNEFS=false		# run tune2fs on filesystem if ext[3|4]
SCHEDULER=deadline	# cfq / noop / anticipatory / deadline
NR_REQUESTS=64		# NR REQUESTS
NCQDEPTH=31		# NCQ DEPTH
MDSPEEDLIMIT=200000	# Array speed_limit_max in KB/s


# ----------------------------------------------------------------------
#
# BODY
#
# ----------------------------------------------------------------------

# determine list of arrays
mdadm -Es | grep ARRAY | while read x1 x2 x3 x4 x5; do
	# INIT VARIABLES
	RAIDLEVEL=0
	NDEVICES=0
	CHUNKSIZE=0
	ARRAYSTATUS=0
	DISKS=""
	SPARES=""
	NUMPARITY=0
	NCQ=0

	RASIZE=0
	MDRASIZE=0
	STRIPECACHESIZE=0
	MINMAXHWSECKB=999999999

	STRIDE=0
	STRIPEWIDTH=0

	# GET DETAILS OF ARRAY
	if [ -L $x2 ]; then
		# Array name is a new-style name. Get the symlink target.
		LINKNAME=`readlink $x2`
		ARRAY="`basename $LINKNAME`"
	else
		# Array name is an old-style name. Use it directly.
		ARRAY="`basename $x2`"
	fi
	MDADMOUTPUT=`mdadm --detail /dev/$ARRAY`
	RAIDLEVEL=`echo "$MDADMOUTPUT" | grep "Raid Level" | cut -d ':' -f 2 | sed 's/\s//g'`
	RAIDDEVICES=`echo "$MDADMOUTPUT" | grep "Raid Devices" | cut -d ':' -f 2`

	case $RAIDLEVEL in
		"raid10")
			NUMPARITY=$(($RAIDDEVICES/2)) ;;
		"raid6")
			NUMPARITY=2 ;;
		"raid5")
			NUMPARITY=1 ;;
		"raid4")
			NUMPARITY=1 ;;
		"raid3")
			NUMPARITY=1 ;;
		"raid1")
			NUMPARITY=1 ;;
		"raid0")
			NUMPARITY=0 ;;
		*)
			echo "Unknown RAID level"
			exit 5 ;;
	esac

	echo ""
	echo "======================================================================"
	echo "FOUND ARRAY - $ARRAY / $RAIDLEVEL / Parity: $NUMPARITY"
	CHUNKSIZE=`echo "$MDADMOUTPUT" | grep 'Chunk Size' | tr -d A-Za-z':'[:blank:]`
	echo "-- Chunk Size = $CHUNKSIZE KB"

	# DETERMINE SETTINGS
	RASIZE=$(($RAIDDEVICES*($RAIDDEVICES-$NUMPARITY)*2*$CHUNKSIZE))	# Disk read ahead in 512byte blocks
	MDRASIZE=$(($RASIZE*$RAIDDEVICES))				# Array read ahead in 512byte blocks
	STRIPECACHESIZE=$(($RASIZE*2/8))				# in pages per device

	# GET LIST OF DISKS IN ARRAY
	echo ""
	echo "Getting active and spare device list"
	while read x1 x2 x3; do
		DSTATUS="$x1"
		DACT="$x2"
		DNAME="$x3"

		if [ "$DSTATUS" = "active" ]; then
			DCURNAME=`basename $DNAME`
			DISKS="$DISKS $DCURNAME"
			echo "-- Active - $DCURNAME"
		elif [ "$DSTATUS" = "spare" ]; then
			if [ "$DNAME" = "" ]; then
				DCURNAME=`basename $DACT`
				SPARES="$SPARES $DCURNAME"
				echo "-- Spare - $DCURNAME"
			else
				DCURNAME=`basename $DNAME`
				DISKS="$DISKS $DCURNAME"
				echo "-- $DACT - $DCURNAME"
			fi
		else
			echo "-- $DSTATUS: $DACT - `basename $DNAME`"
		fi
	done < <(echo "$MDADMOUTPUT" | grep -E "active|spare" | tr -s ' ' | cut -d ' ' -f 6-)
	echo ""
	echo "Active Disks: $DISKS"
	echo "Spares Disks: $SPARES"

	for DISK in $DISKS $SPARES; do
		# check max_hw_sectors_kb
		echo "Checking max_hw_sectors_kb for $DISK"
		FOO1=`cat /sys/block/$DISK/queue/max_hw_sectors_kb | awk '{print $1}'`
		if [ $FOO1 -lt $MINMAXHWSECKB ]; then
			MINMAXHWSECKB=$FOO1
		fi
	done

	if [ $CHUNKSIZE -le $MINMAXHWSECKB ]; then
		MINMAXHWSECKB=$CHUNKSIZE
	fi

	echo ""
	echo "TUNED SETTINGS"
	echo "-- DISK READ AHEAD  = $RASIZE blocks"
	echo "-- ARRAY READ AHEAD = $MDRASIZE blocks"
	echo "-- STRIPE CACHE     = $STRIPECACHESIZE pages"
	echo "-- MAX SECTORS KB   = $MINMAXHWSECKB KB"
	echo "-- NCQ DEPTH        = $NCQDEPTH"

	# TUNE ARRAY
	echo ""
	echo "TUNING ARRAY"
	blockdev --setra $MDRASIZE /dev/$ARRAY
	echo "-- $ARRAY read ahead set to $MDRASIZE blocks"

	echo "$STRIPECACHESIZE" > /sys/block/$ARRAY/md/stripe_cache_size
	echo "-- $ARRAY stripe_cache_size set to $STRIPECACHESIZE pages"

	echo $MDSPEEDLIMIT > /proc/sys/dev/raid/speed_limit_max
	echo "-- $ARRAY speed_limit_max set to $MDSPEEDLIMIT"

	# TUNE DISKS
	echo ""
	echo "TUNING DISKS"
	echo "Settings : "
	echo "  read ahead     = $RASIZE blocks"
	echo "  max_sectors_kb = $MINMAXHWSECKB KB"
	echo "  scheduler      = $SCHEDULER"
	echo "  nr_requests    = $NR_REQUESTS"
	echo "  queue_depth    = $NCQDEPTH"

	for DISK in $DISKS $SPARES; do
		echo "-- Tuning $DISK"
		blockdev --setra $RASIZE /dev/$DISK
		echo $MINMAXHWSECKB > /sys/block/$DISK/queue/max_sectors_kb
		echo $SCHEDULER > /sys/block/$DISK/queue/scheduler
		echo $NR_REQUESTS > /sys/block/$DISK/queue/nr_requests
		echo $NCQDEPTH > /sys/block/$DISK/device/queue_depth
	done

	# TUNE ext3/exti4 FILESYSTEMS
	STRIDE=$(($CHUNKSIZE/$BLOCKSIZE))
	STRIPEWIDTH=$(($CHUNKSIZE/$BLOCKSIZE*($NUMDISKS-$NUMPARITY)))
	echo ""
	echo "TUNING FILESYSTEMS"
	echo "For each filesystem on this array, run the following command:"
	echo "  tune2fs -E stride=$STRIDE,stripe-width=$STRIPEWIDTH <filesystem>"
	echo ""
done


```

---

### Post by MikeBuzz on 2011-10-31
> **drdabbles said:**
> I rewrote the script a bit to be more consistent, and use one source of data (mdadm). Currently, if you operate against a RAID10 array, you will get an error when the script attempts to modify the stripe_cache_size.

I also cleaned up the code to detect the number of disks in an array. There's no need to have a counter variable since mdadm will tell you the number of disks already.

Finally, I call mdadm once at the beginning of the script to make sure the data I operate on is the same throughout the execution of the script file itself. This is simply in case someone is modifying the array while we're running the script. It won't prevent anything bad from happening, it's just for the script's sanity.

Hope this helps!

BTW: MDSPEEDLIMIT should be modified based on the number of devices you have in your array and how much bandwidth you want a rebuild process to take. 200000 KB/s is basically 2/3 of a single SATA-II drive's maximum bus bandwidth. With large RAID10 pools you can easily hit 1000000 KB/s. Just something to keep in mind.


```

#!/bin/bash

# NEED FOLLOWING UTILS
# -- hdparm
# -- lvm

# Add VM tuning stuff?
#vm.swappiness = 1		# set low to limit swapping
#vm.vfs_cache_pressure = 50	# set lower to cache more inodes / dir entries
#vm.dirty_background_ratio = 5	# set low on systems with lots of memory
				# Too HIGH on systems with lots of memory 
				# means huge page flushes which will hurt IO performance
#vm.dirty_ratio = 10		# set low on systems with lots of memory

# DEFAULTS
BLOCKSIZE=4		# of filesystem in KB (should I determine?)
FORCECHUNKSIZE=true	# force max sectors KB to chunk size > 512
TUNEFS=false		# run tune2fs on filesystem if ext[3|4]
SCHEDULER=deadline	# cfq / noop / anticipatory / deadline
NR_REQUESTS=64		# NR REQUESTS
NCQDEPTH=31		# NCQ DEPTH
MDSPEEDLIMIT=200000	# Array speed_limit_max in KB/s


# ----------------------------------------------------------------------
#
# BODY
#
# ----------------------------------------------------------------------

# determine list of arrays
mdadm -Es | grep ARRAY | while read x1 x2 x3 x4 x5; do
	# INIT VARIABLES
	RAIDLEVEL=0
	NDEVICES=0
	CHUNKSIZE=0
	ARRAYSTATUS=0
	DISKS=""
	SPARES=""
	NUMPARITY=0
	NCQ=0

	RASIZE=0
	MDRASIZE=0
	STRIPECACHESIZE=0
	MINMAXHWSECKB=999999999

	STRIDE=0
	STRIPEWIDTH=0

	# GET DETAILS OF ARRAY
	if [ -L $x2 ]; then
		# Array name is a new-style name. Get the symlink target.
		LINKNAME=`readlink $x2`
		ARRAY="`basename $LINKNAME`"
	else
		# Array name is an old-style name. Use it directly.
		ARRAY="`basename $x2`"
	fi
	MDADMOUTPUT=`mdadm --detail /dev/$ARRAY`
	RAIDLEVEL=`echo "$MDADMOUTPUT" | grep "Raid Level" | cut -d ':' -f 2 | sed 's/\s//g'`
	RAIDDEVICES=`echo "$MDADMOUTPUT" | grep "Raid Devices" | cut -d ':' -f 2`

	case $RAIDLEVEL in
		"raid10")
			NUMPARITY=$(($RAIDDEVICES/2)) ;;
		"raid6")
			NUMPARITY=2 ;;
		"raid5")
			NUMPARITY=1 ;;
		"raid4")
			NUMPARITY=1 ;;
		"raid3")
			NUMPARITY=1 ;;
		"raid1")
			NUMPARITY=1 ;;
		"raid0")
			NUMPARITY=0 ;;
		*)
			echo "Unknown RAID level"
			exit 5 ;;
	esac

	echo ""
	echo "======================================================================"
	echo "FOUND ARRAY - $ARRAY / $RAIDLEVEL / Parity: $NUMPARITY"
	CHUNKSIZE=`echo "$MDADMOUTPUT" | grep 'Chunk Size' | tr -d A-Za-z':'[:blank:]`
	echo "-- Chunk Size = $CHUNKSIZE KB"

	# DETERMINE SETTINGS
	RASIZE=$(($RAIDDEVICES*($RAIDDEVICES-$NUMPARITY)*2*$CHUNKSIZE))	# Disk read ahead in 512byte blocks
	MDRASIZE=$(($RASIZE*$RAIDDEVICES))				# Array read ahead in 512byte blocks
	STRIPECACHESIZE=$(($RASIZE*2/8))				# in pages per device

	# GET LIST OF DISKS IN ARRAY
	echo ""
	echo "Getting active and spare device list"
	while read x1 x2 x3; do
		DSTATUS="$x1"
		DACT="$x2"
		DNAME="$x3"

		if [ "$DSTATUS" = "active" ]; then
			DCURNAME=`basename $DNAME`
			DISKS="$DISKS $DCURNAME"
			echo "-- Active - $DCURNAME"
		elif [ "$DSTATUS" = "spare" ]; then
			if [ "$DNAME" = "" ]; then
				DCURNAME=`basename $DACT`
				SPARES="$SPARES $DCURNAME"
				echo "-- Spare - $DCURNAME"
			else
				DCURNAME=`basename $DNAME`
				DISKS="$DISKS $DCURNAME"
				echo "-- $DACT - $DCURNAME"
			fi
		else
			echo "-- $DSTATUS: $DACT - `basename $DNAME`"
		fi
	done < <(echo "$MDADMOUTPUT" | grep -E "active|spare" | tr -s ' ' | cut -d ' ' -f 6-)
	echo ""
	echo "Active Disks: $DISKS"
	echo "Spares Disks: $SPARES"

	for DISK in $DISKS $SPARES; do
		# check max_hw_sectors_kb
		echo "Checking max_hw_sectors_kb for $DISK"
		FOO1=`cat /sys/block/$DISK/queue/max_hw_sectors_kb | awk '{print $1}'`
		if [ $FOO1 -lt $MINMAXHWSECKB ]; then
			MINMAXHWSECKB=$FOO1
		fi
	done

	if [ $CHUNKSIZE -le $MINMAXHWSECKB ]; then
		MINMAXHWSECKB=$CHUNKSIZE
	fi

	echo ""
	echo "TUNED SETTINGS"
	echo "-- DISK READ AHEAD  = $RASIZE blocks"
	echo "-- ARRAY READ AHEAD = $MDRASIZE blocks"
	echo "-- STRIPE CACHE     = $STRIPECACHESIZE pages"
	echo "-- MAX SECTORS KB   = $MINMAXHWSECKB KB"
	echo "-- NCQ DEPTH        = $NCQDEPTH"

	# TUNE ARRAY
	echo ""
	echo "TUNING ARRAY"
	blockdev --setra $MDRASIZE /dev/$ARRAY
	echo "-- $ARRAY read ahead set to $MDRASIZE blocks"

	echo "$STRIPECACHESIZE" > /sys/block/$ARRAY/md/stripe_cache_size
	echo "-- $ARRAY stripe_cache_size set to $STRIPECACHESIZE pages"

	echo $MDSPEEDLIMIT > /proc/sys/dev/raid/speed_limit_max
	echo "-- $ARRAY speed_limit_max set to $MDSPEEDLIMIT"

	# TUNE DISKS
	echo ""
	echo "TUNING DISKS"
	echo "Settings : "
	echo "  read ahead     = $RASIZE blocks"
	echo "  max_sectors_kb = $MINMAXHWSECKB KB"
	echo "  scheduler      = $SCHEDULER"
	echo "  nr_requests    = $NR_REQUESTS"
	echo "  queue_depth    = $NCQDEPTH"

	for DISK in $DISKS $SPARES; do
		echo "-- Tuning $DISK"
		blockdev --setra $RASIZE /dev/$DISK
		echo $MINMAXHWSECKB > /sys/block/$DISK/queue/max_sectors_kb
		echo $SCHEDULER > /sys/block/$DISK/queue/scheduler
		echo $NR_REQUESTS > /sys/block/$DISK/queue/nr_requests
		echo $NCQDEPTH > /sys/block/$DISK/device/queue_depth
	done

	# TUNE ext3/exti4 FILESYSTEMS
	STRIDE=$(($CHUNKSIZE/$BLOCKSIZE))
	STRIPEWIDTH=$(($CHUNKSIZE/$BLOCKSIZE*($NUMDISKS-$NUMPARITY)))
	echo ""
	echo "TUNING FILESYSTEMS"
	echo "For each filesystem on this array, run the following command:"
	echo "  tune2fs -E stride=$STRIDE,stripe-width=$STRIPEWIDTH <filesystem>"
	echo ""
done


```

Tested the above on Oneiric

mdadm: cannot open /dev/0: No such file or directory
Unknown RAID level

---

### Post by apeganz on 2011-11-08
wow, I stumbled on my old post here purely by accident and I'm stunned to see what has happend since!

I guess by now you know more about the script then I do (had totally forgotten it, still works away in my lucid server untouched since week one)

Sorry I never replied to any questions, after the first edit I kind of abbandoned it and I'm all but a regular viewer of this forums :(



I'll try to help out with some stuff I still remember:

> Chunk size and block size of arrayAfair I only knew those values because I specified them when creating the array. I guess there is a way to get them from the array, but idkh. jchung posted a rewritten variant with > 4. auto detect chunk size of array> RASIZE, MDRASIZE, omminous 512b blocks commentThe goal when calculating this numbers was to read ahead the same amount of chunks on all disks in the array. With this formula the following happens:
- Something/one wants to read sth from the array
- The stuff to be read is distributed among the disks, each disk holding consecutive pieces of data of size CHUNKSIZE. The first NUMDEVS-NUMPARITY disks hold chunks containing actual data, the next NUMPARITY disks hold chunks containing parity data (well, that's a simplification, but I hope it's clear enough so you hear what I'm trying to say)
- if I want to read the same ammount from all disks at the same time I have to read N*number of disks*CHUNKSIZE kbyte
- since I'm not sure if parity chunks are skipped when reading, I multiply NUMDEVS with NUMDEVS-NUMPARITY for my number of disks, so the formula works for both cases. Side effect: generally higher read ahead size which should translate into higher performance, and it's even somewhat deterministic ;)
- factor of two is in there because now I have kbyte and in "blockdev --setra N" the N is in 512 byte sectors according to it's man page, I guess that is independent from the actual logical, actual physical and reported physical block size of the drive (mine are 4k physical, 512b logical sector drives reporting as 512b physical, 512b logical)

> stripe cache sizeAfair the higher the stripe cache size the more RAM is needed to cache. But idk if I don't mix up stuff I read about read ahead and stripe cache size right now, it's been a while after all. More cache should always be faster.

> force max sectors kbI think I read that something bad can happen if this is set above 512kb while scouring mailing lists back then. But for the life of me, that's all I can remember.



by the way, when I asked for help to create the code to get the neccessary info out of the mdadm output, geirha (who helped me a lot. I just realized I never propperly credited him. Sorry geirha!) suggested to me that I should try to improve on my bash skills, since the script uses some old sh-style stuff that is not as good as the equivalents available in bash. If you should continue to improve on the script, maybe you would want to use his advice ([http://ubuntuforums.org/showthread.php?t=1510176](http://ubuntuforums.org/showthread.php?t=1510176)). He later also suggested [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls) to me as a good starting point.

Well, that's it I guess, hope I could help! I'll try to remember to check back in over the next few days, but I've got a lot of university stuff going on right now, so I can't promise anything unfortunately.

regards,
alex

---

### Post by CrazyMike on 2011-11-11
I just tried this script by drdabbles and had the same failure as MikeBuzz.  I was able to get the first part to work by manually making it look at /dev/md0 instead of dev/md/0 (which doesn't exist).

Also, my array is on /dev/sdb1, /dev/sdc1, and /dev/sdd1 . I had to manually change DISKS to sdb,sdc, and sdd as the original script was looking at sdb1,sdc1,sdd1 and the path doesnt exist. 

For example, this path in the script 
/sys/block/$DISK/queue/max_hw_sectors_kb needs "sdb" not "sdb1"

I was able to make it run by doing the above, however, it didn't really improve my read performance.  ~120 mb/sec now it is ~114 mb/sec.  My write speed did improve from ~70mb/sec to ~107mb/sec.

Thats my feedback for now.  I'm pretty new to running scripts, so I'm not sure a more elegant way to fix this...

---

### Post by nosebreaker on 2011-11-23
I had used the original script, not this newer one.  I am using CentOS 5.5, but the script worked fine aside from modifying it to use sdx3 instead of sdx1.

For an update, I added 3 more 2tb drives into my array (same brand, same specs, but the "green" label drives instead).  I basically followed this guide:
[http://allintech.info/2008/06/mdadm-growing-raid5-array-ubuntu/](http://allintech.info/2008/06/mdadm-growing-raid5-array-ubuntu/)

Basically you create new partitions on the drive the same size as the others, mark them as type raid, then add them into the array, grow the filesystem, then finally resize the filesystem to use the new space.

I did not have to unmount the filesystem, resize2fs now works with online drives.  It took about 50 hours to grow the filesystem (due to its large size), and apparently about 16 hours to resize2fs.  Now I have 6 2tb drives in total, for a total usable space of 9.3TB.  resize2fs did see them as 4K block sizes.

When it was done, read speeds were still ~160MB/s as before, but write speeds were abysmally slow (12.5MB/s).  I edited the tune_raid.sh script to turn off apm on these new drives, but it looks like they don't support this command (they give an error only on the new drives).  To get proper write speeds all I had to do was reboot the box, and then read speeds also went up.  Just re-running the tune_raid.sh didn't seem to help for some reason.

Now with 6 drives in raid5 I get:
Read speed: 330MB/s
Write speed: 125MB/s

---

### Post by fackamato on 2011-11-23
> **nosebreaker said:**
> I had used the original script, not this newer one.  I am using CentOS 5.5, but the script worked fine aside from modifying it to use sdx3 instead of sdx1.

For an update, I added 3 more 2tb drives into my array (same brand, same specs, but the "green" label drives instead).  I basically followed this guide:
[http://allintech.info/2008/06/mdadm-growing-raid5-array-ubuntu/](http://allintech.info/2008/06/mdadm-growing-raid5-array-ubuntu/)

Basically you create new partitions on the drive the same size as the others, mark them as type raid, then add them into the array, grow the filesystem, then finally resize the filesystem to use the new space.

I did not have to unmount the filesystem, resize2fs now works with online drives.  It took about 50 hours to grow the filesystem (due to its large size), and apparently about 16 hours to resize2fs.  Now I have 6 2tb drives in total, for a total usable space of 9.3TB.  resize2fs did see them as 4K block sizes.

When it was done, read speeds were still ~160MB/s as before, but write speeds were abysmally slow (12.5MB/s).  I edited the tune_raid.sh script to turn off apm on these new drives, but it looks like they don't support this command (they give an error only on the new drives).  To get proper write speeds all I had to do was reboot the box, and then read speeds also went up.  Just re-running the tune_raid.sh didn't seem to help for some reason.

Now with 6 drives in raid5 I get:
Read speed: 330MB/s
Write speed: 125MB/s

I'm guessing the writes are low because of the CPU, what processor is in that system?

---

### Post by drdabbles on 2011-11-23
Sorry everyone! The modifications I made to the script read the device names from the mdadm tool, so I'm not too sure why it would read bad device names for some of you. I'd be interested in seeing the output of mdadm when listing devices.

I also modified the script to parse the raw disk device names without the partition numbers, but my NAS's boot device just died on me a few days ago. Once I get it running again, I'll post the new version here. Again, sorry everyone!

---

### Post by MikeBuzz on 2011-12-02
mdadm -Es | grep ARRAY

ARRAY /dev/md/0 metadata=1.0 UUID=c58c0830:6229119d:29f6c531:0bf0efaf name=BlueBolt:0

---

### Post by alfonso78 on 2012-01-18
> **apeganz said:**
> edit: new version of the script, you now have to do less adjustments. should be pretty save to run on almost any system. regards, alex

I just wrote a script to improve my mdadm-raid's performance and felt like sharing. Maybe someone else can use it or get some inspiration from it.

Happy tuning,
Alex

PS: do NOT just run it, depending on your configuration it might seriously screw up your system if you don't alter it accordingly!


Hi,

I did a bit of modification to the original script to make it a bit more automatic and more usable for newbies like me.
there is still some stuff that I don't understand but I think it's a bit more readable now.

[SIZE="4"][COLOR="Red"]Use it at your own risk![/COLOR][/SIZE]

```
#!/bin/bash
###############################################################################
#  simple script to set some parameters to increase performance on a mdadm
# raid5 or raid6. Ajust the ## parameters ##-section to your system!
#
#  WARNING: depending on stripesize and the number of devices the array might
# use QUITE a lot of memory after optimization!
#
#  27may2010 by Alexander Peganz
#  18/01/2012 Alfonso made the script more verbose 
###############################################################################

# use bash -x scriptname.sh to debug

## parameters ##
LOGFILE=/tmp/tune_raid.log      # just a log file
BLOCKSIZE=4                     # of file system in kb
                                # this is a parameter of mkfs when you created your filesystem
                                # e.g. mkfs.ext4 -b 4096 -E stride=16,stripe-width=32 /dev/md0
                                # if you don't know your block size, run dumpe2fs -h /dev/md0 | grep "Block size"
NCQ=disable                     # disable, enable. ath. else keeps current setting
                                # to be honest I couldn't find any clear and short article
                                # on NCQ but I saw all my disks are already disabled
                                # so I'll keep this option disable
NCQDEPTH=31                     # 31 should work for almost anyone
                                # you only have to care about this if you want to enable NCQ
FORCECHUNKSIZE=true             # force max sectors kb to chunk size > 512
                                # I tried to figure out what this is... but I don't know...
DOTUNEFS=false                  # run tune2fs, ONLY SET TO true IF YOU USE EXT[34]
EXECUTE=false                   # if "true", run actual commands. Otherwise only inform you


echo check $LOGFILE for messages in case of error.

## code ##
# test for priviledges
if [ "$(whoami)" != 'root' ]
then
  echo $(date): Need to be root >> $LOGFILE
  exit 1
fi

if [ $EXECUTE == "true" ]
then
  echo
  echo "************************************************"
  echo "You are about to make real changes to the system"
  echo "************************************************"
  echo
  read -p "Press [Enter] to continue or Ctrl-C to abort"
fi

# find out which one is your md
# note that the script only works for one md. If you have more than one 
# just uncomment the line below and type something like MDDEV=md0
MDDEV="`cat /proc/mdstat | grep md | head -1 | awk '{print $1}'`"
# MDDEV=md0

if [ -z "$MDDEV" ]
then
  echo $(date): Something wrong, I can\'t find any md >> $LOGFILE
  exit 1
fi

#
# find out which RAID level
#
RAIDLEVEL="`mdadm --detail /dev/$MDDEV | grep raid | tr " " "\n" | grep raid`"
if [ -z "$RAIDLEVEL" ]
then
  echo $(date): Something wrong, I can\'t find which raidlevel you are using >> $LOGFILE
  exit 1
fi
if [ $RAIDLEVEL != "raid5" ] && [ $RAIDLEVEL != "raid6" ]
then
  echo $(date): Something wrong, this script only works for raid5 and raid6 >> $LOGFILE
  exit 1
fi

#
# find out your chunk size
#
# this expression takes the output of /proc/mdstat
# then takes the line with chunk
# then cuts it in many lines
# then takes the line with chunk
# then prints the first word
# then removes all the letters and keeps the number
# CAREFUL! CHECK IF YOUR /proc/mdstat REPORT CHUNK IN A DIFFERENT UNIT (e.g. mega instead of kilo)
# this will BREAK the script
CHUNKSIZE="`cat /proc/mdstat | grep chunk | tr "," "\n" | grep chunk | awk '{print $1}' | tr -d [a-z]`"

# set number of parity devices
NUMPARITY=1
if [[ $RAIDLEVEL == "raid6" ]]
then
  NUMPARITY=2
fi

#
# get the letter of all NON spare devices from cat /proc/mdstat
#
# this expression takes the output of /proc/mdstat
# then takes the line of our md
# then changes spaces into new lines
# then takes only lines starting with sd
# then takes the lines without (S) at the end of the string (which are the NON spare disks)
# then take the 3rd character (a for sda1, etc)
# and then remove new lines to make a single string
DEVS="`cat /proc/mdstat | grep $MDDEV | tr " " "\n" | grep '^sd' | grep -v \(S\)$ | awk '{print substr($0,3,1)}' | tr -d "\n"`"

#
# get the letter of all spare devices from cat /proc/mdstat
#
# this expression takes the output of /proc/mdstat
# then takes the line of our md
# then changes spaces into new lines
# then takes only lines starting with sd
# then takes the lines with (S) at the end of the string (which are the spare disks)
# then take the 3rd character (a for sda1, etc)
# and then remove new lines to make a single string
SPAREDEVS="`cat /proc/mdstat | grep $MDDEV | tr " " "\n" | grep '^sd' | grep \(S\)$ | awk '{print substr($0,3,1)}' | tr -d "\n"`"

NUMDEVS=${#DEVS}
NUMSPAREDEVS=${#SPAREDEVS}

# test if number of devices makes sense
if [ ${#DEVS} -lt $[1+$NUMPARITY] ]
then
  echo $(date): Need more devices >> $LOGFILE
  exit 1
fi

# set read ahead
RASIZE=$[$NUMDEVS*($NUMDEVS-$NUMPARITY)*2*$CHUNKSIZE]   # in 512b blocks
echo suggested read ahead size per device: $RASIZE blocks \($[$RASIZE/2]kb\)
MDRASIZE=$[$RASIZE*$NUMDEVS]
echo suggested read ahead size of array: $MDRASIZE blocks \($[$MDRASIZE/2]kb\)
echo RUN blockdev --setra $RASIZE /dev/sd[$DEVS]
echo your current value for readahead is `blockdev --getra /dev/sd[$DEVS]`
if [ $EXECUTE == "true" ]
then
  blockdev --setra $RASIZE /dev/sd[$DEVS]
fi
if [ $NUMSPAREDEVS -gt 0 ]
then
  echo RUN blockdev --setra $RASIZE /dev/sd[$SPAREDEVS]
  echo your current value for readahead is `blockdev --getra /dev/sd[$SPAREDEVS]`
  if [ $EXECUTE == "true" ]
  then
    blockdev --setra $RASIZE /dev/sd[$SPAREDEVS]
  fi
fi
echo RUN blockdev --setra $MDRASIZE /dev/$MDDEV
echo your current value for readahead is `blockdev --getra /dev/$MDDEV`
  if [ $EXECUTE == "true" ]
  then
    blockdev --setra $MDRASIZE /dev/$MDDEV
  fi

# set stripe cache size
STRCACHESIZE=$[$RASIZE/8]                               # in pages per device
echo suggested stripe cache size of devices: $STRCACHESIZE pages \($[$STRCACHESIZE*4]kb\)
echo RUN echo $STRCACHESIZE \> /sys/block/$MDDEV/md/stripe_cache_size
echo current value of /sys/block/$MDDEV/md/stripe_cache_size is `cat /sys/block/$MDDEV/md/stripe_cache_size`
if [ $EXECUTE == "true" ]
then
  echo $STRCACHESIZE > /sys/block/$MDDEV/md/stripe_cache_size
fi

# set max sectors kb
DEVINDEX=0
MINMAXHWSECKB=$(cat /sys/block/sd${DEVS:0:1}/queue/max_hw_sectors_kb)
until [ $DEVINDEX -ge $NUMDEVS ]
do
  DEVLETTER=${DEVS:$DEVINDEX:1}
  MAXHWSECKB=$(cat /sys/block/sd$DEVLETTER/queue/max_hw_sectors_kb)
  if [ $MAXHWSECKB -lt $MINMAXHWSECKB ]
  then
    MINMAXHWSECKB=$MAXHWSECKB
  fi
  DEVINDEX=$[$DEVINDEX+1]
done
if [ $CHUNKSIZE -le $MINMAXHWSECKB ] &&
  ( [ $CHUNKSIZE -le 512 ] || [[ $FORCECHUNKSIZE == "true" ]] )
then
  echo setting max sectors kb to match chunk size
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMDEVS ]
  do
    DEVLETTER=${DEVS:$DEVINDEX:1}
    echo RUN echo $CHUNKSIZE \> /sys/block/sd$DEVLETTER/queue/max_sectors_kb
    echo current value of /sys/block/sd$DEVLETTER/queue/max_sectors_kb is `cat /sys/block/sd$DEVLETTER/queue/max_sectors_kb`
    if [ $EXECUTE == "true" ]
    then
      echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
    fi
    DEVINDEX=$[$DEVINDEX+1]
  done
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMSPAREDEVS ]
  do
    DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
    echo RUN echo $CHUNKSIZE \> /sys/block/sd$DEVLETTER/queue/max_sectors_kb
    echo current value of /sys/block/sd$DEVLETTER/queue/max_sectors_kb is `cat /sys/block/sd$DEVLETTER/queue/max_sectors_kb`
    if [ $EXECUTE == "true" ]
    then
      echo $CHUNKSIZE > /sys/block/sd$DEVLETTER/queue/max_sectors_kb
    fi
    DEVINDEX=$[$DEVINDEX+1]
  done
fi

# enable/disable NCQ
DEVINDEX=0
if [[ $NCQ == "enable" ]] || [[ $NCQ == "disable" ]]
then
  if [[ $NCQ == "disable" ]]
  then
    NCQDEPTH=1
  fi
  echo setting NCQ queue depth to $NCQDEPTH
  until [ $DEVINDEX -ge $NUMDEVS ]
  do
    DEVLETTER=${DEVS:$DEVINDEX:1}
    echo RUN echo $NCQDEPTH \> /sys/block/sd$DEVLETTER/device/queue_depth
    echo current value of /sys/block/sd$DEVLETTER/device/queue_depth is `cat /sys/block/sd$DEVLETTER/device/queue_depth`
    if [ $EXECUTE == "true" ]
    then
      echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
    fi
    DEVINDEX=$[$DEVINDEX+1]
  done
  DEVINDEX=0
  until [ $DEVINDEX -ge $NUMSPAREDEVS ]
  do
    DEVLETTER=${SPAREDEVS:$DEVINDEX:1}
    echo RUN echo $NCQDEPTH \> /sys/block/sd$DEVLETTER/device/queue_depth
    echo current value of /sys/block/sd$DEVLETTER/device/queue_depth is `cat /sys/block/sd$DEVLETTER/device/queue_depth`
    if [ $EXECUTE == "true" ]
    then
      echo $NCQDEPTH > /sys/block/sd$DEVLETTER/device/queue_depth
    fi
    DEVINDEX=$[$DEVINDEX+1]
  done
fi

# tune2fs
if [[ $DOTUNEFS == "true" ]]
then
  STRIDE=$[$CHUNKSIZE/$BLOCKSIZE]
  STRWIDTH=$[$CHUNKSIZE/$BLOCKSIZE*($NUMDEVS-$NUMPARITY)]
  echo setting stride to $STRIDE blocks \($CHUNKSIZE kb\)
  echo setting stripe-width to $STRWIDTH blocks \($[$STRWIDTH*$BLOCKSIZE] kb\)
  echo RUN tune2fs -E stride=$STRIDE,stripe-width=$STRWIDTH /dev/$MDDEV
  echo PLEASE NOTE: RUN tune2fs ONLY if you use ext3 or ext4
  if [ $EXECUTE == "true" ]
  then
    read -p "Press [Enter] to execute tune2fs or Ctrl-C to abort"
    tune2fs -E stride=$STRIDE,stripe-width=$STRWIDTH /dev/$MDDEV
  fi
fi

if [ $EXECUTE != "true" ]
then
  echo
  echo PLEASE NOTE: this script did NOTHING! It simply informed you of your current parameters and suggested some changes.
  echo YOU HAVE TO run the commands suggested if you want to execute them or run again this script setting EXECUTE to true. 
fi

# exit
echo $(date): Success >> $LOGFILE
exit 0
```

[SIZE="4"][COLOR="Red"]Use it at your own risk![/COLOR][/SIZE]


[SIZE="4"][COLOR="Red"]EDIT: based on further tests, this tuning seem to [degrade performances]("http://ubuntuforums.org/showthread.php?p=11627044") for my system.
So finally I wrote [my own script]("http://ubuntuforums.org/showthread.php?p=11646960") to tune settings.[/COLOR][/SIZE]

---

### Post by Rickolati on 2013-01-07
Hey guys

Thanks for all the good information. I have used this and what I could find elsewhere to tweak and benchmark my own system..

To see my benchmarks, check it out here. I would be interested to see how my system compare to other systems.

[http://middoraid.blogspot.com.au/2013/01/tweaking.html](http://middoraid.blogspot.com.au/2013/01/tweaking.html)

let me know what you think...

P.S. I also documented every step of the RAID assembly..

---

