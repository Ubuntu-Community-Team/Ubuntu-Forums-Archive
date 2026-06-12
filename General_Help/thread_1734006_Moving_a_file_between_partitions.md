---
title: "Moving a file between partitions"
date: 2011-04-19
forum: General Help
---

### Post by ClientAlive on 2011-04-19
My temp file is currently located int the root partition which is a a relatively small partition. As it is, if my root partition id more than half full I am unable to make a backup of the whole system. I would like to move that folder into the home partition and maybe even make it a hidden folder. Since a lot of apps depend on the other folders within the temp folder - what I am wondering about is whether I can just move the folder or if I need to be concerned that those apps will not be able to find the folder then. Would I end up needing to go into every app that uses it and change settings? Is there things within the o/s that use it that I would need to reconfigure or something?

Thanks in advance for your helpl

Jake

----------------------------

Ubuntu 11.04 with the Unity Desktop on a HP ze2000

---

### Post by RHTopics on 2011-04-19
Jake,

Are you referring to the /tmp directory?

---

### Post by lmarmisa on 2011-04-19
I think this link could help you:

[http://ubuntuforums.org/showthread.php?t=945595](http://ubuntuforums.org/showthread.php?t=945595)

---

### Post by ClientAlive on 2011-04-19
> **RHTopics said:**
> Jake,
 
 Are you referring to the /tmp directory?
 
 

Yes. The file that if you go to it the gui way you would click your home  folder then "File System" and it is in there and named "tmp". If you go  to it the cli way you would use the absolute path:

```
 cd /tmp/ 
```I also am just taking a guess that I have the correct diagnosis so maybe  I should be more sure before I do anything. All I know is last night I  tried to make a backup of my entire system using k3b. It got most of the  way through creating the project then said there wasn't enough space. I  assumed it was because it is using a temp folder of its own in the tmp  folder to store the project and then burn it.

Since basically the whole system and the tmp folder are in the same  partition (home folder has very little space used right now) - and since  it is over half the - and since  it is over half the available space for the partition it is in, there  was not enough room to  double the amount of data in order to do the job.

If my diagnosis is correct - and that's a big if - then moving the tmp  folder to the home partition (which is much larger) should set me up  just right in the future. I need to be sure though and I am not certain how to find out. I'll have to think about it I guess.

By the way - the entire system is 4.4 gig and the partition for root is 7.63 gig. Home partition is 27,71 gig though.

> **lmarmisa said:**
> I think this link could help you:
 
 [http://ubuntuforums.org/showthread.php?t=945595](http://ubuntuforums.org/showthread.php?t=945595)
 
 
Thanks, I'll read that now.


Jake

----------------------------------------

Edit - Update:

> **lmarmisa said:**
> I think this link could help you:
 
 [http://ubuntuforums.org/showthread.php?t=945595](http://ubuntuforums.org/showthread.php?t=945595)
 
 

I read that thread and it seems like they are talking about my same  situation but it's like they're talking in a foreign language with all  that code talk. I'm very new to this - remember? Oh, guess I didn't  mention that. Sorry. Yeah, I've been at Linux for about a month now. I'm  learning but its a lot to take in.

They said something about "fstab" and I wanted to know what that was so I  looked on google linux for it. The only article I saw so far is from  like 5 years ago and I'm not sure if it is still relevant. I had heard  something like they changed some things in the kernel between then and  now. Not even sure what that is all about but it makes me wonder.

Thanks
Jake

Oh, this is the link to the article I looked up - so far.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

And

[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

---

### Post by RHTopics on 2011-04-20
Jake,

If K3B is the only thing that is having problems with /tmp, then you can change the location of the temp directory in K3B preferences.  Make a new directory in your home directory (i.e. /home/jake/k3btmp) and then change to this directory in K3B preferences.

---

### Post by ClientAlive on 2011-04-20
> **RHTopics said:**
> Jake,

If K3B is the only thing that is having problems with /tmp, then you can  change the location of the temp directory in K3B preferences.  Make a  new directory in your home directory (i.e. /home/jake/k3btmp) and then  change to this directory in K3B preferences.




That's a great idea! That would be perfect since I think burning stuff is the only activity that eats up so much space. Well the only one I do anyway. I didn't know k3b had a way to configure the temp folder like that. I should have though.

One last question ok? I'm not sure this folder is something I want to look at all the time when I open my home folder. Is there any way I can hide it or something - and still be able to access it if I needed to?

Thanks
:)

---

### Post by RHTopics on 2011-04-21
Good to know that approach works for you.

> One last question ok? I'm not sure this folder is something I want to look at all the time when I open my home folder. Is there any way I can hide it or something - and still be able to access it if I needed to?

You could make the temp directory right under /home rather than /home/"user id"/
 and then change the permission on this directory so you have full access to it.

The commands to do this are:

```
sudo mkdir /home/k3btmp
sudo chmod ugo+rwx /home/k3btmp

```
Then change to this directory in k3b preferences as your temp file location.

---

### Post by ClientAlive on 2011-04-22
> **RHTopics said:**
> Good to know that approach works for you.



You could make the temp directory right under /home rather than /home/"user id"/
 and then change the permission on this directory so you have full access to it.

The commands to do this are:

```
sudo mkdir /home/k3btmp
sudo chmod ugo+rwx /home/k3btmp

```
Then change to this directory in k3b preferences as your temp file location.


Excellent. Thank you.

---

