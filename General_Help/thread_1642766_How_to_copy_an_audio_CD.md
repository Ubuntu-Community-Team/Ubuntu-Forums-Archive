---
title: "How to copy an audio CD"
date: 2010-12-10
forum: General Help
---

### Post by BobvanderPoel on 2010-12-10
I'm not at all a beginner ... just frustrated.

Nor do I have a dated computer. 4gig ram, dual core AMD processor, 2 DVD-RW drives.

And, the most current and updated Ubunutu 10.10.

I attempted to do a simple little thing today ... copy an audio CD. Yeah, right.

Took about 3 tries before I finally got it. And, I think the problem is with Gnome and the fact that it tires to be smart (or maybe it's me that is trying to be smart).

Try 1. Insterted a blank in DVD-RW 1 and the source in 2. Got the popup about a new cd being detected, etc. and selected K3B to do the copy. Now, K3B first off did not see the blank disk, so I just told it do a single drive copy. Then, it asked me about killing off some existing programs which were accessing the disk. Fine, let's just do it. After the disk was read I was prompted for the blank. So, took it out of drive 1 and put it in #2. Nope, just keep looping with the <load>, <eject> popup. So, I quit K3B, and (to make sure) logged out and back in.

Try 2: Used Brasero. Again, tried to use 2 drives. This time both drives were recognized. The read was done and the new disk was written. But, got a error message. Told it to write the error log, but it never did find that (or if it did, I never was able to find it). And, yes, the disk was a coaster. Okay, never did have success with Brasero in the past ...

Now I'm a bit ticked off :)

Logged into KDE4. Inserted my new blank and the original. And, yes!!!, K3B worked flawlessly.

But, I really don't like KDE4 :) Let's not argue about that (but I think it's slow and bloated). So, can it be done in Gnome?

There must be a magical sequence of commands to follow or a unpublished sequence to insert my disks. Does anyone have success in doing 2 drive copies in Gnome?

Sorry if this is a bit of a rant ... but it was very frustrating. Not to mention that the person who I was copying the disk for runs a Mac and was quite amused by it all.

---

### Post by tommcd on 2010-12-10
Gnomebaker should be able to do this. Gnomebaker has always worked better for me than Brasero. See this documentation on Gnomebaker:
[https://help.ubuntu.com/community/GnomeBaker](https://help.ubuntu.com/community/GnomeBaker)
> Copy Data CD - Opens a new window that allows a computer with two useable CD Writing drives and appropriate media to copy the data from one to the next. One drive must hold a disc with the data to be copied, other should hold a blank disc.
Copy DVD and Copy Audio CD - Same as previous, except with minor variations to be explained below. ...

I only have one optical drive, so I can not test this.
Hope this helps.

---

### Post by BobvanderPoel on 2010-12-10
Thanks. 

Question: Do you insert the disk-to-be-copied and wait for the media-finder-thing to pop up the "what to do" question ... or do you start gnomebaker and then put in the disk?

BTW, I'm trying it right now and it seems to be quite slow in reading the source disk ... K3B appears to be much fast. Note sure without doing a timing.

---

### Post by tommcd on 2010-12-10
> **BobvanderPoel said:**
>  
Question: Do you insert the disk-to-be-copied and wait for the media-finder-thing to pop up the "what to do" question ... or do you start gnomebaker and then put in the disk?

You will have to try it both ways. I can not be sure about this since I have only one optical drive.
It should not matter much either way I would think.

---

