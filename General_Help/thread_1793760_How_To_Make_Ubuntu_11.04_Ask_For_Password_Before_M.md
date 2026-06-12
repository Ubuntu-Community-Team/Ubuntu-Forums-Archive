---
title: "How To Make Ubuntu 11.04 Ask For Password Before Mounting Partitions"
date: 2011-06-30
forum: General Help
---

### Post by Lancelot59 on 2011-06-30
I'm currently using an older version of ubuntu (Karmic) and want to finally update. Is there a way for me to get ubuntu to ask for a password before mounting a partition like Karmic did? I've been looking for a way to solve this problem, but I haven't been able to find any solutions. I know a lot of people found it annoying but I rather liked it.

---

### Post by DawieS on 2011-06-30
I don't know about** 11.04**, but the method I suggested in this thread works for **10.04** and **10.10**:
[http://ubuntuforums.org/showthread.php?t=1490436](http://ubuntuforums.org/showthread.php?t=1490436)

---

### Post by Lancelot59 on 2011-06-30
> **DawieS said:**
> I don't know about** 11.04**, but the method I suggested in this thread works for **10.04** and **10.10**:
[http://ubuntuforums.org/showthread.php?t=1490436](http://ubuntuforums.org/showthread.php?t=1490436)

Excellent! I'll test this out in a VM later and see if it works.

---

### Post by Lancelot59 on 2011-07-01
I tested the first option and it's asking for a password before mounting anything. I think I might leave it like that. I'll try out the other option you have in that post tomorrow, however I expect they'll work fine too. 

Do you know where I could find some documentation on the file I'm editing? I'd like to know more about what exactly I'm doing.

---

### Post by DawieS on 2011-07-01
I don't know if anything formal in this regard was documented. I picked up some leads while browsing the Development Forum during the alpha and beta stages of **10.04**.

At the time the majority of users were complaining about the default behavior having to authenticate all mounts in **9.10**, while they were the only ones with physical access to their computers.

---

### Post by Lancelot59 on 2011-07-01
The only behaviour I seem to be able to get out of it is to ask to mount everything, or not ask. I'm still cankering with it.

EDIT: Forgot to comment out the lines in the first file. Everything works as expected now. Thanks!

---

