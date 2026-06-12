---
title: "(initramfs) prompt"
date: 2011-09-17
forum: General Help
---

### Post by l07 on 2011-09-17
I get a kernel menu (only the latest and recovery), and upon choosing either, it ends up not being able to mount several things, and says /sbin/init not found, try with init= bootarg. It ends up at the ash prompt saying (initramfs).

I was lying down after I ran the update, and several hours later (approximately) heard the fan stop spinning, and the beep that's produced when pc starts up. So I figured for some reason the pc restarted. Maybe because of power spike/loss, or some hardware fault.

Some time later, I got up and looked at the screen. It said "disk boot failure", which by now, I've gotten used to. The pc used to work very well, before I opened it and started plugging in a different drive with ubuntu installed. Since then, it occasionally displayed this error (disk boot failure), which I could only resolve by retesting connections, and making sure the contacts between hard drive cables were tight. Although I could get it working (and did so this time) the cause of the problem is still unknown and makes this pc seem unreliable.

I think maybe something on the disk became corrupted when it restarted, so I should run fsck. Do you have other advice?

---

### Post by ajgreeny on 2011-09-17
Open up **System ->Administration ->Disk Utility** program, and run the SMART diagnostic test in that to see if it finds any faults.  Maybe your hard disk is at the end of its life, and forewarned is forearmed.

---

### Post by l07 on 2011-09-17
That hard drive is rather new, it was bought about a year ago. It says it found one bad sector. Self-test failed (read).

---

### Post by ajgreeny on 2011-09-17
> **l07 said:**
> That hard drive is rather new, it was bought about a year ago. It says it found one bad sector. Self-test failed (read).
That's not good in such a new drive. I suggest you do run fsck on it from a live CD with the command ```
sudo e2fsck /dev/sdx#
``` where sdx# is each linux partition in turn, one by one.

If it's possible, see if you can get hold of the disk manufacturer's own diagnostic utility to run on it as well, and whether or not that also finds faults.  If it does, and the drive is really only that age, you may have some call upon the maker to put it right, depending on where in the world you are, and your own laws.

---

### Post by l07 on 2011-09-17
I ran fsck, it fixed errors and now everything works fine. Thanks for your help.

Here are the messages fsck printed:
```
Error reading block 2394344 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Clearing orphaned inode 1026311 (uid=120, gid=130, mode=0100600, size=0)
Clearing orphaned inode 1026229 (uid=120, gid=130, mode=0100600, size=0)
Clearing orphaned inode 1026180 (uid=120, gid=130, mode=0100600, size=0)
Clearing orphaned inode 1026168 (uid=120, gid=130, mode=0100600, size=0)
Clearing orphaned inode 1026161 (uid=120, gid=130, mode=0100600, size=0)
```Could I convert that block number into a file name in order to see if I should reinstall something?

I'm inclined to think that the hard drive is not at fault, but rather  the pc is, because of the "disk boot failure" message that appears  sometimes (and did so upon restart), independently of any specific hard  drive. I think that because it appeared upon restart, even though I  didn't move the pc (hence didn't disturb the cables) since it was  working, that indicates that a separate power loss problem is less  likely. On the other hand, it is possible that the power loss problem  somehow triggered the "disk boot failure" message. Do you have any  suggestions about that?
 This message appears often when I exchange hard drives - plug one in  and another one out, because they don't both fit into the case. Thus I  thought contacts between cables could've been at fault. But now I'm not  sure.

---

### Post by ajgreeny on 2011-09-18
Having run fsck and "solved" the problem for now at least, I suggest you leave things as they are for the present and see how things go.  I suspect that the power-loss caused the problem and is now all put right again.

---

### Post by vra5107 on 2011-09-24
Awesome @ajgreeny. 6 hours and finally one post does it. 

 My system shutdown because of over hearing. Based on what you said this might have cause d the problem. 

    When can I use the e2fsck command. what problems does this solve?

Thanks
Venkat

---

