---
title: "Ubuntu 10.10 Won't Suspend or Hibernate"
date: 2011-02-01
forum: General Help
---

### Post by MandoJM on 2011-02-01
Hello, I have an  Asus U43F With Ubuntu 10.10 Installed and Everytime I  Try To Suspend  Or Hibernate The Screen Turns Of And Quickly Gets Back  On.. I Read it  was something about the USB 3.0 But I Don Know How to  solve it. Can  Anybody Help Me? I Tried Doing The Option of When I Close It That It  Does Suspend But It Doesn't Work...

---

### Post by mikewhatever on 2011-02-01
To make sure it's really usb3 that prevents suspending, try unloading the xhci module first, then suspend.
```
sudo rmmod xhci
```
If it works, blacklisting the module would be a solution for Maverick. Usb3 should be working well with Natty, the next Ubuntu release.
Edit: Here is a solution without blacklisting.
[http://ubuntuforums.org/showpost.php?p=9117597&postcount=6](http://ubuntuforums.org/showpost.php?p=9117597&postcount=6)

---

### Post by MandoJM on 2011-02-01
How do i do the thing from the link?

---

### Post by MandoJM on 2011-02-01
i created the file but i cant move it to the sleep.d folder because i dont have some permissions. anybody know what to do about this?

---

### Post by drewsus on 2011-02-01
How much RAM do you have and how big is your swap space?

---

### Post by MandoJM on 2011-02-01
how do i check that?

---

### Post by drewsus on 2011-02-01
Open System Monitor and on the first tab you can see your RAM. Open Disk Utility and you should be able to find the size of your SWAP partition. 
Your SWAP space should be double your RAM to achieve what you desire.

---

### Post by MandoJM on 2011-02-01
I See The RAM size That is 3.7 GB And Swap Is 13 GB

---

### Post by MandoJM on 2011-02-01
Forget It.. I Found A Solution In Another Thread That Took Me Here. [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)
But Thanks Anyway! :)

---

### Post by mikewhatever on 2011-02-02
Thanks for posting your link, and sorry for not being around, I had to go to bed yesterday.

---

### Post by Deeday on 2011-02-22
> **drewsus said:**
> How much RAM do you have and how big is your swap space?

Hi drewsus,

do you mean that it matters?

I've just put more memory into my laptop, from 1 GB to 2.4 GB, but left the swap partition as it was, at 1.7 GB.

Roughly around the same time, the Suspend function stopped working: computer hanging with blank screen (blinking cursor in the corner).

Do I have to increase the swap partition? My typical memory usage is very modest, currently rarely above 30% and 0% swap, and when I put it on Suspend, the memory usage is never above 400 MB: does it still need a bigger swap?

Cheers.

---

### Post by drewsus on 2011-02-22
Yeah, your SWAP space should be at *least* 2x the size of your RAM if you want to use suspend and especially hibernate.

---

### Post by Deeday on 2011-02-25
Thanks drewsus. Yes, it was indeed the swap area that needed some bigging up. I got away with with less than 2x the size of RAM though.
Currently I've got 2.4 GiB of RAM and 4.5 GiB of swap and it suspends OK, although when I do that I usually never have a large memory usage.

Cheers.

---

