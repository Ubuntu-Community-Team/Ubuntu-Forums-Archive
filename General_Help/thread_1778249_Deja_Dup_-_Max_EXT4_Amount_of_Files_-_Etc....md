---
title: "Deja Dup - Max EXT4 Amount of Files - Etc..."
date: 2011-06-08
forum: General Help
---

### Post by Roasted on 2011-06-08
So I began using Deja Dup, which supposedly is coming to Ubuntu 11.10 and Fedora 15 (I think). It's, to say the least, very sweet. It's easy to use, easy to set up, and truly a "set it and forget it" backup recovery program. I love it because it automatically mounts my samba shares to my Ubuntu file server. Very easy to use.

Here's the catch. What's the limit on how many files can sit in a single EXT4 folder? Reason I ask is I have nearly 6,000 files from Deja Dup. You see, Deja Dup slices my data into 10.0 MB sized tar.gz files. I'm not sure if I can change it to a higher number or not, but having it only at 10.0 MB makes for a lot of files to back up my data. And since it's all going to 1 section it's like, ehh...

Just trying to plan ahead. What's the cap? Is there a way to edit Deja Dup to back up in different increments?

---

### Post by tgalati4 on 2011-06-08
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

Limits
Max file size	16 TiB (for 4k block filesystem)
Max number of files	4 billion (specified at filesystem creation time)
Max filename length	256 bytes
Max volume size	1 EiB (limited to 16TiB because of e2fsprogs limitation)

If want to handle a lot of files, then look at zfs:

[http://en.wikipedia.org/wiki/Zfs](http://en.wikipedia.org/wiki/Zfs)

256 quadrillion zettabytes

The real limit may be the 64,000 ext4 subdirectory limit.  I don't know anything about DejaDup so there may be internal limits set by its programming language.

---

### Post by psusi on 2011-06-08
AFAIK, the 64k per directory limit has been fixed, as has the 16tb total size limit, though the user space tools ( mke2fs ) have not caught up yet.

---

### Post by dFlyer on 2011-06-08
> **Roasted said:**
> So I began using Deja Dup, which supposedly is coming to Ubuntu 11.10 and Fedora 15 (I think). It's, to say the least, very sweet. It's easy to use, easy to set up, and truly a "set it and forget it" backup recovery program. I love it because it automatically mounts my samba shares to my Ubuntu file server. Very easy to use.

Here's the catch. What's the limit on how many files can sit in a single EXT4 folder? Reason I ask is I have nearly 6,000 files from Deja Dup. You see, Deja Dup slices my data into 10.0 MB sized tar.gz files. I'm not sure if I can change it to a higher number or not, but having it only at 10.0 MB makes for a lot of files to back up my data. And since it's all going to 1 section it's like, ehh...

Just trying to plan ahead. What's the cap? Is there a way to edit Deja Dup to back up in different increments?

Can't answer your question, but do like deja dup. I've been using it since 10.10.

---

### Post by Roasted on 2011-06-09
> **dFlyer said:**
> Can't answer your question, but do like deja dup. I've been using it since 10.10.

It's a very solid application, and I really enjoy using it. I do wish it had the option to synchronize data without compressing it, because I would like to have my data in raw format on my file server because I like to connect to my file server from my little 16gb SSD laptop and utilize all of my 500gb+ data from there, but I cannot do so when it is compressed. Since I don't need to use those files constantly, I tend to just fire up my desktop whenever I need access since I have my home directory shared out there and then power it off when I'm done. However, it is by far the best disaster recovery software based on functionality and ease of use for desktop systems. I just haven't used anything else that can beat it in that department. I set up a test desktop with a ton of bogus data on it and tested this functionality, and so far it's backup and recovery has been spot on. I've also noticed a lot of times on my desktop when I go into my home directory I see my samba share mounted to my file server, which I don't have set up to be automatic upon boot. This tells me Deja Dup is running properly.

Likewise, I'm still a little in the gray area on this file system thing. For example, the limitation is listed as 4 billion, but is that for the entire file system or can I literally put 4 billion files into 1 folder and max it out? I remember hearing there was a limitation based on the actual folder itself, with there being a separate restriction on the entire file system. So that's what I was a little "Well geez, I'll just ask and see".

---

