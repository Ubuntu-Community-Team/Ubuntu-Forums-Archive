---
title: "Boots to frozen Desktop"
date: 2010-01-20
forum: General Help
---

### Post by Starman~ on 2010-01-20
Preface: I'm a relative neophyte when it comes to Linux anything. I was running Hardy in an attempt to learn. I recently decided to upgrade to Karmic. I liked the look of "Mint 8" (AKA Karmic).I've been running Mint nicely for about a week after a fresh install.
Then.... something went spastic...

I went logged in as root and changed file permissions for my "/" folders. The change was simply making group "root" able to read and write files. Than was it. It carried out the change smoothly.

When I hit "Logout" from root, to return to my user account, the screen went white. Stuff flickered when I hit keys. I ended up having to hard boot to get it moving.

Now when I boot, Grub works, it boots to my desktop, graphics display appropriately, but NO mouse and NO keyboard. Dead system. Only thing I can do is hard boot. 

I tried the recovery from Grub, no change. I have no idea where to begin. Any ideas before I go back and reinstall it again (3rd time).
Sure glad I've kept my old W2K, or I'd be screwed.

Thanks in advance

PS - I booted the live Hardy CD to look at files. When partitions are mounted no files in "/" or "/home" can be seen.

---

### Post by myth1914 on 2010-01-20
If there were no files in / it wouldn't boot at all.  You mentioned that the screen flickered when you hit keys.  Are you able to SSH into the box even if the X session is frozen?

I would start with booting the machine and using ctl-alt-bkspc to respawn the X session.

---

### Post by Starman~ on 2010-01-20
Edit: what am i thinking, NO key board

---

### Post by majickmann on 2010-01-20
What command did you use to change the group permissions?

:-)
--majickmann

---

### Post by Starman~ on 2010-01-20
I did it thru the GUI

*Administration-> Users/Groups-> group, root-> permissions-> allow read write of "/"*

---

### Post by Starman~ on 2010-01-21
I should have said I can boot in recovery mode from grub. So I can get a prompt for my user or root. Logging in both ways works.
But... being a linux noob I have no idea what to do with it. Searches aren't coming up that help much.



Edit: I have reinstalled fresh. The problem was too much to fix.

---

