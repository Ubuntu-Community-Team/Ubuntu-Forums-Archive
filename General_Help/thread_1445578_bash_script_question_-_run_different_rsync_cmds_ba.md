---
title: "bash script question - run different rsync cmds based on which devices are mounted"
date: 2010-04-02
forum: General Help
---

### Post by stone1343 on 2010-04-02
Since my hobby is distro-hopping, I am very careful about having my data backed up properly, but it's also in different places (e.g. photos and music on separate flash drives), so I have a few rsync's that I can execute manually, drives are mounted.

Unfortunately, it gets confusing very quickly, I'd like a simple bash script that goes something like this (this pseudo-code would be most like REXX):

pair.1 = (/dev/sdb1, /dev/mmcblkp01)
pair.2 = (/some/other/device, /yet/another/device)

for i = 1 to #pairs
  if pair.i.1 && pair.i.2 are mounted
    rsync -av --delete pair.i.1 pair.i.2
  else
    tell me which one (or both) not mounted to remind me
  end

Seems simple enough, but I've never written a bash script and wouldn't know where to start. Suggestions?

If it's wrong of me to ask here, please be gentle and just tell me where I should ask something like this. :-)

Jeff

---

### Post by stone1343 on 2010-04-02
I'm reading up and think it will somehow probably use the output from

ls -l /dev/disk/by-uuid

that gives the uuid of the mounted devices, right?

---

### Post by blueridgedog on 2010-04-02
A rough out:

```
#!/bin/bash
SDB1=`mount | grep sdb1`
SDA3=`mount | grep sda3`
SDC1=`mount | grep sdc1`

if [ -n "$SDB1" ]; then
        echo $SDB1
        # put in rsync command
else
        echo "sdb1 is not mounted"
fi

if [ -n "$SDA3" ]; then
        echo $SDA3
        # put in rsync command
        else
        echo "sda3 is not mounted"
fi

if [ -n "$SDC1" ]; then
        echo $SDC1
        # put in rsync command
        else
        echo "sdc1 is not mounted"
fi
```

It may get you started in the right direction.  I used some random device names, but you should get an idea of what you can do.  You could chop up the output of the mount command to see where they were mounted and then send that to the rsync command as a variable.

---

### Post by stone1343 on 2010-04-02
thank you very much, that's what I hoped for something to get me started. Awesome!!!

---

### Post by blueridgedog on 2010-04-02
Just a final word of warning...test what you come up with very carefully so that you don't overwrite something you need, especially if you are using the delete option in rsync.

Also, keep in mind that this assumes that drive and partitions will remain consistent.  If you change things around, you will want to change your script.

---

### Post by stone1343 on 2010-04-21
FYI, here's the script as I have it working now. Stored in my Ubuntu One folder, it can be used on each of my computers. I'm sure it could be better, but it does what I need.

Thanks for your help!!!

Jeff

#!/usr/bin/env bash

function do-it
{
  # use -anv to test, -av to really do it
  rsync -av --delete $exc $src $tgt
}

# Videos from SDHC
lbl=sdhc-ext4-8gb
if [ -d /media/$lbl ]; then
  src=/media/$lbl/Videos/
  lbl=EXT3-80GB
  if [ -d /media/$lbl ]; then
    tgt=/media/$lbl/Videos/8GB
    exc=
    if [ -d $tgt ]; then
      do-it
    fi
  else
    echo "Connect $lbl to backup $src"
  fi
  lbl=EXT4-8GB
  if [ -d /media/$lbl ]; then
    tgt=/media/$lbl/Videos
    exc=
    if [ -d $tgt ]; then
      do-it
    fi
  else
    echo "Connect $lbl to backup $src"
  fi
else
  echo "Connect $lbl"
fi

# Music, Pictures, Videos
lbl=FAT32-32GB
if [ -d /media/$lbl ]; then
  src=/media/$lbl/
  lbl=NTFS-80GB
  if [ -d /media/$lbl ]; then
    tgt=/media/$lbl/Music-Pictures-Videos
    exc=
    if [ -d $tgt ]; then
      do-it
    fi
  else
    echo "Connect $lbl to backup $src"
  fi
else
  echo "Connect $lbl"
fi

# Non-hidden directories in $HOME
src=$HOME/
lbl=EXT3-80GB
if [ -d /media/$lbl ]; then
  tgt=/media/$lbl/$(uname -n)/$USER
  exc="--exclude=.*"
  if [ ! -d $tgt ]; then
    mkdir -p $tgt
  fi
  do-it
else
  echo "Connect $lbl to backup $src"
fi

---

