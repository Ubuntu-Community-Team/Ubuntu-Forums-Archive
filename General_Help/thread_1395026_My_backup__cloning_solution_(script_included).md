---
title: "My backup / cloning solution (script included)"
date: 2010-01-31
forum: General Help
---

### Post by paxxus on 2010-01-31
Hi all,

I have struggled quite a bit with getting a simple backup / cloning solution working. In case others might find it useful I will post my working solution here; at the end of this post I have included the script I made (backup_hdd).

This script enables me to:

[LIST]
[*]Backup my main drive from the ubuntu LiveUSB (nice, since I can browse the net etc. while the backup is running).
[*]Restore COMPLETELY on another (or the same) disk - the clone boots as if it were the original.
[*]Restore individual partitions (in case only my ubuntu or Vista got messed up).
[/LIST]
Usage (assuming the backup_hdd script is located in /home/ubuntu/bin and marked as executable):

[LIST=1]
[*]cd into the directory where you want the image files to be stored (typically an USB drive).
[*]Type: sudo /home/ubuntu/bin/backup_hdd sda
where "sda" is the drive you want to backup.
[*]Check that all is OK, then answer "y".
[*]Wait for the backup to complete.
[/LIST]
Note that the backup_hdd script in itself is fairly harmless as it can only save, not restore. When the backup is complete I get these files on my system:

```
-rwxr-xr-x 1 root root        1669 2010-01-31 07:17 img-2010-01-31-restore*
-rw------- 1 root root    26118449 2010-01-31 03:32 img-2010-01-31-sda1.gz
-rw------- 1 root root 82104894103 2010-01-31 06:27 img-2010-01-31-sda2.gz
-rw------- 1 root root  8199856535 2010-01-31 06:38 img-2010-01-31-sda4.gz
-rw------- 1 root root  2187903461 2010-01-31 06:46 img-2010-01-31-sda6.gz
-rw------- 1 root root  8748460496 2010-01-31 07:17 img-2010-01-31-sda7.gz
-rw-r--r-- 1 root root     1048576 2010-01-31 03:32 img-2010-01-31-sda.fst
-rw-r--r-- 1 root root       31744 2010-01-31 03:32 img-2010-01-31-sda.hid
-rw-r--r-- 1 root root         512 2010-01-31 03:32 img-2010-01-31-sda.mbr
-rw-r--r-- 1 root root         412 2010-01-31 03:32 img-2010-01-31-sda.pt
```*.mbr is the master boot record.
*.hid is the 62 sectors of hidden data after the MBR.
*.pt is the partition table.
*.gz is the individual partitions as saved by partimage.
*.fst is really not needed, I just save it to be safe. It contains the first 1MB of the drive and thus includes the MBR.

Notice that a restore script was generated as well, and this scripts **is** potentially harmful if you don't know what you're doing.

To restore completely to e.g. sdb:

[LIST=1]
[*]cd into the directory where the image files are stored.
[*]Type: sudo ./<prefix>-restore sdb
[*]If all is good, type "yes"
[*]Wait for the restore to complete.
[/LIST]
If you only need to restore parts of the disk, you can open the <prefix>-restore script and either comment out the dd/sfdisk/partimage commands you don't want executed or copy selected (typically partimage) commends to the shell prompt.

The backup_hdd and the <prefix>-restore scripts will not start if they detect that the drive is mounted, so this should provide some level of safety against user error.

I have tested this in ubuntu 9.10 on my dual boot Vista/ubuntu machine which looks like this:

```
sudo fdisk -lu /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37053704

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     1028159      514048+  83  Linux
/dev/sda2   *     1028160   410637464   204804652+   7  HPFS/NTFS
/dev/sda3       410637465   820230704   204796620    5  Extended
/dev/sda4       820232192   956289015    68028412    7  HPFS/NTFS
/dev/sda5       410637528   418830614     4096543+  82  Linux swap / Solaris
/dev/sda6       418830678   582677549    81923436   83  Linux
/dev/sda7       582677613   820230704   118776546   83  Linux

```The provided backup_hdd script will only backup partitions of type 7 and 83, but at the top of the script you can easily add more types, provided these are supported by partimage (which you need to install of course (sudo aptitude install partimage)).

Anyway, here's the backup_hdd script, remember to mark it executable (chmod +x backup_hdd):

```
#!/bin/bash
###############################################################################

# Only these partition IDs will be considered for backup.
export SAVE_IDS="7 83"

# Linux swap partition ID.
export SWAP_ID="82"

###############################################################################

if [ "$1" == "" ]; then
    echo 'Please specify HDD (e.g "sda")'
    exit 1
fi

HDD="$1"

set -ue

TOOLS="perl dd df sfdisk partimage"
for TOOL in ${TOOLS}; do
    if which ${TOOL} > /dev/null; then
        :
    else
        echo "Unavailable tool: ${TOOL}"
        exit 1
    fi
done

MNT=`df 2>&1 | grep /dev/${HDD} || :`
if [ "${MNT}" != "" ]; then
    echo "Device appears to be mounted: ${HDD}"
    exit 1
fi

PART_NUM_LIST=`
sfdisk -d /dev/${HDD} | perl -ne '
if ( m,^(/dev/[a-z]+(\d+)), ) {
    die "Could not understand sfdisk output\n"
    unless ( m,^/dev/[a-z]+(\d+).* Id=\s*(\d+), );
    foreach $i ( split( " ", $ENV{SAVE_IDS} ) ) {
        print( " $1" ) if ( $2 eq $i );
    }
}
'
`

SWAP_NUM_LIST=`
sfdisk -d /dev/${HDD} | perl -ne '
if ( m,^(/dev/[a-z]+(\d+)), ) {
    die "Could not understand sfdisk output\n"
    unless ( m,^/dev/[a-z]+(\d+).* Id=\s*(\d+), );
    print( " $1" ) if ( $2 eq $ENV{SWAP_ID} );
}
'
`

echo "============================================================"
echo "Save: ${HDD}"
echo "============================================================"
fdisk -l /dev/${HDD}
echo "============================================================"

echo "The following partitions will be backed up:"
for PART_NUM in ${PART_NUM_LIST}; do
    NAME=${HDD}${PART_NUM}
    PARTITION="/dev/${NAME}"
    echo "  ${PARTITION}"
done

if [ "${SWAP_NUM_LIST}" != "" ]; then
    echo "The following partitions will be treated as linux swap:"
    for PART_NUM in ${SWAP_NUM_LIST}; do
        NAME=${HDD}${PART_NUM}
        PARTITION="/dev/${NAME}"
        echo "  ${PARTITION}"
    done
fi

echo ""
echo -n "Continue (y/n)? "
read ANSWER
if [ "${ANSWER}" != "y" ]; then
    exit
fi

echo "============================================================"

TAG=img-$(date +%Y-%m-%d)

# The corresponding restore commands are saved in this variable.
RESTORE_CMD=""

echo "Saving MBR..."
dd if=/dev/${HDD} of=${TAG}-${HDD}.mbr count=1 bs=512
RESTORE_CMD+="dd if=${TAG}-${HDD}.mbr of=/dev/\${HDD}\n"

echo "Saving hidden data after MBR..."
dd if=/dev/${HDD} of=${TAG}-${HDD}.hid count=62 bs=512 skip=1
RESTORE_CMD+="dd if=${TAG}-${HDD}.hid of=/dev/\${HDD} bs=512 seek=1\n"

# Just in case.
echo "Saving first 1MB of disk..."
dd if=/dev/${HDD} of=${TAG}-${HDD}.fst count=2048 bs=512

echo "Saving partition table..."
sfdisk -d /dev/${HDD} > ${TAG}-${HDD}.pt
RESTORE_CMD+="sfdisk --no-reread -f /dev/\${HDD} < ${TAG}-${HDD}.pt\n"

for PART_NUM in ${PART_NUM_LIST}; do
    FILE="${TAG}-${HDD}${PART_NUM}.gz"
    PARTITION="/dev/${HDD}${PART_NUM}"
    echo "Saving partition: ${PARTITION}"
    partimage -V 0 -z1 -o -d -b save ${PARTITION} ${FILE}
    RESTORE_CMD+="partimage -b restore /dev/\${HDD}${PART_NUM} ${FILE}\n"
done

for PART_NUM in ${SWAP_NUM_LIST}; do
    RESTORE_CMD+="mkswap /dev/\${HDD}${PART_NUM}\n"
done

###############################################################################

SF="${TAG}-restore"

cat > ${SF} <<"EOH"
#!/bin/bash

if [ "$1" == "" ]; then
    echo 'Please specify HDD (e.g "sda")'
    exit 1
fi

HDD="$1"

set -ue

TOOLS="dd df sfdisk partimage"
for TOOL in ${TOOLS}; do
    if which ${TOOL} > /dev/null; then
        :
    else
        echo "Unavailable tool: ${TOOL}"
        exit 1
    fi
done

MNT=`df 2>&1 | grep /dev/${HDD} || :`
if [ "${MNT}" != "" ]; then
    echo "Device appears to be mounted: ${HDD}"
    exit 1
fi

echo "============================================================"
echo "Restore to: ${HDD}"
echo "============================================================"
fdisk -l /dev/${HDD}
echo "============================================================"

echo -n "This drive will be WIPED. Continue (yes/no)? "
read ANSWER
if [ "${ANSWER}" != "yes" ]; then
    exit
fi

echo ""
echo "ALL EXISTING DATA ON THE FOLLOWING DRIVE WILL BE COMPLETELY LOST"
echo "==> ${HDD}"
echo ""
echo -n "Last chance to hit Ctrl-C..."
for i in `seq 10 -1 0`; do
    sleep 1
    echo -n " ${i}"
done
echo ""
echo "============================================================"

set -v

EOH

echo -e ${RESTORE_CMD} >> ${SF}

cat >> ${SF} <<"EOH"
set +v

echo "============================================================"
echo ""
echo "Restore complete."
echo ""
EOH

chmod +x ${SF}

###############################################################################

echo "============================================================"
echo ""
echo "Backup complete."
echo ""


```

---

