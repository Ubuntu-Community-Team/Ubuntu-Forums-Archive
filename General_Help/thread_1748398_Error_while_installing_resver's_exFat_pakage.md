---
title: "Error while installing resver's exFat pakage"
date: 2011-05-03
forum: General Help
---

### Post by Gowie47 on 2011-05-03
[SIZE=2]Hey guys,

So I've been trying to get at least read access for my exFat external drive. I've done a lot of looking around and found a couple work arounds. 
Mainly these two:
1. [http://winipulator.blogspot.com/2010/10/how-to-read-and-write-exfat-flash.html](http://winipulator.blogspot.com/2010/10/how-to-read-and-write-exfat-flash.html)
2. [http://code.google.com/p/exfat/](http://code.google.com/p/exfat/)

I have tried doing both of these, both with errors. I think it has something to do with FUSE, and to be honest I don't really know what that is even though I was reading about it last night. Then again that was at 3:00 in the morning so maybe I should give that another try, but if anybody could also give that a plain explanation I would appreciate that as well. 

So back to my error. I am just going to include the error I got when dealing with the winipulator tut since I just dealth with it. So in the winipulator tut, I get up to the point where you are supposed to update the packages with
# sudo apt-get update

it runs update and comes back with this
[/SIZE]```
W: Failed to fetch http://ppa.launchpad.net/gowie/exfat/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gowie/exfat/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```[SIZE=2]

So basically does anybody know whats going on here? Can anybody point me in the right direction? Thanks in advance, I appreciate any help!



[/SIZE]

---

### Post by Gowie47 on 2011-05-08
Hey just bumping this and crossing my fingers for some help. If you have ANY idea on whats going on please let me know. Thanks!

---

