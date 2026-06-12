---
title: "dd funtion please help"
date: 2011-05-29
forum: General Help
---

### Post by scar1 on 2011-05-29
Hi,

Can anyone please help me with what I thought was quite a simple task and function.

I just would like to create am iso image of some dvds I have. I thought it would be best to use dd command, see sample below;

admin@unixbox:$ ls -l /dev/dvd
lrwxrwxrwx 1 root root 3 2011-05-29 21:53 /dev/dvd -> sr0

dd if=/dev/sr0 of=/home/videos/dvd.iso bs=2048 conv=sync,notrunc

however i get an error message "No such file or directory" and I am not sure of the reason why.... Can anyone assist me to understand why?

I was not sure where to post this question, so posted here under general. 

Thanks
Scar1

---

### Post by scar1 on 2011-05-29
Spotted the error, please ignore my stupidity.....

---

