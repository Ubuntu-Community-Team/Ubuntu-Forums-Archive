---
title: "Recover Deleted File in Encrypted Home"
date: 2012-03-26
forum: General Help
---

### Post by CptAwesome on 2012-03-26
Hi All,

In what was possibly my most retarded move, I executed "rm -rf *" within a folder containing another folder with my VM's Virtual Drive (.vdi file).

I was quick to notice my blunder and immediately powered the machine off and created an image of the drive using DD. 

I am now able to mount the image.dd image with either OFSMount in Windows 7 or the tradtional route using the installation passphrase etc in Linux (home directory unecrypted). 

Since my dilemma is the lost VDI file, how can I go about recovering it? I tried PhotoRec on the encrypted home directory and it brings back .ecryptfs files which are not really useful. 

I am yet to try running it and foremost on my unecrypted home directory; can someone suggest me tools to use? Alternatively, since the data in the VDI is quite NB - would someone wan to do it for me for a fee? (My whole life resides in it. On the day of my blunder I was updating the back up on an external drive.)

Thanks in advance,

---

### Post by winh8r on 2012-03-26
You might be able to get your file back using 

ext3grep

which is available in the Ubuntu repositories

```
sudo apt-get install ext3grep
```

You should run this either from a live cd or from another partition as the partition where the deleted data resides should be unmounted.

You say you have taken an image of the drive which is good, if possible , make another copy of this image and work on that to begin with.

I am tring to recreate your scenario at the moment and will check back to see how you get along.Although I have never had to recover an encrypted .vdi before, but it seems like a nice challenge!

Hope this helps you.


******EDIT******

Had a look around whilst i was installing on the VirtualBox and found this:

[http://tinyurl.com/ck3eegr]("http://tinyurl.com/ck3eegr")

Seems to be fairly straightforward after all.

---

### Post by CptAwesome on 2012-03-26
Seeing that my partition was using ext4 file system, I will try the above suggested process but using extundelete instead. This should be fine yeah?... 

PS: Yup. I am doing alll my messing about on copies of the original image.

---

### Post by winh8r on 2012-03-26
Sorry i took so long to get back to you.

Yes, extundelete should do it , but you should use the dtime option if possible to prevent recovering too much unneeded data, you can set it to only recover data deleted before or after a specified time.

Also if using the --restore-all option, make sure you have enough space to recover into. If not then it will crash if it runs out of space.

I was hoping to offer more in the way of useful commands here but I have just started this machine up and extundelete is on the other one!!!

You have a fairly good idea what you are doing anyway.


******EDIT******

The  --dump-names option is the best way to find out what extundelete can "see" rather than trying to guess the syntax, then use it to recover the specified file/directory. (i just installed it on this machine to check!)

---

### Post by CptAwesome on 2012-03-27
> **winh8r said:**
> Sorry i took so long to get back to you.

Yes, extundelete should do it , but you should use the dtime option if possible to prevent recovering too much unneeded data, you can set it to only recover data deleted before or after a specified time.

Also if using the --restore-all option, make sure you have enough space to recover into. If not then it will crash if it runs out of space.

I was hoping to offer more in the way of useful commands here but I have just started this machine up and extundelete is on the other one!!!

You have a fairly good idea what you are doing anyway.


******EDIT******

The  --dump-names option is the best way to find out what extundelete can "see" rather than trying to guess the syntax, then use it to recover the specified file/directory. (i just installed it on this machine to check!)

So I tried running 'extundelete image.dd --dump-names' and it reported that it is unable to recover anytyhing. (0 recoverable inodes still lost). The files it was able to recover are nothing useful. 

I tried specyfying the file name to recover 

[PHP]sudo extundelete image.dd - restore-file path/to/file/filename.vdi [/PHP]

but that brought home nothing so I am thinking it is because of the ecrypted file names?... 

I am currently running teskdisk on it but that is giving a "Write isn't available because "none" has been selected" [It doesnt pick up a filesystem when selecting any other partition type]. 

Bleh. FML. Any suggestions?... 

PS: I have no idea what I am doing. I am a noob who enjoys learning new tricks and thus far, it's been exciting. Sadly not fruitful lol.

---

### Post by winh8r on 2012-03-27
What do you get if you run the ```
--restore-all
``` option?

I have tried to recreate the scenario and was able to "see" some entries in testdisk but they are very vague and unrecoverable
from /home/user/.local/share/Trash. Just entries like:

```
?--------- 0  0  0  N -kM- ^FG^C9
```

Which seems to be the encrypted stuff I deleted for the test.

Still working on it though, now looking at possibly using sleuthkit and autopsy, which I have not used before but might give them a go later.

Got a couple of meetings this afternoon, but will check back later this evening.

Keep trying!

---

### Post by CptAwesome on 2012-03-27
> **winh8r said:**
> What do you get if you run the ```
--restore-all
``` option?

If I am not mistaken this returned a folder of about 6GBs with .ecryptfs files. 

I've made some progress I think :/. 

I have managed to collect a bucket of data using testdelete. I have about 68GB of files/folders named according to some convention: 

ECRYPTFS_FNEK_ENCRYPTED.FWZrQ2k16tyJCUTjL.UqnbcSp8mB89Lc-nMe5rMmuntQlC3VPPhVBY3RaE--,
ECRYPTFS_FNEK_ENCRYPTED.FWZrQ2k16tyJCUTjL.UqnbcSp8mB89Lc-nMe.r6QyU4qXc01YZN8mvJ3KU--,
ETC...

within "/home/.ecryptfs/username/.Private". I imagine these are the encrypted data stores?... Is it somehow possible to trick eCryptfs into decrypting these considering I have the passphrases and password?

How can I go about that?...  Thanks in addie.

PS: The files recovered have a collective size consistent to the VDI file that was deleted.

(This is one interesting learning cruve).

---

### Post by winh8r on 2012-03-27
Those seem to be the files you are looking for , now this is where it gets interesting.

I do not know if it would be possible to copy them back to where they were deleted from, and sort of pretend this never happened if you know what I mean.

Okay, I am guessing from this point onwards, and hope that someone who has successfully done this will add something to the discussion.

I am unsure of how the encryption of the .vdi image works, perhaps restoring them all to their original location on your "real" machine, i.e the .Private folder might reconstruct something, although I doubt it.

I am also wondering if it would be possible to make a new VM and "add" them to the new VM in some way.

Going to do some reading about .vdi files.


I think this curve is getting steeper!!!


EDIT***  I did find this, which seems similar to what I was suggesting above  [http://tinyurl.com/brzqd92]("http://tinyurl.com/brzqd92")

worth a try!

---

### Post by elj4176 on 2012-03-27
I'll be curious to see if you are able to extract the encrypted files. I had a similar issue today and need the do the same thing.

I was testing some software and my system locked up. Couldn't start a terminal to kill the process so I pulled the power. When I rebooted my openbox config was gone. I ran thunar and started looking around and all of my files in my home dir were gone - Music, Documents, pictures... Empty.

I now have duplicates of several of these empty folders. I removed the drive and ran extundelete and it recovered my home encryptfs folder and a bunch of encrypted files.

Not sure what to do from here.

---

### Post by CptAwesome on 2012-03-28
_**Recovery Test 1:**_

i) Execute TestDisk with the image
```
testdisk image.dd
```

ii) Open/Select the "None" partition type with teskdisk. 
iii) Do a search (no need for deeper search as my partition was picked up).
iv) Attempt to copy folder home folder (Pressing P on the selected partition).
v) Able to retrieve /home/ folder containin 68GBs of data. 
vi) Enable encrypted file access by adding the original installation mountphrase following the [top post]("http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/") and [this]("http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/#comment-3544") comment. 

Open files only to discover the deleted stuff is there but as duds. Delete all files and start over again. 

I plan to use the same sequence as above, only this time I will actually use a utility to recover stuff rather than copy them. (I was unable to restore directly initally because the image was in read only mode). 

I'll revert with more info/sequential steps within 3 hours.

My colleague has advised that I give up but that is not an option.

I am literally trying to break through:

HDD/image.dd -> ext4 -> ecryptfs -> vdi ->  ntfs.

I've managed to get to the VDI level but with no valid files to work. Failure is not an option.

---

