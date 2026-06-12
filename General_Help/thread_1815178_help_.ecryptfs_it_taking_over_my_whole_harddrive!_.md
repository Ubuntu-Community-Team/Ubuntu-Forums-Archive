---
title: "help .ecryptfs it taking over my whole harddrive! This could also be happening to you"
date: 2011-07-30
forum: General Help
---

### Post by Isaacgallegos on 2011-07-30
It seems to be copying everything in my home folder! It's suppose to be encrypting my files, but I don't need that. My home folder is already encrypted. I don't need two copies of the same thing. 


1) Can I just delete this? I found no answers on if I can just delete files from this. I'm in the middle of school and cant afford to break my whole system right now! Please help!

2) How do I stop this assault on my system? 

3) What mistake did I make that caused ecryptfs to take over my system? It's 50% (a bit less now that i've looked again, but close to 50%) of my whole harddrive. When did I enable this thing? 

4) Check to see if this is happening to you in /home/.ecryptfs

---

### Post by bodhi.zazen on 2011-07-30
LOL

This is normal behavior for Ecryptfs.

You have essentially two copies of the data , one encrypted and the other decrypted.

See man ecryptfs or [http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

---

### Post by Isaacgallegos on 2011-07-30
Why thank you, but I can't find any of my answers there.

But that page does give me a new question: 
So this is the only option when you "encrypt home folder"? It takes up twice as much space on your harddrive?!? 

Someone please tell me, THIS IS MY ONLY COMPUTER! I'm deleting tons of work I've done trying to fix this mess and keep my system floating. 

CAN I DELETE THIS ENCRYPTFS FILE WITH OUT BREAKING EVERYTHING!?!?!? PLEASE TELL ME!!!!

---

### Post by bodhi.zazen on 2011-07-30
> **Isaacgallegos said:**
> Why thank you, but I can't find any of my answers there.

But that page does give me a new question: 
So this is the only option when you "encrypt home folder"? It takes up twice as much space on your harddrive?!? 

Someone please tell me, THIS IS MY ONLY COMPUTER! I'm deleting tons of work I've done trying to fix this mess and keep my system floating. 

CAN I DELETE THIS ENCRYPTFS FILE WITH OUT BREAKING EVERYTHING!?!?!? PLEASE TELL ME!!!!

Yes ecryptfs keeps essentially two copies of your data, one decrypted in your home direcory, and the second encrypted . The specifics are going to vary a bit by version of Ubuntu.

Yes if you delete .ecryptfs you will break ecryptfs and loose data.

If you do not want this, back up your data, make a new user, and restore your data from back up.

How large is your hard drive ? Perhaps it is time for you to look at additional storage or backing up to CD / DVD ?

---

### Post by Isaacgallegos on 2011-07-30
I'm on a netbook with 15 gigs. I might have to drive to a friends house or something then never encrypt my home folder again... Major bummer. 

My home folder is 7.3 gigs *2 with encrptfs . 

Thanks.

Solved: Reformat system.

---

