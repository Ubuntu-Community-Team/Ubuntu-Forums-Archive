---
title: "sharing folder from 2nd drive"
date: 2009-07-18
forum: General Help
---

### Post by singhrh on 2009-07-18
Help needed. I am a relative noob to ubuntu (jaunty) so please be kind. Thanks

I have my home folder in the first drive of my Ubuntu machine and able to share folder with windows vista PC with no problems. I can shut down each computer and restart and everybody is happy. I can read/write as i wish. 

Now I installed a new 2nd drive created a folder on that drive ( I am the owner of that folder) and set it for sharing (same as the home folder). When i set the sharing options  i check off "Allow other people to write to this folder". Then I can then acces this folder from windows, no problem. But if i restart my Ubunut machine this option becomes unchecked and i cannot acces from windows until i recheck this option again. Any way of keeping this option checked through a restart?

Part of my SMB.conf file is below (if necessary). 


Any and all help is greatly appreciated. Thanks in advance. 


[Music]
path = /home/rsh/Music
available = yes
browsable = yes
public = yes
writable = yes
create mask = 0775
directory mask = 0775


[disk]
path = /media/disk
available = yes
browsable = yes
public = yes
writable = yes
create mask = 0775
directory mask = 0775

---

