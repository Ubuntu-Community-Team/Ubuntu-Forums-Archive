---
title: "Superblock errors"
date: 2006-04-04
forum: General Help
---

### Post by megadodo on 2006-04-04
Hey
When booting up, kubuntu (5.10 amd64) says that fsck failed on /dev/hda and that i have to run it manualy. It then drops me to  a shell. So i run:
```
root# fsck /dev/hda
fsck 1.35 (28-Feb-2004)
e2fsck 1.35 (28-Feb-2004)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

So i then run:
```
root# e2fsck -b 8193 /dev/hda
e2fsck 1.35 (28-Feb-2004)
e2fsck: Bad magic number in super-block while trying to open /dev/hda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```

Now I actually have ext3 on that partition, so i tried running fsck.ext3 /dev/hda and it gave identical error messages, as did fsck.ext3 -b 8193 /dev/hda

Any help would be greatly apprectiated, as at the moment I cant boot up and am therefore screwed!
Cheers
Richard

---

### Post by waster on 2006-04-04
is it by any chance part or formerly part of a software raid array?

---

### Post by megadodo on 2006-04-04
No I have never used raid.
Rich

---

### Post by Al3xanR0 on 2006-04-04
I had an issue nearly identical to what you are experiencing when I was using hoary. I was attempting to add an additional drive. I posted to no avail without any response (I'm not bitter, really I'm not) and that is by no means a negative reflection on this forum I have received a lot of  good help. I continued looking here a little, there a little for the solution to my dillema. All indications lead me to believe that perhaps the drive was bad. I the logical thing I swapped the drive,  only with the same results; now of course I am skeptical and confused because the odds of both drives going bad are slim. To add insult to injury the drives were in there original static bags. This time I tried somthing different; I was about due for an upgrade so I backked up my home directory, popped in a breezy cd and performed a fresh install then restored my home directory all with the additional drive in place. Ironically I am able to mount the drive with out error, the same drive that rendered the infamous "Bad Magic Number" error go figure.. Sorry that I wasn't much assistance just empathising I suppose. Good luck

---

### Post by megadodo on 2006-04-04
Ive managed to fix it
The error message was because I was running fsck /dev/hda rather than fsck /dev/hda2 which is tha actual partition, rather than /dev/hda which doesnt exist, which would explain why it couldnt find the superblock :oops: 
When I ran fsck on the actual partition, it came up with lots of errors that i didnt understand, I pressed 'y' a lot, and now it works and boots fine
Cheers
Rich

---

