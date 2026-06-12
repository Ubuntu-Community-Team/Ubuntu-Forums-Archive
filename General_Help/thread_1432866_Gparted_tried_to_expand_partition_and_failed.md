---
title: "Gparted: tried to expand partition and failed"
date: 2010-03-18
forum: General Help
---

### Post by maghoxfr on 2010-03-18
I wanted to expand the Ubuntu partition, on a previous [thread]("http://ubuntuforums.org/showthread.php?t=1426476") I've been told how to do that. So I followed the [documentation]("https://help.ubuntu.com/community/HowtoPartition") of GparteD (and [here]("https://help.ubuntu.com/community/HowtoPartition") too) but it's way easier to shorten a partition than expanding it.

On the documentation is not really clear on how to do the latter. What I did was:

[LIST]
[*]I shortened the partition I had for storage issues.
[*]I removed the "keys" from the swap partition.
[*]I moved the swap so the free space would be located next to my         ubuntu partition.
[/LIST]
Here the first problem arised: the free space, the swap and the storage partition instead of being individually are all subparts of a new partition?

So I shortened that new multi-partition and resized (expanded) my ubuntu partition. An error jumped. When I want to put back the keys to the swap it liks it to the multi partition instead of the ubuntu one.

Now I am like this (and still getting the notification of lack of disk space): see thumbnails.

I really apologize if this uniteligible but please ask me anything! Thank you

---

### Post by zvacet on 2010-03-18
Delete swap and partition nex to it (~8GB) and extend your sda6 to that free space.Afte that shrink sda6 from right to left and make new partition.And at last make swap partition on the end.

---

### Post by maghoxfr on 2010-03-18
Thanks for the answer, just a question and I'll get my hands on it:
> Afte that shrink sda6 from right to left and make new partition.And at last make swap partition on the end.
out of that new partition is where swap will be located right?

---

### Post by audiomick on 2010-03-18
Hallo.
first of all, you would have an easier time if you were to do this from the live CD or using the gparted live cd
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Then you wouldn't have to worry about unmounting the partitions, except for the swap if using the live CD.

I gather you want more space for the partition /dev/sda3 where your Ubuntu system is.

It shouldn't be that hard to do. From where you are now, you need to

shrink (move the left border to the right) the data partition sda6 to make as much space available as you want for sda3

move the right border of the swap partition to the right until it is up against sda6
move the left border of swap until it has the size it should have.

this will leave the empty space as the first thing in the extended partition sda4.

move the left border of the extended partition sda4 to the right till it is up against the swap partition.

this will put the empty space outside the extended partition and adjacent to sda3. You should now be able to extend sda3 to the right to incorporate the empty space.


Bear in mind that you can save all your videos and whatever that is taking all the space in the Ubuntu partition to another location of your choice, e.g. that data partition that has 220GB free still. It is very easy in every Linux program I know to change the default storage path so that it automatically stores to somewhere other that /home/username.

---

### Post by maghoxfr on 2010-03-18
Thanks, I actually did this from the 9.04 live cd I have. I really don't have many things stored in /home but I have quite a lot of programs. I'll give it a try and come back, yesterday it took me like three hours but let's see. Thanks for the reply both of you zvacet and audio mick!

---

### Post by audiomick on 2010-03-18
> **maghoxfr said:**
> ... yesterday it took me like three hours but let's see....
Yes, it takes time. The tool has to shovel everything from where it is to where is has to go. That is a lot of read/ write operations.

---

### Post by sandyd on 2010-03-18
> **audiomick said:**
> Yes, it takes time. The tool has to shovel everything from where it is to where is has to go. That is a lot of read/ write operations.
I remember that time I had a RAID faliure after the great blackout of canada/us

It took me one day (24h) to rescue everything..... :|

---

### Post by maghoxfr on 2010-03-19
What I did was what zvacet told me because I could not do what audiomick said. I show my new state on the thumbnail. I have a partition (sda4) that has another one inside (sda5), you can see that the outerline is light blue and the inner is green. I can't shrink sda4. I can shrink sda5 though, but the free space would be inside sda4 also. I want to get sda5 out of sda4, shrink it and out the freed space create swap again.

Suggestions?
Thanks again

---

### Post by zvacet on 2010-03-19
Shrink sda5 from right to left and on that free space make swap.

---

### Post by audiomick on 2010-03-19
> **maghoxfr said:**
> What I did was what zvacet told me because I could not do what audiomick said. I show my new state on the thumbnail. I have a partition (sda4) that has another one inside (sda5), you can see that the outerline is light blue and the inner is green. I can't shrink sda4. I can shrink sda5 though, but the free space would be inside sda4 also. [COLOR=Red]I want to get sda5 out of sda4[/COLOR], shrink it and out the freed space create swap again.

Suggestions?
Thanks again
You can't. Sda4 is an extended partition, sda5 a logical inside that. This is a good thing.
Go and look here at the explanation of Primary and Extended/Logical partitons.

From where you are now, you need to shrink sda5 towards the end of sda4. Then you will be able to shrink sda4, which will put the empty space outside of sda4, then you will be able to expand sda3 into it.

This still leaves you without a swap partition. It is inadvisable to run without a swap space. You have the option of recreating a swap partition inside sda4 (i.e. recreating the one you needlessly erased) or creating a swap file later.

---

### Post by maghoxfr on 2010-03-19
Thanks, I'll do that, tomorrow I'll post the news...hopefuly good ones.

Very grateful for your help really

---

### Post by maghoxfr on 2010-03-20
Ok, I made some progress but I'm still having some trouble. I show below the thumbnail of my current situation.

I extended the ubuntu partition and created a new linux-swap one. But I get this message when opening ubuntu:

> One or more of the mounts listed in /etc/fstab cannot yet be mounted: swap:waiting for cuid=6c4061d5-6009-490a-ac1b-3201e53d4322/media/datos: waiting for /deb/sda6 press ESC to enter a recovery shell.

So I press esc and run ubuntu. It runs kind of slow, specially video. I couldn't link the swap partition to the ubuntu one with the keys icon because if I right click on the swap partition> activate interchange then it adds the keys icon to swap and sda4

---

### Post by audiomick on 2010-03-20
At a guess, the fstab is still pointing at the old swap that you removed, and you have to change it to point at the new one.

I haven't done this myself, so I can only offer you some reading on the subject. Have a look at this
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
_and_ the links at the bottom of that page to "UUID" and "how to fstab". I think all the information you need should be in there somewhere.

---

### Post by maghoxfr on 2010-03-20
Ok, I have a lot to read

---

### Post by audiomick on 2010-03-20
I think you should be able to make the necessary changes to fstab from the live CD if you have to, but I am not sure. Might be good to wait for some more advice.

ah, you edited whilst I was typing...

---

### Post by maghoxfr on 2010-03-20
yeah, sorry for that, I rushed. I restarted like 3 times and I could open the terminal. I think the problem is solved, here's what i did:

```
sudo mkswap /dev/sda6
```

it gave back an UUID number, I copied that number into the fstab file because the swap UUID number on that file did not belonged to the new file. To open the fstab:

```
sudo gedit /etc/fstab
```

I saved the changes (I should've backed the original file just in case but I didn't).

Then activated the swap and added it to the sistem:

```
sudo swapon /dev/sdaX
```

Finally I restarted. Here I show the thumbnails and I think they look good but I don't have an expert eye, do you think it's solved?

PS it's in spanish but the second one is a shot of the system monitor showing the ram and swap(2.4Gb).

---

### Post by maghoxfr on 2010-03-20
i'll wait for some replies in case the problem is not solved and if someones makes the call I'll label the thread as solved.

Thank you VERY VERY much!!!

---

### Post by audiomick on 2010-03-20
I think it is right. The size of swap that the resources thing is showing matches the size of your swap partition. If the computer is booting without any trouble, I'd say you've won.

---

### Post by maghoxfr on 2010-03-20
Yeah no trouble at all, thanks very much man. Now I'll be solving some audio configuration and sstart recording *finally!!!*

---

