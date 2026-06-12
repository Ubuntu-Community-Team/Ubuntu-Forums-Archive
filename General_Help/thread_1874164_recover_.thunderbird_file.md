---
title: "recover .thunderbird file"
date: 2011-11-02
forum: General Help
---

### Post by bluexrider on 2011-11-02
I was copying files from files from one profile on sda1 to another on sda2 and accidentally moved the file instead. I have since reinstalled another OS to the sda2 partition that I was copying to.

Result:
sda1  file was moved
sda2 reformatted

How can I recover .thunderbird folder that was originally on sda1?

---

### Post by oldfred on 2011-11-02
Welcome to the forums.

Do not write anything into the sda1 partition as that may overwrite the deleted data.

You may be able to use photorec, but the thunderbird profile is a lot of files. And you do not get file names, just extensions. You will have to inspect each file and see what name to give to it. And it may not recover all and make a workable system. I have used photorec. It takes a long time to run and you  need space on another device to copy files to.

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

Use scripts to help sort files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)

I have always kept my Firefox & Thunderbird profiles on a shared NTFS partition. Then XP and all my Ubuntu's easily use it with a minor edit to profile.ini. I also copy the profiles to my portable for travel & back.

---

### Post by bluexrider on 2011-11-03
I should have known better than do what I did. Lesson learned (again). 

Tried testdisk-photorec. It doesn't want to recover .hidden files.

[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588) dead link


Will try something else.

---

### Post by bluexrider on 2011-11-14
Could use some help here. Any more suggestions?

R-Studio?

---

### Post by bluexrider on 2011-12-05
bump

---

### Post by sindhughanti on 2011-12-05
Please help here as well!
[http://ubuntuforums.org/showthread.php?p=11516517#post11516517](http://ubuntuforums.org/showthread.php?p=11516517#post11516517)

Thanks!

---

### Post by bluexrider on 2011-12-06
> **sindhughanti said:**
> Please help here as well!
[http://ubuntuforums.org/showthread.php?p=11516517#post11516517](http://ubuntuforums.org/showthread.php?p=11516517#post11516517)

Thanks!
post in your own thread

---

