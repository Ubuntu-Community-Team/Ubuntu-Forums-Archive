---
title: "Problems backing up encrypted home folder"
date: 2010-02-13
forum: General Help
---

### Post by danielstrong52 on 2010-02-13
Hello, I recently installed Ubuntu Karmic on my netbook (I tried netbook remix but preferred the look of the regular desktop edition). When during installation, the option to encrypt the home folder appeared, and being mildly paranoid I thought, "sure, why not?" (I must warn you that I am a new user with little technical knowledge other than what I have managed to gather in a semi-passive manner over the past couple of months). The problem is, I (try to) backup my data weekly, and so today I gave it a shot (I got the desktop edition a week ago). I have encountered the following problem.
 
I backup my system following (approximately) the instructions at [https://help.ubuntu.com/community/BackupYourSystem/TAR#Preparing](https://help.ubuntu.com/community/BackupYourSystem/TAR#Preparing) for Backup
The exact command I enter at backup is:
sudo tar -cvpjf 2010.02.13.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/home/dan/music /
(I exclude my music folder as it is huge and I already have it all in several other locations)
When I executed this command all ran smoothly for a while, however it soon began backing up the directory
/home/.ecryptfs/dan/.Private
At this point, it started backing up the huge number of files in this directory. I assume these are encryption keys? Forgive my ignorance...
Anyway, it took several hours going through this folder, and finally bzip gave up, complaining of excessive file size:
----
bzip2: I/O or other error, bailing out.  Possible reason follows.
bzip2: File too large
	Input file = (stdin), output file = (stdout)
----
Now... I am just guessing here, but I assume that excluding the encryption keys and such from the backup would be a bad idea: I guess that if I did not restore the relevant directories along with my home folder, it would be inaccessible?

Is there a way to avoid backing up such a large amount of data? How? If not, could you point me to some instructions for backing up large amounts of data? I have heard of references to "splitting" tarballs, I guess this might be a solution?

Thanks in advance for any advice/solutions.

Dan

---

### Post by flippo on 2010-02-13
I've never backed up an encrypted partition before, but there are some basics of compression which are working against you in it.  Compression is based on finding patterns in the binary.  If the file your compressing is completely random compression will actually make it larger.  Encryption attempts to randomize information in a way that it cannot be deciphered, therefore you may have some issues compressing an encrypted drive.  I'm not entirely sure, but it seems to be whats happening to you.

An easy workaround is to compress everything but your encrypted system, then just back up the exact data (cp -a) thats encrypted.  It will be exactly the same size of your home directory, but it should work.

---

### Post by danielstrong52 on 2010-02-13
Ah, I can see that might be a problem. I'll give that a try, but there's just one thing I'd like to clarify first... I suspect this question may be due to my limited, or perhaps void, understanding of encryption, but I tried compressing a directory in my home folder to see whether it would actually get bigger. The file I archived was called lib, and contained a few folders of very (very) short and basic python programs (I am in the process of taking a stab at programming...). It was originally about 100kB and went down to 10kB when compressed using bzip.
The thing that made me think about this in the first place was the point at which my backup froze up. It was compressing, as I said, a load of files in the /home/.ecryptfs/dan/.Private folder. There files were of the general style of
ECRYPTFS_FNEK_ENCRYPTED.bunchofnumbersandletters-anotherbunchandbetween2and3hyphensattheend
Are these files, as I thought, encryption keys? I can see how these would be very randomized, but wouldn't the directories that are encrypted be so also? Shouldn't lib, being part of my encrypted home folder, be larger when compressed?

Sorry if this is all a little trivial, but apart from any practical implications, my curiosity has also been sparked ;)

---

### Post by flippo on 2010-02-13
To be honest, I'm not sure.  I've never used an encrypted home folder personally, nor have I knowingly attempted to compress encrypted information.  It sounds like the directory thats giving you troubles is the /home/.ecryptfs/dan/.Private directory, which may be full of private/public keys (look up public key cryptography on wikipedia for more information), but that is just a guess I don't know how an encrypted home folder is actually implemented.  It would make sense that if it is full of keys it wouldn't compress well, I would add that to the list of directories to be excluded and try compressing the whole thing again.

---

### Post by danielstrong52 on 2010-02-13
Ok, I'll give that a go, and submit how it went tomorrow. Thanks for the help!

---

### Post by danielstrong52 on 2010-02-15
Yep, worked fine: I archived the filesystem with bzip, excluding the .ecryptfs folder in /home/, and then archived that into an uncompressed tarball. About 7G in total.
Thanks for the help!

---

