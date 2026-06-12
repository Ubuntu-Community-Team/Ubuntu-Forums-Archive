---
title: "Moving tmp to RAM - Performance Increase"
date: 2010-07-15
forum: General Help
---

### Post by johnathanamber on 2010-07-15
Hello!

I've found this page:
[http://linux.aldeby.org/speed-up-your-ubuntu-linux-boot.html](http://linux.aldeby.org/speed-up-your-ubuntu-linux-boot.html)

I've followed several suggestions on my system and overall performance is better.

My question is related to the following:
> OPTIMIZATIONS NOT RELATED TO STARTUP

Move your temporary files /tmp folder to your RAM if you have loads of memory. This will also provide you greater privacy. Edit /etc/fstab and add the following line to it

tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0

Is this not normally implemented since some users don't have a lot of RAM?

Also, would it make that much difference if the system didn't have a lot of RAM to work with?

God bless,
Johnathan

---

### Post by cj.surrusco on 2010-07-15
> **johnathanamber said:**
> Hello!
My question is related to the following:


Is this not normally implemented since some users don't have a lot of RAM?

Also, would it make that much difference if the system didn't have a lot of RAM to work with?

God bless,
Johnathan

I'm sure that it is not implemented because Ubuntu tries to keep memory to the minimum. To answer your second question, if you don't have that much RAM, then it will take some kind of toll on other programs that are using the RAM.

I have at least 1GB that is almost never in use, so I'm going to try this now.

---

### Post by johnathanamber on 2010-07-15
I've got 3GB so I do not see that it would hurt my system but make it overall more enjoyable.

I've also been wondering about Gnome and other lighter weight desktop environments. But I am also concerned about compatibility with a majority of packages are made for KDE or Gnome. I was looking at LXDM.

Would everything working fine if you installed both Gnome and LXDM? Meaning would I still be able to use Gnome apps while using LXDM or another lighter Desktop manager?

I'm also working on scripts to make a minimal install... so the least amount of packages needed to do what I need is best.

Thank you and God bless,
Johnathan

---

### Post by ajgreeny on 2010-07-15
Have you seen [http://ubuntuforums.org/showthread.php?t=1525322](http://ubuntuforums.org/showthread.php?t=1525322) which talks about a distro with this enabled by default, Samiux

I keep thinking I might try it on my 10.04, but it's running so well that I just don't want to mess anything up, though I see no reason why it should not be reversible.

---

### Post by johnathanamber on 2010-07-15
Since it is a simply /etc/fstab edit... you can use nano or vi to make the change if for some reason it died during boot. If nothing else... use the Ubuntu LiveCD.

Still would like to know more about the different Desktop environments etc.

---

### Post by bodhi.zazen on 2010-07-15
> **johnathanamber said:**
> I've got 3GB so I do not see that it would hurt my system but make it overall more enjoyable.

The only potential problem I have seen with doing this (mounting tmp in RAM) is if you are doing something that is /tmp intensive.

Burning CD or in your case DVD comes to mind.

So long as you do not need that much /tmp space you should be fine.

Here are some potential suggestions, they seem to help

[http://blog.bodhizazen.net/linux/netbook-optimization/](http://blog.bodhizazen.net/linux/netbook-optimization/)

Edit : FYI much of that advice, as indicated on the page, is out of date. I suggest you look for more recent information.

---

### Post by johnathanamber on 2010-07-15
Another question... if you can use Gnome apps while on another Desktop Manager... what are the minimal packages needed?

Would this simply work:
*sudo apt-get install gnome*

---

### Post by johnathanamber on 2010-07-15
> **bodhi.zazen said:**
> The only potential problem I have seen with doing this (mounting tmp in RAM) is if you are doing something that is /tmp intensive.

Burning CD or in your case DVD comes to mind.

So long as you do not need that much /tmp space you should be fine.

Here are some potential suggestions, they seem to help

[http://blog.bodhizazen.net/linux/netbook-optimization/](http://blog.bodhizazen.net/linux/netbook-optimization/)

Ah, I didn't think about that... if your tmp is stuck in memory, then you are limited to the amount of RAM as to whatever you are doing. For instance if you are making a copy of a 4.7 GB DVD, but only have 3 GB, I assume it would never finish due to the RAM being full etc. Wonder if it gets full would it simply start to remove more info in RAM to accomplish the job?

If it did I would not see a problem even if you had less than 4.7 GB of RAM copying that DVD.

---

### Post by Skaperen on 2010-07-15
tmpfs can also swap out to swap space.  If you make your swap space larger, then what tmpfs gives you is basically a filesystem that starts in RAM and can move to disk, as opposed to regular filesystems that start on disk and get cached in RAM.  I've you have an overkill of RAM, like my 16GB machines, in many cases everything can be cached and the system can run like it were all tmpfs not using swap.

---

### Post by mcduck on 2010-07-15
> **johnathanamber said:**
> Hello!

I've found this page:
[http://linux.aldeby.org/speed-up-your-ubuntu-linux-boot.html](http://linux.aldeby.org/speed-up-your-ubuntu-linux-boot.html)

I've followed several suggestions on my system and overall performance is better.

My question is related to the following:


Is this not normally implemented since some users don't have a lot of RAM?

Also, would it make that much difference if the system didn't have a lot of RAM to work with?

God bless,
Johnathan

It's simply a question of what you do with your computer, and do you really have enough RAM to do all that. For basic desktop use that's probably not going to be a problem, but if you try to do anything that requires a lot of temporary data, you'll easily run out of RAM. For example any video editing can easily require anything from couple of gigabytes up to tens of gigabytes of temporary data. Unless you have tens of gigabytes of RAM, you'd be out of luck without being able to keep those files on your hard drive.

(I just did some basic editing on a 30 minute video file directory from a normal, Mini-DV camera, and ended with over 30GB of temporary files.. I _definitely_ don't have enough RAM to store all that data :D)

So, if you know for sure that anything you'll do with the system won't require large amounts of temporary data, then you can of course move /tmp to RAM. On the other hand, from a distro's point of view making such assumption wouldn't really work.

One more thing to consider is that if you really have enough RAM, then all the data from your /tmp will be cached on RAM anyway. So moving /tmp itself to RAM as well wouldn't make any difference apart from perhaps slightly improving disk read/write for other programs as the system wouldn't need to write temporary data to /tmp on the hard drive.

---

### Post by johnathanamber on 2010-07-15
So then if you have a lot of RAM and you move everything there... at what point do you not need swap? Also at what point does is it smart to move everything to RAM. For instance how much RAM should you use in that case at a minimum?

I guess it would depend on what you are doing.

Anyone have any good insight as to how RAM is used in Ubuntu?

---

### Post by bodhi.zazen on 2010-07-15
> **johnathanamber said:**
> So then if you have a lot of RAM and you move everything there... at what point do you not need swap? Also at what point does is it smart to move everything to RAM. For instance how much RAM should you use in that case at a minimum?

I guess it would depend on what you are doing.

Anyone have any good insight as to how RAM is used in Ubuntu?

As you indicated, it depends on what you are doing. 

If, as you asked earlier, you are burning a DVD, If you run out of memory (ram/tmp/swap) -> crash.

I advise you simply monitory how much RAM you use.

```
free -m
```

---

### Post by johnathanamber on 2010-07-15
When Ubuntu uses RAM, does it keep the entire file in RAM until it is finished with it? Or does it keep only the parts of the file that it needs?

I would assume it would be the latter...

---

### Post by mcduck on 2010-07-15
> **johnathanamber said:**
> When Ubuntu uses RAM, does it keep the entire file in RAM until it is finished with it? Or does it keep only the parts of the file that it needs?

I would assume it would be the latter...

That really depends on what you are doing. Some things might require all the used data in RAM, while other tasks can be done with small amounts of data at a time.

Think of it like the difference between watching a movie file on your computer versus watching a streamed video on a web site. The first approach requires you to have a fairly large, single file of data, but allows you to quickly move backwards and forwards and even jump to completely different places in the movie without any delay. On the other hand a streamed movie only requires small amount of data at a time, but moving to different locations in the video takes a lot of time as the video player needs to first find and get the required data for that part of the movie.

To make things more complex there's also the fact that all recently accessed data is kept in cache as long as there's enough RAM available to do that. So if you have lots of RAM, all the data will be kept in RAM anyway, even though the program might only use small parts of it at a time. This is the main reason why I personally see the idea of moving /tmp or any other temporary/cache directory to RAM rather pointless. If you have enough RAM to do that, you don't need to do it. :D

---

### Post by johnathanamber on 2010-07-15
> **mcduck said:**
> That really depends on what you are doing. Some things might require all the used data in RAM, while other tasks can be done with small amounts of data at a time.

Think of it like the difference between watching a movie file on your computer versus watching a streamed video on a web site. The first approach requires you to have a fairly large, single file of data, but allows you to quickly move backwards and forwards and even jump to completely different places in the movie without any delay. On the other hand a streamed movie only requires small amount of data at a time, but moving to different locations in the video takes a lot of time as the video player needs to first find and get the required data for that part of the movie.

To make things more complex there's also the fact that all recently accessed data is kept in cache as long as there's enough RAM available to do that. So if you have lots of RAM, all the data will be kept in RAM anyway, even though the program might only use small parts of it at a time. This is the main reason why I personally see the idea of moving /tmp or any other temporary/cache directory to RAM rather pointless. If you have enough RAM to do that, you don't need to do it. :D

I am sure as you know that the only point is to speed up the overall system without spending money on it. i.e. memory, etc.

I did see a system speed boost... but I have not tried modifying videos, images or burning data... I so all three from time to time... Guess I'll see. Just need to remember that I did that so if I have a problem, I can 'rollback'.

Do you have any ideas/suggestions on getting better performance mcduck?

---

### Post by mcduck on 2010-07-15
like I said, I doubt that you'd actually get any real performance benefits from doing that, since all the data *is already in your RAM* if you have enough RAM to fit it. And if you don't have enough RAM, then you definitely don't want to move your /tmp from hard drive to RAM.

So you only get the performance benefit from getting enough RAM to fit all the programs and data you use, and the benefit is the same regardless of if you just access the temporary data from cache or if you move the /tmp itself to RAM. The only difference would be that keeping the /tmp in disk would cause the system to occasionally write to the disk, which in any normal use case shouldn't cause any noticeable difference in the system's performance (remember, all the /tmp data would already be in cache so the system wouldn't need to read it from hard drive).

I can't really see any use for moving /tmp to RAM apart from live environments and running on some special systems like embedded devices where you simply might not have any hard drive space where you could put the temp files.

---

### Post by efflandt on 2010-07-15
One place tmpfs is used by default is on bootable iso on USB.  That is because flash can wear out after a certain amount of write cycles, and because if data is changed, it is erased in blocks (instead of bits or bytes) and each block is rewritten.  Athough, it does not wear out that quickly, most flash should be good for at least 100,000 write cycles and newer flash used for SSD drives is good for a million write cycles.

---

### Post by cj.surrusco on 2010-07-15
I used the link that bodhi.zazen provided, except did not mount /var/log to the RAM since I like to keep my logs. 

Two things that are odd that I have noticed.

The folders that are mounted on the RAM say that there is 1000MB free, and I have 2GB of RAM.

Also, When I copy a sizable file (about 400mb) to /tmp, there is no change in the System Monitor as far as RAM usage... Seems a bit odd to me... I'm guessing that System monitor doesn't actually measure the amount of RAM free, but actually just the amount that programs are using?

Maybe somebody could explain this to me.

---

### Post by digitalcitizenx on 2010-07-15
This has been discussed here

[http://ubuntuforums.org/showthread.php?t=1054129](http://ubuntuforums.org/showthread.php?t=1054129)

and eluded to here

[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

Interesting concept - I would like a distro like Knoppix that would boot into RAM completely but still write do disc when shutting down.

I wish I had more than 2 Gig of RAM - I may play with this if I do get more RAM.

Imagine your OS running in RAM along with a VM running all in RAM - imagine how fast that would be - right now with 2 Gig of RAM I use 1.4 when a VM is running.

---

### Post by dcstar on 2010-07-16
> **digitalcitizenx said:**
> 
.........
Imagine your OS running in RAM along with a VM running all in RAM - imagine how fast that would be - right now with 2 Gig of RAM I use 1.4 when a VM is running.

I don't have to "imagine" it, my 4GB 64-bit system comfortably runs multiple VMs alone with the 10.04 host without using swap at all, but **all** systems still access the disk because you cannot fit every single OS file into RAM - and you shouldn't because it is a ridiculously inefficient way of using RAM.

---

