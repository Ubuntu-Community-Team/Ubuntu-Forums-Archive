---
title: "Wrote my research to windows partition while windows was hibernated."
date: 2011-07-13
forum: General Help
---

### Post by georcp on 2011-07-13
Hello

I Recently upgraded my ubuntu from 10.10 to 11.04, I backed up all my old stuff onto the windows partition.

Unfortunately my windows was hibernated. When I went into windows and back to ubuntu the backup folder was gone so were my backed up files.

I realise what a fool I was now, moving on how can I recover the files? Is it possible?

I installed testdisk from synaptic manager but have no idea how to open the program.


Please help, three months of masters work is on the line.

George

---

### Post by dino99 on 2011-07-13
here is how to make a secure installation (with /home for your data/settings):

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

testdisk:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

note: upgrading (meaning not formatting) never have destoyed data/settings, so dont really understand your problem

---

### Post by georcp on 2011-07-13
I formatted for a fresh install

---

### Post by dino99 on 2011-07-13
then use photorec if nothing else have been written on the partition

---

### Post by georcp on 2011-07-13
I did the photorec thing, it got alot of the windows stuff but little of the linux stuff. there was a 89GB png and most of the .pdf did not recover cleanly...

A disaster! 

Oh well...

---

### Post by Mark Phelps on 2011-07-13
For future reference ...

When Window Hibernates (and, Linux may do the same), it saves information such that, when the PC is restarted, it can return to exactly the state it was in when it was hibernated.

This includes the underlying filesystem.

So basically, when your machine awoke, it restored the Windows filesystem to the state it was in previously.

Also, this does tend to underscore the importance of doing backups.  For a few dollars, you can purchase a USB stick capable of holding several GB of data -- more than enough, I would guess, for a thesis.

Suggest you do that in the future and maintain your backups offline.

Also, it's a bunch of work, and it's likely NOT to do any good (but, you never know), but you can consider doing the following:
1) Disconnect your drive from your PC
2) Using an MS Windows PC, download and install GetDataBack for NTFS from Runtime Software.
3) Connect your drive to the Windows PC
4) Run DetDataBack using the mode that does the in-depth searches.  Probably best to let it run overnight.
5) Check the logs and see if it found your thesis.

If it did, you will have to buy it to actually recover the thesis -- but what is three months work worth?

---

### Post by georcp on 2011-07-16
I did something like that in the end luckily my labmate had software that undeletes stuff, nearly all the files were there... much to my relief.

I learned the hard way about hibernation. 

Recovering the data is a mission and requires another computer,and you get all the other windows deleted folders...

I am just glad i can get on with life. I am backing up to the cloud and syncing with another pc, hopefully this should not happen again....

Thanks for your responses.

---

