---
title: "bash cp from network directory"
date: 2009-09-20
forum: General Help
---

### Post by metalmaniac248 on 2009-09-20
hi im trying to make a simple bash script to copy a directory from within a network folder onto my machine

the network folder is the Vista public folder and is shared on our home network, 

im using ```
cp -r smb://baskerville-pc/public/Photos /media/My\ Book
```as the command but its saying smb://baskerville-pc/public/Photos is not a directory, so I'm assuming that the smb://baskerville-pc/public/Photos that is the nautilus location bar is not what i should be using with cp


help greatly appreciated

thanks

---

### Post by blueridgedog on 2009-09-21
Nautilus is natively aware of the remote cifs share (samba or smb) and can interact with it.  Bash isn't so blessed.  To get bash to be able to copy from a cifs share, you need to mount the share:

 /sbin/mount.cifs <remotetarget> <dir> -o <options>

So, in your case you might:

```
mkdir /home/USER/baskerville_photos
sudo mount.cifs smb://baskerville-pc/public/Photos /home/USER/baskerville_photos
cp -r /home/USER/baskerville_photos /media/My\ Book
```

Change USER to be your account.

---

### Post by metalmaniac248 on 2009-11-06
when i tried that it appears that ```
sudo mount.cifs
``` is not command

---

### Post by jonathan morales on 2009-11-06
you want:

```

mkdir /home/USER/baskerville_photos
sudo mount -t cifs //baskerville-pc/public/Photos  /home/USER/baskerville_photots

cp /home/USER/baskerville_photos/* /media/My\ Book


```

---

### Post by jonathan morales on 2009-11-06
Also if you're going to make a script out of it that you want to run whenever, you're going to have to leave the sudo out of it, and just run it as root

as in open gedit and paste:

# simple script to copy photos
mkdir /home/USER/baskerville_photos
mount -t cifs //baskerville-pc/public/Photos  /home/USER/baskerville_photots
cp /home/USER/baskerville_photos/* /media/My\ Book
rm -r /home/USER/baskerville_photos/

save as /home/USER/mount.sh (for example)

To run it, open a terminal and type 
```
sudo bash mount.sh
```

You could also leave the directory you're going to mount it to there, no harm in keeping it, and then just mount the network share from inside it whenever you want. In that case remove the mkdir and rm-r lines from that script.

---

### Post by metalmaniac248 on 2009-11-09
hi the script didnt work so i ran the mount command outside of the script 

this is what i got
```
nick@nick-desktop:~/Documents/Bash$ sudo mount -t cifs //baskerville-pc/Public /home/nick/downstairs\ backup\ mount
mount: wrong fs type, bad option, bad superblock on //baskerville-pc/Public,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

