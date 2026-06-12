---
title: "can two users from two distros share a home?"
date: 2011-09-29
forum: General Help
---

### Post by F.G. on 2011-09-29
hi,
I'm basically trying to set up a system whereby my laptop dual boots with a user in each distro sharing the same home folder.

the two distros are Archbang and Ubuntu:  
my user in Ubuntu has it's '/home' on a separate logical partition, in the same physical partition as the ubuntu '/'.

Archbang is on a separate physical partition, if i try to make a user with the same /home as the ubuntu user it wont let me.

so, i was wondering if anyone knows if this is doable? and what the issues are? 

thanks.

---

### Post by aeiah on 2011-09-29
do you mean the same username, or just the same partition? the same username probably wouldn't be all that wise, as sharing config files could get messy if you use different versions of the same software. i cant see why you can't specify the same home partition for both distros though.

---

### Post by zhogan85 on 2011-09-29
I've been looking into this myself lately (I plan on dual booting Arch and Ubuntu). I've not tried it yet, I think I will this weekend, but from what I've read sharing a /home partition is doable, though there seems to be mixed opinions about whether its advisable. The issue with sharing a /home partition is that the different config files from different versions of the same applications in each system can cause bugs. To get around this, you must use a different username in each system. The problem with Archbang could be it uses a different UID than Ubuntu? For instance, in Ubuntu I think its 1000, but I know in other OS's it is sometimes 500? I'm not familiar with Archbang.

An alternative to sharing a /home partition I've found (and what I plan to do) is having /home and / on the same partition for each OS, and then have a separate /data partition and mount it in each OS.

Sorry I don't have any links handy, but there are several threads both in this forum and in Arch's forum detailing this discussion. Hope this helps. Let me know what you choose and how it goes.

---

### Post by F.G. on 2011-09-29
so, my main idea was to have a user in one distro and a user in another, who both share their /home folders.  the main purpose would be to be able to use both, and easily access the same data.

whether the usernames are the same or not i hadn't though about, i guess i thought it probably wouldn't matter.  I am increasingly thinking that it is probably wisest, just to manually set-up some shared folders and use those, as zhogan85 suggests, (as it's only really shared access to data that concerns me).

otherwise, here's a link to a thread about setting up archbang and ubuntu to dual boot, in which i've detailed how i did it. also oldfred lists a wealth of information about the shared home question: 

[http://ubuntuforums.org/showthread.php?t=1850131](http://ubuntuforums.org/showthread.php?t=1850131)

ps. i'm new to archbang, but so far i really like, and would recommend it.

---

### Post by WorMzy on 2011-09-29
What you want is a shared data partition. You can easily mount a separate storage partition to /media/store, or wherever, and then mount --bind (or even symlink) specific folders to each user's /home folder.

For instance, here's what I have set up in all my Linux OSes fstabs:

```
# 
# /etc/fstab: static file system information
#
# <file system>                           <dir>                   <type>  <options>                  <dump> <pass>
[COLOR="Gray"]*...snip...*[/COLOR]
UUID=7A5C94995C94522D                     /media/Terastore        ntfs-3g auto,uid=1000,gid=100,umask=002 0 0
/media/Terastore/Collection/              /home/wormzy/Collection none    bind                            0 0
/media/Terastore/Users/WorMzy/Pictures/   /home/wormzy/Pictures   none    bind                            0 0
/media/Terastore/Users/WorMzy/Documents/  /home/wormzy/Documents  none    bind                            0 0
/media/Terastore/Downloads/               /home/wormzy/Downloads  none    bind                            0 0

```

That mounts my storage partition, then binds the music, pictures, documents and downloads folders over my user's home folder equivalents.

So then, I can access all my documents by simply going to /home/wormzy/Documents, but all my config files remain separate to every other Linux installation on my PC (I currently have 7 - three Ubuntu, four Arch, varying desktop environments and architectures). I do the same with my Videos, but they have their own partition which I just mount directly onto /home/wormzy/Videos

Works great.

---

### Post by zhogan85 on 2011-09-29
F.G., thanks for the link to the other thread, there are some good links in there. Glad to hear you like Archbang, I'm excited to try Arch, and maybe will dabble with Archbang too.

---

### Post by F.G. on 2011-09-29
thanks WorMzy, this looks like it may be exactly the kind of thing i'm looking for.  Although I think i may wait to try and implement it until i can do it with a whole home network (i'm about to move, and also put together a new computer).

regarding archbang, stylistically its a lot like crunchbang (minimalist and dark), its really easy to install, so it seems like quite a simple easy way to get into Arch and using pacman. 

also it has a number of desktop environments which you can choose from when you log in like: 
blackbox, xfce4, icewm, wmaker

---

### Post by indstr on 2011-09-29
Statement retracted, sorry

---

### Post by Lars Noodén on 2011-09-29
> **F.G. said:**
> I'm basically trying to set up a system whereby my laptop dual boots with a user in each distro sharing the same home folder.


Yes, it's doable.  Just make sure that the /home directory is a separate partition and in a format that both distros handle.  e.g. EXT3 or EXT4.  When you install the second distro just point to the existing /home partition and be sure *not* to erase it.

Edit: The one crucial part is that the UID for that account must be the same on both systems.  It's easy enough to change if necessary.

---

