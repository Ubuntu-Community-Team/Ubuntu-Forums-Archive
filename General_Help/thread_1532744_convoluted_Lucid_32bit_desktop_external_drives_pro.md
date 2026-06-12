---
title: "convoluted Lucid 32bit desktop external drives problem(s)"
date: 2010-07-16
forum: General Help
---

### Post by biturica on 2010-07-16
This morning I was attempting to rsync my two external hard drives, which should have only taken a couple of minutes. For many months my two external drives have been given volume names of wd-master and wd-slave. All new files go to wd-master and maybe once a week or so I use rsync to make wd-slave mirror the contents of wd-master. However this morning, I happened to be paying attention to the terminal screen and noticed rsync was deleting files and folders from wd-slave. I killed the process because it looked like it was basically going to completely erase wd-slave. I unplugged the two external hard drives.

Now that I've gotten back home I rebooted my pc after plugging the drives back in. My pc had probably been running without rebooting for a couple of weeks, and perhaps done a couple of updates during that time. After the first reboot I had a white screen, I never even saw the splash screen. So this time I actually turned the pc off, rather than just reboot, and Ubuntu seemed to load normally.

I opened a terminal and cd'd into /media to see if anything looked wierd, and indeed it does.

```
drwx------  2 root    root 4096 2010-07-04 12:05 wd-master
drwxr-xr-x 12 derrick root 4096 2010-07-11 20:57 wd-master_
drwx------  8 derrick root 4096 2010-07-16 08:44 wd-slave

```

I have no idea where wd-master_ came from and why wd-master now belongs to root and only shows 2 files / directories. wd-master and wd-slave formerly looked identical, same perms, same owner, etc.

Moreover, on my Gnome Desktop, the external drives show their original names, there is no underscore appended to wd-master. When I double-click the wd-master icon on the desktop, it opens the volume that has multiple files and directories (the one appended with the underscore and assigned to root from the ls -al command above).

***********

I don't remember all the details but something like this happened to me a couple of months ago too, after the Lucid release was issued and I upgraded from Karmic. After that, I made a fresh install of Karmic and figured maybe there were some bugs that might be ironed out in a couple of months. I only did a dist-upgrade to Lucid again within the last week.

When this happened a couple of months ago, I also got white screens after rebooting, and I had a new folder showing up on one of the external drives that was given the name of the other external drive, and the new folder only contained 2 or 3 files I had just created in my last session. It seemed the other drive was not mounting, and I assumed the couple of files I was seeing had something to do with a permissions error and the remaining directories were merely hidden from me -- I didn't realize Ubuntu was creating a whole new directory on wd-master that gave me the illusion that wd-slave was actually mounted.

I have Lucid 64bit on a laptop (also not a fresh install, but rather a dist-upgrade), and I've never had these kinds of problems with the laptop. I've even used the laptop a couple of times to carry out the rsync of the two external drives. I don't know if that affects them the next time the desktop pc mounts them, after the laptop has mounted them (my user name is not the same on both computers either).

I don't know if this is a difference in the 32 and 64 bit versions, a difference between the components of my laptop (Compaq) and my desktop (Dell), or something different, or a combination of issues. The desktop pc is also dual-booting Lucid and Windows 7; the laptop is not multi-booting; I dunno if this could factor in.

I was not having these problems with Karmic, I'm beginning to think Karmic is the last version I will be able to have on the desktop pc.

Has anyone else experienced anything like this?

---

### Post by dcstar on 2010-07-17
> **biturica said:**
> 
........
Has anyone else experienced anything like this?

Any time you **assume** that devices are mounted always has risks if you do not test to see if the mount is actually there:

[http://ubuntuforums.org/showthread.php?t=820702](http://ubuntuforums.org/showthread.php?t=820702)

---

