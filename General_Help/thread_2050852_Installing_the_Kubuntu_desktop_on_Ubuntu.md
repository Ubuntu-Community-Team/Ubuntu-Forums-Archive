---
title: "Installing the Kubuntu desktop on Ubuntu"
date: 2012-08-31
forum: General Help
---

### Post by Karandras on 2012-08-31
im still getting use to linux so please bare with me. 

i was thinking of doing a fresh install of ubuntu and dual booting it with kubuntu (both 12.04 64bit), then i saw a forum post that you can install the kubuntu desktop along side of ubuntu. now my real question is: i understand that id have to do "sudo []("http://www.linuxquestions.org/questions/#")aptitude kubuntu-desktop" but would that change if im running the 64 bit version or will it automatically download the 64 bit version? like would it be something like "sudo aptitude kubuntu 64bit-desktop"?

thanks in advance.

---

### Post by drmrgd on 2012-08-31
No, the package manager should realize your architecture and install the appropriate one for you.  

Also, as it goes, you'll be basically installing a new desktop environment that can be alternatively started when you're at the login screen.  So, your base system will remain the same, and if you decide you want to stick with Unity, you can easily log out and log back in to that session instead.

---

### Post by Karandras on 2012-09-01
ok thanks drmrgd. being able to switch the desktop environment at the login screen is the driving factor instead of doing a dual boot where id have to do a complete restart to switch between the 2.

---

### Post by lisati on 2012-09-02
Have you tried the suggestion [here]("http://ubuntuforums.org/showpost.php?p=12213942&postcount=2408")?

As an aside, be careful about having your support requests in multiple places in this forum, as it dilutes the community's ability to help in a coherent fashion.

---

