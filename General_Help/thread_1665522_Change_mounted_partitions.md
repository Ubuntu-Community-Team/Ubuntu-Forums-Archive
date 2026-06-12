---
title: "Change mounted partitions"
date: 2011-01-12
forum: General Help
---

### Post by foofi22 on 2011-01-12
Hi

I'm not sure if the title is an accurate overview of the problem, I'm not fluent in the lingo.

Anyway I now have 10.04 installed and have 2 partitions, one for / and the other for swap.

I upgraded recently from an old version to 10.04 (using full distro disk) and unfortunately missed a few files when doing backups which are now presumably lost for good.

What I want to do is move to three partitions with the third being /home which should avoid losing files in this manner again.

Is it possible to do this without reinstalling (I assume it is!) and if so, how?

Thanks

---

### Post by tredegar on 2011-01-12
This is a common problem, and it is easy to solve.
Here's a [link]("http://blogs.pcworld.co.nz/pcworld/tux-love/2010/09/hidden_linux_moving_home.html") for you, but there are many other HOWTOs out there.

---

### Post by foofi22 on 2011-01-28
Thanks for the link - I've found a few more useful ones too.

One question I do have is how much space do I need for / ?

I have 22GB to use (I'm not going to have a swap partition as I don't use it)

I don't install a great deal more than the basic install - should I just work out the size of / minus the size of /home and set it to that + 1GB or so?

Thanks, any advice appreciated.

---

### Post by tredegar on 2011-01-28
I count on 4-6GB being good for / depending on the distro and how much stuff I am likely to install.
**/home** gets the rest.

---

### Post by vanadium on 2011-01-28
I recommend against a separate /home partition for a disk space so small. Your much better bet to avoid losing data is to have a frequent backup of your user data. this will also safeguard your data against a disk failure.

If you want to follow the link given anyway, then make sure that you mount you partitions using the UUID rather than the device name. More and more commonly, device names can change between boots. This is why you should refer to a partition by its unique UUID.

---

### Post by srs5694 on 2011-01-28
My usual recommendation is 5-20 GiB for root (/), 1 to 2 times the system's RAM size for swap, and the rest for /home. If you've got only 22 GB (20.5 GiB) free, that makes creating a separate /home partition a bit iffy. You could do it, of course, and if your installation is minimal, a 5-8 GiB root (/) partition would probably be adequate, leaving you about 10-15 GiB for /home. Good backups, as vanadium suggests, would be another option.

Given the cost of hard disks today, you might consider supplementing or replacing your hard disk; you can get a 1 TB drive for a little over $50 these days (there's one at Newegg for $45, but shipping brings the cost to a bit over $50).

---

