---
title: "How to recover ecryptfs from other partition"
date: 2010-11-03
forum: General Help
---

### Post by Crazedpsyc on 2010-11-03
I recently had to install ubuntu 10.10 through wubi because my olde ubuntu broke after a failed upgrade. Now I am quite happy with everything in 10.10 except I can't get to the files in my olde home folder because I chose the home folder encryption option in the installation process. How can I recover my home folder? I tried several guides but none worked. They all seemed to be recovering from another user not another partition.

---

### Post by deinonychai on 2010-11-04
I found myself with a very similar problem tonight.  Long story short: I had my /home folder mounted on a different drive/partition than my / files.  I had to reinstall all my / files on a third partition, because I was co-opted into installing Windows 7 (which, bless its soul, simply would NOT install on any partition other than the one I had my Ubuntu / files on!)  Ideally, I would have had all my /home files ready to go when Ubuntu booted up, but... I'd encrypted the drive.  The drive showed up, alright, but with only a pile of wonderfully encrypted files.

So, after a half hour or so of fiddling around, here's what I did.  It seemed to work, and hopefully it works for you too.  Everything that I'm about to type assumes that you already have your old encrypted drive mounted, or that Ubuntu recognizes that it has been mounted.  Ubuntu recognized my folder, so I didn't actually do anything to get it up and visible.  Hopefully that's the case for you as well.  Anyhow, here's what I did:

1-  I needed to recover my passphrase, as I hadn't written it down at all.  I'd *assumed* it would just be my sudo passphrase, but that wasn't the case; I could see, when I looked at the "Private.sig" file (which for me was located in /media/"Drive Name"/.ecryptfs/"user"/.ecryptfs/Private.sig), that the numbers I got in step #2 weren't the ones I should have gotten.

So, to recover my passphrase, I opened up a terminal and typed in:

ecryptfs-unwrap-passphrase /media/"Drive Name"/.ecryptfs/"user"/.ecryptfs/wrapped-passphrase

It asked for a passphrase at this point, and I just typed in the sudo password I used when that drive was still my /home folder.

And that gave me my mount passphrase.  With the mount passphrase, I then did the following:


2- Typed: sudo ecryptfs-add-passphrase --fnek 

I was then prompted for a passphrase, and gave the mount passphrase I'd received from step #1.

After doing that, the terminal fed me back some dialogue:
[INDENT]
Inserted auth tok with sig [846db420b857e761] into the user session keyring
Inserted auth tok with sig [9acfebe8401e72ec] into the user session keyring[/INDENT]

I double-checked these against that Private.sig file I mentioned above, and they were the same.  A good sign.


3- I copied down the second number (9acfebe8401e72ec), as it becomes important in step #7


4- In my home folder, I created a new folder called "Temporary."  You can call it whatever you like, really... it's just a spot where you're going to mount the encrypted files.


5- Typed: sudo mount -t ecryptfs /media/"Drive Name"/.ecryptfs/"user"/.Private /home/username/Temporary

The first location should be the same as the spot where your old encrypted home folder is currently located (/media/"Drive Name"/.ecryptfs/"user"/.Private for me... should be pretty universal).  The second location is where you're going to want to send the files.


6- Next, ecryptfs asked me a few questions, but it already had most of the correct answers filled in:

[INDENT]Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y[/INDENT]

I just had to hit enter for the first three, because they were already good to go.  The fourth one I needed to change, as it defaulted to "no."  In most cases, it should be a "yes."

7- Next, I was prompted with:

[INDENT]Filename Encryption Key (FNEK) Signature [846db420b857e761]:[/INDENT]

So, I grabbed the number I'd copied down before (9acfebe8401e72ec) from steps 2 & 3, and entered that in.


8- Next, I was prompted with a warning: 

[INDENT]WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? :[/INDENT]

I chose yes, as the passphrase was most definitely correct.  The terminal then asked:

[INDENT]Would you like to append sig [846db420b857e761] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? :[/INDENT]

I declined, as I was pretty sure there wouldn't be a next time.


9- I navigated on over to my ~/Temporary folder, and lo and behold: all of my files were there.  Now, I'm just in the process of moving them around and getting everything straightened out.

---

### Post by Crazedpsyc on 2010-11-04
Everything up to the last step went exactly as you said. when I tried to mount it I got:
```
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [48b2ec3298b9f44e]: 0a0a1b67fc6bc1c1
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=0a0a1b67fc6bc1c1
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=48b2ec3298b9f44e
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [48b2ec3298b9f44e] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>

```I tried the mount password I got, my old root password, my current root password, and the second number for the password here but I think it wants something else. Thanks for the great try though!

EDIT: Now i see the problem. Why isn't it accepting my "FNEK" key? 
> Would you like to append sig [**48b2ec3298b9f44e**] to

---

### Post by deinonychai on 2010-11-04
The error:

[INDENT]Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://launchpad.net/ecryptfs>[/INDENT]

This should only come up if either the directory you're trying to *mount*, or the directory you're trying to mount *to* don't exist.  So, if you either got the encrypted volume drive location wrong, or are trying to mount to a folder that doesn't yet exist - either because you haven't yet manually created the folder you're trying to mount to, or have typed it in incorrectly - you'll get that error.

It's basically telling you that one (or both) of the two locations you're trying to perform a mount command on do not exist.

If your FNEK keys are identical to the ones in your Private.sig file, you should be good to go on that account.  The terminal will return you the first value listed in that file, and will expect you to type in the second value.  The error you listed, though, is just an error that gets returned when the file location specifications are wrong.

---

### Post by Crazedpsyc on 2010-11-05
I checked all the file locations, Yes I used "mkdir ~/Temporary" first, and the only other thing I can think of that would make the paths wrong is I mounted my entire old partition, not just my home folder. I think the problem is that it is somehow not recognizing my FNEK key, although is is exactly the same as the one in Private.sig. Instead it is using the one it would assign to me now if I encrypted my new home folder (Which I have decided not to do this time). As my previous post shows, I entered the correct FNEK key, but when it verifies my information, it shows the default instead of the one I entered. I did enter my key both with Ctrl+Shift+V and manually typing, so I don't think it is a problem with pasting it in. Which password should I use for that last step though?

---

### Post by deinonychai on 2010-11-06
I think I may have typed in the wrong path on step #5... which, while it may not make a difference for you if your .Private folder is in a different location (and it may well be), it will return the error code you keep getting if your .Private folder is in a similar location.

Just to highlight the change:

I initially had "/media/"Drive Name"/"user"/.Private" listed as the location of the folder, when it REALLY should be "/media/"Drive Name"/.ecryptfs/"user"/.Private"

So, sorry for the confusion there.  But make sure to double-check the correct location of your .Private folder on the mounted drive, as you really shouldn't be getting that specific error for any reason other than an incorrect path.

If the FNEK key seems fine.  You'll see on my post above that ecryptfs did the same thing to me when verifying information: that is, it asked if I wanted to append the initial value (846db420b857e761), and not the value I entered in (9acfebe8401e72ec).  The drive still mounted correctly in spite of this.

And just to verify, I tried mounting the drive with an incorrect FNEK key.  What happened was that my drive *mounted* correctly, but didn't *decrypt* at all.  So basically, in my /home/"user"/Temporary folder, I wound up with an exact duplicate of what is currently visible in my current /media/"Drive Name"/.ecryptfs/"user"/.Private folder: a bunch of files and folders with encrypted names and inaccessible content.

As for the password you're asking about: which step are you referring to?

---

### Post by deinonychai on 2010-11-06
An easy way to check if your paths are all correct, I guess, would be to do the command without the "ecryptfs -t" part... to just do a "sudo mount" that is.

If you get an error saying that the special device doesn't exist, you know something is wrong with the folder to be mounted you have in mind.  If you get an error saying that the mount point doesn't exist, you know something is wrong with the mount point path.  If you get a generic error saying that you're not trying to mount a block device, you know the paths are all ok.

Basically, ecryptfs is just trying to decode information for you.  When it returns an error saying that there is no such file or directory, it's getting this information from the "mount" part of the command... it's looking for something to mount (and later decode), but can't find anything at all in the spot you've told it to look.

---

### Post by Crazedpsyc on 2010-11-06
I tried mounting the same path without -t ecryptfs, and it said the path didn't exist, so I checked it and found that "home/" was missing. I added this and tried it again and mount told me it was not a dev block file, which is as close as I can get because it really is not a dev block file. I retried the -t ecryptfs part and I still got the same exact error. 

Here are a few more ideas that might help:
Do I need to mount /media/device/home/ separately from /media/device?
Does "device" need to unmounted so I can use something like mount -t ecryptfs /dev/sdb1/home/?
I mounted my old home partition before while trying an ubuntu guide to fix this issue, but I can't remember how.
Is there any way to forcibly decrypt it with a cracker tool? It's only 16 bit encryption, but I have never heard of a cracker that works on entire filesystems.

---

### Post by mwshook on 2010-11-07
Thank you, thank you!

I had this exact same problem, and was about to give up. I had to add some sudos here an there because of permission issues, but your instructions worked perfectly.

---

### Post by deinonychai on 2010-11-08
Ah!  Wonderful!  I'm glad the instructions worked for you.  Now, to try to figure out why they're not working for the OP.

---

### Post by deinonychai on 2010-11-08
Now, onto the questions...

"Do I need to mount /media/device/home/ separately from /media/device?"

No, you shouldn't have to.  What you're wanting to do is mount *just* the /.Private folder into a temporary location, and then decrypt it.  Mounting both /media/device/home/ and /media/device shouldn't be necessary, as long as all folders within /media/device are accessible.  So, if you can browse all directories and files in your encrypted drive, you should be good to go.


"Does 'device' need to unmounted so I can use something like mount -t ecryptfs /dev/sdb1/home/?"

No, it doesn't need to be.  The instructions above actually assume that the device is already mounted prior to running these commands.  The "mount" portion of the commands is simply trying to mount the /.Private folder in a new location (which can be done without decrypting it).

Of course, you can always try unmounting the device and mounting it again in a different location, but the ecryptfs commands should be run *following* a successful mount of the drive, and not for the purpose of a successful mount of the drive.  If that makes any sense.


"Is there any way to forcibly decrypt it with a cracker tool? It's only 16 bit encryption, but I have never heard of a cracker that works on entire filesystems."

I'd imagine it's possible, though I haven't a clue what direction I'd point you in.  Depending on the size of the drive, even 16-bit encryption could take you quite some time to decrypt.  Of course, a timely procedure that works is always better than anything that doesn't work, so if you get some success down that road, make sure to post an update.

Question for you: when you ran the "mount" command without the "ecryptfs" part, were you able to see your /.Private folder in the spot you'd mounted it in?  If the mount went as it should have, the folder should have become visible, with all of its encrypted files and folders still encrypted.

---

### Post by Crazedpsyc on 2010-11-08
No I just got an error message saying 
```
mount: /media/63509a24-2036-4eee-ad6b-def338fb85a5/home/.ecryptfs/mike/.Private is not a block device

```Which as far as  I know means it is not mountable because it is not an external device or partition in itself like /dev/sd* and /dev/hd* are. And yes I can see all the encrypted folders there (all starting with ECRYPTFS_FNEK_ENCRYPTED.FXY80Vhbz4j.kETicU1TuhYS-zrvEmw3J5...)

---

### Post by Crazedpsyc on 2010-11-11
Still looking for s solution here

---

### Post by Crazedpsyc on 2010-11-15
and I still am. 
bump

---

### Post by Crazedpsyc on 2010-11-16
I have two new ideas.
1. Can I manually install/up/downgrade some necessary packages to get recovery mode working?(manually install meaning extract the .deb file and copy the files to the right places on the old partition)
2. Can I temporarily set bash or zsh to use only files from the old partition (not just reset that PATH but also the directories the commands use for configuration)

and also brining back my old idea, How can I crack the encryption? I need a program or a live CD. I hear cracking encrypted partitions is actually rather easy, but I need the right tool. Anybody know of a good one?

---

### Post by Crazedpsyc on 2010-11-17
Bump
I have made little progress with the cracking option

---

### Post by Crazedpsyc on 2010-11-18
And another bump with no progress
:(

---

### Post by Crazedpsyc on 2010-11-20
Still Nothing but the recommendation of finding a recovery cd like knoppix or an "offensive security" distro like BackTrack

---

### Post by Crazedpsyc on 2010-11-22
Bump.

---

### Post by Crazedpsyc on 2010-11-24
And another bump

---

### Post by Crazedpsyc on 2010-11-29
Finally, _***BUMP***_
*Sigh*

---

### Post by IpomeaWebSolutions on 2012-04-17
Hi guys,


  I have a similar problem with encryptfs. I’ve upgraded the server from Ubuntu 9 to Ubuntu 10.
  Now when I try  to recover data using the command ecryptfs-recover- private
I receive an error message that say , unable to find Private.sig.
  This file does not exist into the server. But I never delete it.  
  How can I recover the encrypted files?
   This is the error message (partial in Italian):
  [EMAIL="root@ipomea-server:/mnt/home/.ecryptfs/ipomea/.ecryptfs"]root@xxxxx-server:/mnt/home/.ecryptfs/xxxxx/.ecryptfs#[/EMAIL] ecryptfs-recover- private
  INFO: Searching for encrypted private directories (this might take a while)...
  INFO: Found [/mnt/home/.ecryptfs/xxxxx/.Private].
  Try to recover this directory? [Y/n]: y
  INFO: Enter your LOGIN passphrase...
  Passphrase: 
  Inserted auth tok with sig [43db47xxxxx066b] into the user session keyring
  sed: impossibile leggere /mnt/home/.ecryptfs/xxxxxx/.Private/../.
  ecryptfs/Private.sig: File o directory non esistente [EMAIL="root@ipomea-server:/mnt/home/.ecryptfs/ipomea/.ecryptfs"]root@xxxxxx-server:/mnt/home/.ecryptfs/ipomea/.ecryptfs#[/EMAIL]

---

