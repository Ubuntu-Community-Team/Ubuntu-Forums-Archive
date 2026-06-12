---
title: "Newcomer, basic mounting problems"
date: 2009-08-15
forum: General Help
---

### Post by Goatherd on 2009-08-15
Hi,
 
First of all, my apologies in advance for pestering you with what is probably just basic ignorance on my part. Be gentle!
 
I am a complete newcomber to this. 
 
I have never used Ubuntu before. It was pointed out to me by somebody in an effort to rescue files from my computer's hard drive. Essentially, some trojan got entangled with my drivers and knocked my operating system (Windows XP) out of commission. I am trying to recover the files I had on my computer. (I have an external hard drive ready).
 
Following instructions, I used another computer to create a Ubuntu CD (9.04). And then put in my defunct computer. As per instructions, I clicked on "Try Ubuntu without changing your compuer" option and a desktop loaded up as expected. I was next instructed to 'mount' the hard drive via places->computer. 
 
Unfortunately, it doesn't mount. It doesn't say it can't mount, I just click on the option, some little note on the bar says "starting computer", but then that's it. It doesn't do anything. I can't open a file manager of any sort, don't see anything.
 
Fearing it was a corrupt CD, I burnt a second Ubuntu CD, but it also didn't mount anything.
 
Evidently, I don't know what I'm doing or what I am supposed to be doing. 
 
I am a little desperate to get these files quickly, since they contain some work stuff I have to get done ASAP. I have tried searching these forums, but either I don't find my problem or maybe its there (or very basic) and I'm just not seeing it.
 
Again, I am a complete newcomer, never even heard of Ubuntu before, so a lot of the technical details are going over my head.
 
Any help or hint in the right direction would be much appreciated.
 
Thanks in advance. 
 
[For the record, when the OS failed, I tried to reinstall XP (repair, not new), but it got hung up and BSODd. So the non-operational OS is effectively in the middle of a setup which it can't complete. I doubt that has anything to do with the mounting issue, but maybe it does]
 
[EDIT: If it helps any, it can also detect my external drive, CD drive, etc., but also doesn't "mount" for me to see.  Obviously, I am missing some step I should be doing]

---

### Post by mwjones on 2009-08-15
Let's see if we can mount it manually.  

[LIST=1]
[*]Fire up a terminal: (top left) Applications > Accessories > Terminal
[*]Run: ```
dmesg | grep sd
```
[*]Look for distinct drives in the output, you should see lines like:
```
[    2.822790] sd 0:0:0:0: [sda] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
```
The [sda] is one drive.  
[*]Assuming your corrupted Windows drive is /dev/sda, let's try creating a mount point and mounting the first partition:
```
sudo mkdir /mnt/windows
sudo mount /dev/sda1 /mnt/windows
```
[*]If that mounts, you can begin browsing /mnt/windows (open a directory under Places in the top left) and access your files there.
[/LIST]

HTH!

---

### Post by Goatherd on 2009-08-15
Thanks. Just tried that. Gave some scary lines (Buffer I/O error on device, sdb, etc.) but went through.
 
But the basic problem seems to remain the last step - opening a directory through places. I can't figure out how. This is probably embarassingly basic, but no matter what device I choose, I can't seem to get any browsing window. When I use "search" command, I can see the thankfully see the contents of the hard drive (but can't move them. I right-click to open folder, and nothing happens).
 
I feel really stupid. What am I missing here? How do I browse/move stuff without a browsing window?
 
Thanks for you help.

---

### Post by yeeeev on 2009-08-15
if the mount command succeeded, you can open a file manager by any one of these options:
* Lead an open file manager to the /mnt/windows directory
* Type in a command line: "nautilus /mnt/windows &"

If the mount failed, the disk you're trying to save might not contain a usable file system anymore...

Can you copy/paste here the error message you received when mounting?

---

### Post by Goatherd on 2009-08-15
> **yeeeev said:**
> if the mount command succeeded, you can open a file manager by any one of these options:
* Lead an open file manager to the /mnt/windows directory
* Type in a command line: "nautilus /mnt/windows &"
 
If the mount failed, the disk you're trying to save might not contain a usable file system anymore...
 
Can you copy/paste here the error message you received when mounting?
 
Doesn't recognize nautlius. In fact, I can't find nautilus anywhere - at least not where it is said it is supposed to be. 
 
I checked the installed packages at start up, and it says its there. But I can't see it anywhere on any menus. Nor is it under the add/remove programs. Home folder doesn't open, etc.  Although the search does seem to work.
 
Maybe it's just a missing Nautlius? Am I supposed to activate it somehow?
 
I didn't receive any error message when mounting.

---

### Post by michy99 on 2009-08-15
Nautilus is the name of the file manager. Let's try something basic. Enter these commands in a terminal and post the output here.```
sudo fdisk -l
mount
```

---

### Post by Goatherd on 2009-08-15
> **michy99 said:**
> Nautilus is the name of the file manager. Let's try something basic. Enter these commands in a terminal and post the output here.```
sudo fdisk -l
mount
```
 
That's what I fear the problem is. I don't seem to have a working file manager.
 
On your first command:
 
```

Device boot     Start     End            Blocks    Id    System
/dev/sdb1        1          121601    97676001   7   HPFS/NFTS

```
 
'mount' is huge (I can't just cut & paste, since it is on another computer, I'll have to transcribe it by hand. Doesn't seem to have any errors, though. Any particular line to look for?  Or should I go ahead and transcribe the whole thing?)

---

### Post by P4man on 2009-08-15
it sounds like the harddisk of the XP install is dead or dying. That correlates both with windows itself being defunct and the 'buffer I/O errors' you see in ubuntu. The output of "mount" should also fit on a screen, if its that huge, I want to see it even more :)

Anyway, what are you trying to achieve ? Do you want to rescue some files or do you hope to revive the drive? My guess is its dead or dying, so you might be able to save some stuff, but dont expect to revive it.

---

### Post by michy99 on 2009-08-15
Was that the only output from sudo fdisk -l? Do you only have one hard drive? If so, it seems it would be sda, not sdb.

---

### Post by Goatherd on 2009-08-15
> **P4man said:**
> it sounds like the harddisk of the XP install is dead or dying. That correlates both with windows itself being defunct and the 'buffer I/O errors' you see in ubuntu. The output of "mount" should also fit on a screen, if its that huge, I want to see it even more :)
 
Not that huge. Just a pain to transcribe.  :D
 
I don't think it is physically dead/dying HDD.  I can certainly see all the files on the HDD via the "search for" option.   At any rate, I'm working ubuntu from a boot CD.   
 
Just don't seem to have an operating file manager in ubuntu.  Nothing under Places seems to work.
 
Following another suggestion, just tried alt-F2 and typing nautlius, nothing came up.   Certainly seems like nautilus just ain't there or needs to be activated or something.  
 
 > Anyway, what are you trying to achieve ? Do you want to rescue some files or do you hope to revive the drive? My guess is its dead or dying, so you might be able to save some stuff, but dont expect to revive it.
 
Just trying to transfer the HDD filoes on to an external drive.  What happens after, I am not sure. :(

---

### Post by Goatherd on 2009-08-15
> **michy99 said:**
> Was that the only output from sudo fdisk -l? Do you only have one hard drive? If so, it seems it would be sda, not sdb.
 
Yeah, only one HD.  sda? sdb?

---

### Post by P4man on 2009-08-15
no need to transcribe.. there is this thing called "copy paste" :)
In case you're not already, in the livecd you should be able to connect to the web and post here.

As for nautilus not working.. thats weird. Wild guess: its choking on that drive that it cant properly read? If its not too much trouble, try disconnecting it physically (with the machine turned off of course) and then see if nautilus works as it should.

As for the drive: I admire your optimism, but ubuntu generally doesnt throw around I/O errors if there is nothing wrong with it :s

---

### Post by P4man on 2009-08-15
another possibility is that there is something wrong with the cd, or the image you downloaded. In the startup menu of ubuntu, there is an option "check this cd for errors". Doesn't hurt running it, so we can exclude that.

---

### Post by Goatherd on 2009-08-15
> **P4man said:**
> another possibility is that there is something wrong with the cd, or the image you downloaded. In the startup menu of ubuntu, there is an option "check this cd for errors". Doesn't hurt running it, so we can exclude that.
 
BINGO!!!  :)
 
Just downloaded another copy from a different location and burnt another disk.  Problem gone.  Everything works well now.  Nautilus splendid.  Something must have been wrong with the earlier ISO download (it was buggered on two CDs).
 
Probably should have just done that before bothering all of you. :oops:
 
But thanks so very much for your time and attention! 
 
THANKS A LOT GUYS!!
 
You really saved my ***.
 
Now, I have to go save my poor little files....

---

