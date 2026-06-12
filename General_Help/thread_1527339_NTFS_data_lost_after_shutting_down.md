---
title: "NTFS data lost after shutting down"
date: 2010-07-09
forum: General Help
---

### Post by agsel on 2010-07-09
I have recently installed ubuntu 10.04 aside to my windows 7. One thing I tried out was to share firefox and thunderbird profiles. I have a separate NTFS partition for sharing stuff. Everything seemed to work fine. I had all my browsing history and bookmarks and emails shared nicely between windows and ubuntu. But now I have managed to lost data twice already (in one week time). The data itself is not so important (no need to recover it). But I'm just curious, why is this failing?

I use firefox ProfileManager (firefox -ProfileManager) to create a new profile. I did it in Ubuntu. I created a new folder on my Share partition and pointed profile there. Everything works fine. Profile is saved there and I can use it in Ubuntu. Now, after I shut down Ubuntu and go into Windows 7 (which was hibernated the whole time), the given folder is gone. And in Ubuntu, the folder is also gone.

There are some other folders, which I created during my Ubuntu session, which are not visible in Windows, but are visible in Ubuntu.

Does any one have any suggestions, how to make sharing data possible? Or why is my data getting lost. May-be the problem is hibernated Windows? But why then?
Or should I manually unmount my NTFS partition?

---

### Post by Vincentlaborant on 2010-07-09
Why would you keep Windows in hibernation mode? Shut it down when you are not using it. Then create the shared folders in Ubuntu on the shared partition you have created. Shut down Ubuntu, and load Windows. It should work that way out of the box, at least it does at my computers.:D

---

### Post by agsel on 2010-07-09
Thanks for the reply! At least I know, there are people who have managed to get this working.

I'm keeping windows in hibernation because it starts faster that way. I'd say about 4-5 times faster than from full boot.

I will try that. But I don't get, why the hibernation causes the problem. I still think there is something more..

---

### Post by QLee on 2010-07-09
[QUOTE=agsel]...
I will try that. But I don't get, why the hibernation causes the problem. I still think there is something more..[/QUOTE]

Another name for hibernation is suspend to disk. The contents of RAM are written to disk so that the system comes out of hibernation in the same state as when it when in. Thus it makes sense that it couldn't know about what was done while it was hibernated.

---

### Post by Vincentlaborant on 2010-07-09
> **QLee said:**
> Another name for hibernation is suspend to disk. The contents of RAM are written to disk so that the system comes out of hibernation in the same state as when it when in. Thus it makes sense that it couldn't know about what was done while it was hibernated.

Yes. That is the major disadvantage of hibernation mode. Even if it gives you a faster boot (since it only has to load a bunch of files), I would recommend only to shut down the pc if you have a multiboot system, especially when you have shares between the different operating systems.

Hibernation writes a large cache file to disk, and reads it when you load the OS again. Therefor, it is not able to work with the changes in the shares you create. At least that is what i found out after some experimenting on several computers.

---

### Post by agsel on 2010-07-09
I will try sharing with shut down windows. Seems to be working for now. Thanks

---

### Post by Vincentlaborant on 2010-07-09
> **agsel said:**
> I will try sharing with shut down windows. Seems to be working for now. Thanks

No problem:popcorn:

---

