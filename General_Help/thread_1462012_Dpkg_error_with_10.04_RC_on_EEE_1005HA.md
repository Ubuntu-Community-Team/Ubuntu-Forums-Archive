---
title: "Dpkg error with 10.04 RC on EEE 1005HA"
date: 2010-04-25
forum: General Help
---

### Post by xanfantasy on 2010-04-25
This has certainly been a new experience. I wanted to try the Ubuntu 10.04 RC on my Asus EEE 1005HA to test it out for my girlfriend for her Dell mini 10. I first tried to use the 10.04 UNR installed by a thumb drive made with UNetBootin. This first failed at about 95-98%. Every time after that, The entire live session froze right as it was starting the partition manager. After this I could not get Windows XP home back on using Novell ghost recovery, it would set up the files system but not transfer files. I finally was able to get 9.10 to install and work with I then followed with updating to 10.04 using alt-f2 + update-manager-d. I went to try to open synaptic and received the error message about needing to use "sudo dpkg --configure -a" I tried running the command and it freaked out with a fast scrolling message and not being able to do anything. Navigating to /var/lib/dpkg/updates/ and deleting everything let me perform a few of the apt-get functions but they all eventually crashed and the computer would have to restart. I performed the 9.10 to 10.04 again with formatting and now no longer have gui login. I have also tried sudo apt-get -f which also crashed. df -h showed I had plenty of space on all partitions. Can anyone assist in fixing this? I can try to provide any data that I can access from a ctrl+alt+f(1-6) terminal I would just need instructions since I still don't know a lot about Linux and Ubuntu.

---

