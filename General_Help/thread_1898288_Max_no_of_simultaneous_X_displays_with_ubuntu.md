---
title: "Max no of simultaneous X displays with ubuntu?"
date: 2011-12-21
forum: General Help
---

### Post by frozen.fire on 2011-12-21
I'm not sure if i'm posting in the right forum, I couldn't find a more specific forum for this problem. Please direct me to the correct place if this is not the one.

Ok, I have an ubuntu 10.04 LTS 64-bit istalled on vmware, allocated 4-core processor, 18GB RAM to this virtual machine. I already had some 8 users regularly logging in on the system remotely using remote desktop (i installed xrdp on ubuntu).

Today, i faced a strange problem. I was trying to shift more users on this ubuntu machine, who could successfully connect through remote desktop. however, they could not login with the error "login failed" (there were already **edit:** *10 users including the admin* logged in). So, i was wondering that this has to do with either the max number of simultaneous X displays (is it really 10..??!! :confused:) or the number of processes being handled. I couldn't find any solution so i rebooted the machine and now everything is smooth again, strange, eh..?

I did some research on internet, somewhere someone suggested that it could be a problem with deficiency of video ram or memory and number of slots. My specs on VM are mentioned above, please ask if you need more information.

---

### Post by frozen.fire on 2011-12-22
Ok....

The good news is that i figured out the exact problem and the solution to it.
The problem was not with ubuntu limitations or RAM or video RAM or slots as i asked earlier. The problem was with xrdp which uses sesman to connect to the host.

All i had to do was edit the file sesman.ini in /etc/xrdp and change the value of Maximum Sessions to whatever number i wanted. There were other settings too, i'll play with those settings and a few other stuff on my test server. Finally, i again found something for study..:guitar:

Hope this helps anyone who finds himself in a similar situation.
Cheers...!!
FF

---

