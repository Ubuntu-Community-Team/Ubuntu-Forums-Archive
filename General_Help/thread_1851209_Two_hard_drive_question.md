---
title: "Two hard drive question"
date: 2011-09-27
forum: General Help
---

### Post by djen9999 on 2011-09-27
I may be going about this in the wrong way so I'm just going to open this up for comment and ideas.  

I recently was gifted a new hard drive which is larger than my original drive.  I just did a clean install of Natty on the smaller drive after moving my home directory to the newer, larger drive.  I would like to keep the smaller drive as a dedicated boot drive and have all of my apps. and files on the larger drive. How do I go about linking my Applications menu to the second drive and how do I install my apps. to the second drive?  I've had no problem linking my files to the Places menu but applications are a different matter.  I've done some searches into this but the results have been more about partitioning and RAID.

Again, if my thinking is wrong on this, I'm happy to take suggestions.

---

### Post by papibe on 2011-09-27
Having / and /home in different partitions is a pretty common configuration. Boot files, and applications will go on /, and settings and personal files on /home.

Applications depend on both libraries and kernel versions, and are not 'located' in just one directory. The 'executable' usually will be in /usr/bin, documentation on /usr/share and libraries in /usr/lib

You can check all files inside a package with a command similar to this
```
$ dpkg -L vlc
```
This will display all files in the package vlc (the media player).

What would be your concern behind wanting to have your applications on a  partition different than / ?

I think you may use the smaller disk as /boot to keep the start up system and kernels.

What are the HD sizes?

Hope this helps,
Regards.

---

### Post by djen9999 on 2011-09-28
Thanks, that does help somewhat.  The reason I was thinking of moving my applications from / was to avoid having to reinstall everything after doing a clean install of the OS.  It's not a big deal to merge / directories, just time consuming.

Thanks again.

---

