---
title: "Rhythmbox Problems"
date: 2011-03-25
forum: General Help
---

### Post by iFuzo on 2011-03-25
Well I recently tried syncing music to my iPod touch with rhythmbox and it keeps telling me the following:

> There is not enough space on the device to transfer the selected music, playlists and podcasts

This is not true as I only have 3.2GB of music and 5.7GB space remaining on the ipod as shown below:

[IMG]http://s2.postimage.org/sx5483htq/Screenshot.png[/IMG]
[IMG]http://s4.postimage.org/tz9r1m5by/IMG_0021.png[/IMG]

Can anybody explain what is going on and why it wont let me sync ipod?

---

### Post by jblake20 on 2011-04-10
Hi

I am having the same problem, does anyone have any suggestions.

I have a 64 gb ipod touch and have been syncing fine with library.  now it says it is full.  I can access the 6100 songs on there but when I try to sync or add new files I get the out of space error or the following:

Error transferring track

Error while getting peer-to-peer dbus connection:  The name: 1.98 was not provided by any .service files

Thanks

Jamie

---

### Post by paque on 2011-04-26
I am having the same with my 16GB iPhone. I think I know what's happening. I have been synchronizing a few albums at a time, slowly filling the iPhone. At some stage, the total amount of music becomes larger than the total amount of free space. When the synchronizing failed in my case, I had something like 7.2GB of music with 7.0GB free space. It is as if Rhythmbox wants to be sure it can copy all music, rather than figuring out what's new and ensuring there is enough space on the device for the new music.

I.e. everything was fine when I had 7.0GB of music and 7.2GB of free space. I bet that if I delete all music from my iPhone and then synchronize my entire music collection it will work without any problem.

I hope this description will help the developers in locating and resolving the bug in the software.

Marc.

---

### Post by paque on 2011-07-04
As requested, here is the output of df -hT, while my iPhone is attached to my notebook:
```

root@Ubuntu-8440p:~# df -hT
Filesystem Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    283G  180G   90G  67% /
none      devtmpfs    1.9G  300K  1.9G   1% /dev
none         tmpfs    1.9G  200K  1.9G   1% /dev/shm
none         tmpfs    1.9G  372K  1.9G   1% /var/run
none         tmpfs    1.9G     0  1.9G   0% /var/lock

```

For the record, the iPhone has 5.6GB free space and my music collection is 7.1GB. The iPhone has 16GB of total space.

---

