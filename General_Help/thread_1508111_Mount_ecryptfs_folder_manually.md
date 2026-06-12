---
title: "Mount ecryptfs folder manually"
date: 2010-06-12
forum: General Help
---

### Post by Exaby1e on 2010-06-12
Hi!
I have a encrypted home folder on a hard drive that I took out off my desktop. Now, I would like to manually mount it on my laptop.

I tried the following command:
```
cd /path/to/encrypted/folder
sudo mount -t ecryptfs . /mnt/
```

After entering the password, I got these options:
```
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 8; min keysize = 4; max keysize = 56 (loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (loaded)
Selection [aes]:
```

How are the the home folders encrypted in Ubuntu, using ecryptFs? I didn't find any information about this.

---

### Post by Exaby1e on 2010-06-14
Anybody?

---

### Post by idallen on 2010-09-06
> **Exaby1e said:**
> I have a encrypted home folder on a hard drive that I took out off my desktop. Now, I would like to manually mount it on my laptop.

Me too.  I have my encrypted home directory backed up onto a different disk.  How do I manually mount this?

---

### Post by nicodemus13 on 2010-10-09
The default (at least on Lucid) is AES, so, try 1.

---

### Post by mightyiam on 2011-02-10
Dear Ones,

This is the procedure which worked for me.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually)

Blessings,
Shahar

---

### Post by idallen on 2011-02-10
Here is a script to mount a backup of your encrypted HOME directory.
(This is not the same as a Private directory under your HOME.)
The script prompts for your login password, to unwrap the mount keys.
```

#!/bin/bash -u
#    $0 [ecryptfsdir [mountpoint]]
# Run as root with USER set to login user of ecryptfs
# https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709
# http://ubuntuforums.org/showthread.php?p=10445371
# -Ian! D. Allen - idallen@idallen.ca - www.idallen.com

if [ $(whoami) != 'root' ] ; then
    echo 1>&2 "$0: ERROR must be root to use this"
    exit 1
fi
if [ "$USER" = 'root' ] ; then
    echo 1>&2 "$0: Warning - USER is '$USER'"
fi

# source ecryptfs dir and desired mount point
#
if [ $# -gt 0 ] ; then
    DIR=$1
    shift
else
    # change this to where your keep your default encrypted backup
    DIR=/backup/home/.ecryptfs/$USER
fi
if [ $# -gt 0 ] ; then
    MNT=$1
    shift
else
    # change this to your default backup mount point
    MNT=/mnt/some/place/you/decide
fi
if [ $# -gt 0 ] ; then
    echo 1>&2 "$0: $#: more than two arguments: $*"
    exit 1
fi

# check that things exist and we can write them
if [ ! -d "$DIR" -o ! -r "$DIR" ]  ; then
    echo 1>&2 "$0: not a directory, or not readable: $DIR"
    exit 1
fi
if [ ! -d "$MNT" -o ! -w "$MNT" ]  ; then
    echo 1>&2 "$0: is not a writable directory: $MNT"
    exit 1
fi

pvt=$DIR/.Private
ecr=$DIR/.ecryptfs

if [ ! -d "$pvt" -o ! -r "$pvt" ]  ; then
    echo 1>&2 "$0: not a readable directory: $pvt"
    exit 1
fi
if [ ! -d "$ecr" -o ! -r "$ecr" ]  ; then
    echo 1>&2 "$0: not a readable directory: $ecr"
    exit 1
fi

privsig=$ecr/Private.sig
if [ ! -s "$privsig" -o ! -r "$privsig" ]  ; then
    echo 1>&2 "$0: not a non-null, readable signature file '$privsig'"
    exit 1
fi

sig1=$(head -n1 "$privsig") || exit $?
sig2=$(tail -n1 "$privsig") || exit $?
case "$sig1/$sig2" in
????????????????/???????????????? ) ;;
*)  echo 1>&2 "$0: Unable to extract signatures from '$privsig'"
    echo 1>&2 "$0: sig1: '$sig1'"
    echo 1>&2 "$0: sig2: '$sig2'"
    exit 1
    ;;
esac

read -s -p "$USER login password: " loginpass || exit $?
echo "" # add the missing newline after reading the password

# echo "DEBUG sig1 $sig1 and sig2 $sig2"
# keyctl clear @u
printf '%s\0' "$loginpass" | ecryptfs-insert-wrapped-passphrase-into-keyring "$ecr/wrapped-passphrase" - || exit $?
# keyctl list @u # DEBUG

# The -i bypasses the mount helper - see "man mount.ecryptfs"
#  ... but the "mount" man page claims this has a different function!
#  ... but it works for me (Ubuntu 10.10).  -IAN!
mount -i -t ecryptfs -o "ro,ecryptfs_passthrough=no,ecryptfs_unlink_sigs,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_sig=$sig1,ecryptfs_fnek_sig=$sig2" "$pvt" "$MNT" || exit $?
echo ""
df "$MNT"

```

---

### Post by mightyiam on 2011-02-12
> **idallen said:**
> Here is a script to mount a backup of your encrypted HOME directory.
(This is not the same as a Private directory under your HOME.)
The script prompts for your login password, to unwrap the mount keys.
```

#!/bin/bash -u
#    $0 [ecryptfsdir [mountpoint]]
# Run as root with USER set to login user of ecryptfs
# https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/455709
# http://ubuntuforums.org/showthread.php?p=10445371
# -Ian! D. Allen - idallen@idallen.ca - www.idallen.com

if [ $(whoami) != 'root' ] ; then
    echo 1>&2 "$0: ERROR must be root to use this"
    exit 1
fi
if [ "$USER" = 'root' ] ; then
    echo 1>&2 "$0: Warning - USER is '$USER'"
fi

# source ecryptfs dir and desired mount point
#
if [ $# -gt 0 ] ; then
    DIR=$1
    shift
else
    # change this to where your keep your default encrypted backup
    DIR=/backup/home/.ecryptfs/$USER
fi
if [ $# -gt 0 ] ; then
    MNT=$1
    shift
else
    # change this to your default backup mount point
    MNT=/mnt/some/place/you/decide
fi
if [ $# -gt 0 ] ; then
    echo 1>&2 "$0: $#: more than two arguments: $*"
    exit 1
fi

# check that things exist and we can write them
if [ ! -d "$DIR" -o ! -r "$DIR" ]  ; then
    echo 1>&2 "$0: not a directory, or not readable: $DIR"
    exit 1
fi
if [ ! -d "$MNT" -o ! -w "$MNT" ]  ; then
    echo 1>&2 "$0: is not a writable directory: $MNT"
    exit 1
fi

pvt=$DIR/.Private
ecr=$DIR/.ecryptfs

if [ ! -d "$pvt" -o ! -r "$pvt" ]  ; then
    echo 1>&2 "$0: not a readable directory: $pvt"
    exit 1
fi
if [ ! -d "$ecr" -o ! -r "$ecr" ]  ; then
    echo 1>&2 "$0: not a readable directory: $ecr"
    exit 1
fi

privsig=$ecr/Private.sig
if [ ! -s "$privsig" -o ! -r "$privsig" ]  ; then
    echo 1>&2 "$0: not a non-null, readable signature file '$privsig'"
    exit 1
fi

sig1=$(head -n1 "$privsig") || exit $?
sig2=$(tail -n1 "$privsig") || exit $?
case "$sig1/$sig2" in
????????????????/???????????????? ) ;;
*)  echo 1>&2 "$0: Unable to extract signatures from '$privsig'"
    echo 1>&2 "$0: sig1: '$sig1'"
    echo 1>&2 "$0: sig2: '$sig2'"
    exit 1
    ;;
esac

read -s -p "$USER login password: " loginpass || exit $?
echo "" # add the missing newline after reading the password

# echo "DEBUG sig1 $sig1 and sig2 $sig2"
# keyctl clear @u
printf '%s\0' "$loginpass" | ecryptfs-insert-wrapped-passphrase-into-keyring "$ecr/wrapped-passphrase" - || exit $?
# keyctl list @u # DEBUG

# The -i bypasses the mount helper - see "man mount.ecryptfs"
#  ... but the "mount" man page claims this has a different function!
#  ... but it works for me (Ubuntu 10.10).  -IAN!
mount -i -t ecryptfs -o "ro,ecryptfs_passthrough=no,ecryptfs_unlink_sigs,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_sig=$sig1,ecryptfs_fnek_sig=$sig2" "$pvt" "$MNT" || exit $?
echo ""
df "$MNT"

```

This could be a great addition to the ecryptfs-utils package. Do you think that this can be submitted as a patch?

Blessings,
Shahar

---

### Post by oldmilwaukee on 2012-02-21
EDIT This seems to have helped a lot of people in the same boat [http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/) 

if found it by searching for  ecryptfs_parse_tag_70_packet: Error attempting to find auth tok for fnek sig 
which was in dmesg


Old post follows -->

I tried to use the script above but looking it over i was perplexed by the requirement 


[B]if [ $(whoami) != 'root' ] ; then
    echo 1>&2 "$0: ERROR must be root to use this"
    exit 1
fi
if [ "$USER" = 'root' ] ; then
    echo 1>&2 "$0: Warning - USER is '$USER'"
fi

[/B]I need to be root, but if I am root i get a warning?
I imagine that userid is important when unencrypting a home folder.. so..I just grabbed the relevant command from the bottom of the above script and ran it as sudo. 

BUT FIRST:
>>ecryptfs-add-passphrase --fnek
copy the second one
OK NOW:
>>sudo mount -t ecryptfs /home/username/.Private /mnt/foo/

This got the files unencrypted (I could watch videos with mangled filenames) but the file names stayed encrypted.

Then, since I knew the ownership was wrong (as cryptfs-recover-private had told me when it failed me earlier) I issued
>>chown -R username:usernam /mnt/foo/ 
to the somewhat mounted filesystem

then to be clean i rebooted
fails to log in properly
ctrl-alt-f1

>>sudo cryptfs-mount-private

crtl-alt-f7
unlock screen pops up. unlock, everything else is peachy
yay!


Full disclosure, I had messed up the permissions on the drive by mounting it r/w from anther distro, I had created a chroot mount to mount the drive from fedora.  
i was using ecryptfs-recover-private on my fedora boot to do this

Anyways I saw lot of unsolved threads about this, hopefully this helps some one.
I cant find those specific threads anymore as the browser history is not mounted anymore (since the actual encrypted partion is mount on /home/username now.)
I know the browser data still exists, but whatever im just going to put this here)

---

### Post by Milan Knizek on 2012-09-25
> **oldmilwaukee said:**
> 
I tried to use the script above but looking it over i was perplexed by the requirement 


[B]if [ $(whoami) != 'root' ] ; then
    echo 1>&2 "$0: ERROR must be root to use this"
    exit 1
fi
if [ "$USER" = 'root' ] ; then
    echo 1>&2 "$0: Warning - USER is '$USER'"
fi

[/B]I need to be root, but if I am root i get a warning?


Try to run it as:

```
$ sudo USER=your_user_name script.sh /path/to/encrypted/home/dir /mount/point
```

---

