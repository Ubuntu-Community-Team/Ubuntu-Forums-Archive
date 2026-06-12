---
title: "32 bit or 64 bit?"
date: 2009-10-25
forum: General Help
---

### Post by viking_maniac on 2009-10-25
Well, that's the question I have for you today! :P
 
 
I have an Intel C2D CPU that supports 64 bit operating systems. Should I therefore use 64 bit Linux as a rule, or are there other factors to consider in advance?
 
I've heard that 64 bit operating systems drain a lot more memory than 32 bit, and that the difference in speed doesn't justify the loss of memory. When I use Ubuntu 9.04 32 bit with 2GB of physical memory, it only uses a fraction of it and I don't even need a swap space.
 
What are the pros and cons? What's your personal opinion or experience?
 
Thanks!

---

### Post by DeMus on 2009-10-25
> **viking_maniac said:**
> Well, that's the question I have for you today! :P
 
 
I have an Intel C2D CPU that supports 64 bit operating systems. Should I therefore use 64 bit Linux as a rule, or are there other factors to consider in advance?
 
I've heard that 64 bit operating systems drain a lot more memory than 32 bit, and that the difference in speed doesn't justify the loss of memory. When I use Ubuntu 9.04 32 bit with 2GB of physical memory, it only uses a fraction of it and I don't even need a swap space.
 
What are the pros and cons? What's your personal opinion or experience?
 
Thanks!

If you run programs full of large calculations and so so all the tiem you should get the 64-bits version. If not, stick to the 32 bits version. It's easier to maintain, specially drivers, codecs and flash.

---

### Post by 3rdalbum on 2009-10-25
If you want to be able to use PowerDVD Linux from the Canonical store, use 32-bit. Otherwise, use 64-bit.

---

### Post by XCan on 2009-10-25
64 bit do drain a bit more memory, but I wouldn't call it "a lot more". However, seeing as you're only having 2 GB RAM, perhaps you can stick with 32 bit if it's alreayd working for you. If you, on the other hand, use stuff like LAPACK, or some encoding apps, then I believe you would gain some speed by going 64 bit.

---

### Post by scorp123 on 2009-10-25
I find 64-bit Ubuntu is still a bit lacking ...

For example: I get "stuttering" when I play some videos on 64-bit. The reason behind this is that for some formats the decoding has to pass through a 32-bit wrapper. Flash is such an example. Or sometimes I run into sync issues: the pictures in the movie will slow down to a crawl while the sound continues in normal speed ... and all of a sudden the movie tries to re-sync and the scenes fly over the screen as if someone had pushed the "Fast Forward" button ... And it doesn't really matter what player I use. I get the same behaviour from VLC, MPlayer and Totem.

Yes, I know .... there are various workarounds. Like installing native 64-bit Adobe Flash manually instead of going with the 32-bit wrapper you get from the repos. Or manipulating /proc/mtrr ...

But seriously: Who wants to bother with that?

On 32-bit Ubuntu I simply install the "ubuntu-restricted-extras" package and a few things from the "medibuntu" repo and I'm done.

64-bit is still too hasslesome, IMHO.

So if you only have 2 GB of RAM ... don't bother with 64-bit. Just use 32-bit and be happy to know that all your multimedia stuff will simply work.

Even if you have more than 4 GB of RAM: Oh well. You can install the Ubuntu Server kernel ("linux-server-*" packages). That one makes use of the "Physical Address Extension" (PAE) and thus increases the addressable amount of RAM for a 32-bit kernel from 4 GB to 64 GB max.

I used to have this setup before switching to 64-bit (I have 8 GB RAM). And I am seriously considering of going back to it. This stuttering I get from various multimedia formats seriously is getting on my nerves.

Related threads:

"Full amount of RAM not being displayed"
[http://ubuntuforums.org/showpost.php?p=8092098&postcount=4](http://ubuntuforums.org/showpost.php?p=8092098&postcount=4)

Installing the "linux-server" package on 32-bit Ubuntu:
[http://ubuntuforums.org/showpost.php?p=7985098&postcount=20](http://ubuntuforums.org/showpost.php?p=7985098&postcount=20)

---

### Post by gnuisancev3 on 2009-10-25
> **viking_maniac said:**
> Well, that's the question I have for you today! :P
 
 
I have an Intel C2D CPU that supports 64 bit operating systems. Should I therefore use 64 bit Linux as a rule, or are there other factors to consider in advance?
 
I've heard that 64 bit operating systems drain a lot more memory than 32 bit, and that the difference in speed doesn't justify the loss of memory. When I use Ubuntu 9.04 32 bit with 2GB of physical memory, it only uses a fraction of it and I don't even need a swap space.
 
What are the pros and cons? What's your personal opinion or experience?
 
Thanks!
I've been using 64 bit since there was 64 bit flash, and i've liked it quite a bit.  I've honestly not noticed much of a performance loss or gain. 

I notice the gain when i use processor intensive apps like DeVeDe as it encodes movies to go onto a DVD.

---

### Post by oldos2er on 2009-10-25
I ran 64-bit Ubuntu on my Core 2 Duo with 2GB RAM, no problem. For day-to-day activities like web browsing, emailing, etc, you won't notice much difference from 32-bit. But video encoding is noticeable faster.

 It's just as easy to install 64-bit Flash as it is 32-bit; there's a script at the top of the 64-bit users forum you can use. Can't say I've noticed any video or audio stuttering.

---

