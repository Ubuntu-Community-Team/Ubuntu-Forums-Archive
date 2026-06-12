---
title: "New user and forum member"
date: 2010-01-14
forum: General Help
---

### Post by photofinishron on 2010-01-14
Greetings.  I'm new to the linux community and excited to get my system up and running and breaking free of the windows gridlock.  SO far I've tried several different linux platforms and seem to be gravitating to the ubuntu version.

I have a 6 computer system with W2K as the primary OS.  (One laptop has W-Vista but it's my wife's and I've been told it's a hands off situation there :) - go figure))

I would like to keep one computer running W2k and migrate the rest to linux.  Problem I'm haveing is My system is not set up with the domains Linux seems to want to see to use the windows share function.  What I want to be able to do is to see the W2k computer from the Linux computers.  It would be nice if I could see the Linux computers from the W2k computer but that's not too critical as once all my important archives have been migrated to the linux system it will get a linux OS too.  But for now keeping it W2k is a necessary evil.

If someone would be kind enough to direct me in the proper direction to solve this problem I would appreciate it muchly.

Thanks

Ron

---

### Post by oldfred on 2010-01-14
For me every upgrade for the last three years changed my connections to my windows XP laptop. Most of the time it was the settings in windows, firewall, sharing configuration etc. 

You will need samba and probably would do better with a thread with Samba network in the title and specific issues. There are several users regularly commenting on those type of issue but with your title they may not see this thread.

Howto: Fix Windows share browsing issues 
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
Sharing issues
[http://ubuntuforums.org/showthread.php?t=1374369](http://ubuntuforums.org/showthread.php?t=1374369)

 HOWTO: Setup Samba peer-to-peer with Windows 
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting)

And Welcome to Ubuntu Forums, we hope you enjoy ubuntu as much as we do.

---

### Post by bodhi.zazen on 2010-01-14
This question goest through using Samba, I believe you are wanting to add your Linux box to the same workgroup as Windows. You can do this in the samba config file.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

