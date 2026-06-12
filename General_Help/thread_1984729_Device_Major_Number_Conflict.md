---
title: "Device Major Number Conflict"
date: 2012-05-22
forum: General Help
---

### Post by venky999 on 2012-05-22
Hi Guys,
This is Ven.

I am trying to install a video frame grabber in my **Ubuntu 10.02 LTS** machine.
The problem I am facing is that the frame grabber's** major number** (which is being allocated dynamically to 251 as a char device) is **conflicting** with the **device mapper** 's **major number** (i.e its major number is also 251 but its under block device category ).
Because of this I am not able to see any video from this card.
But if we change the major number of my frame grabber to 250,its working fine but once if we boot up,we are getting the same issue.

Can you guys help me in fixing this issue.
Is there any way to assign the frame grabber major number to other than 251 while booting up.
Is there any script which is helpful as I am new to Linux.

Thank you.

Kind Regards,
Ven

---

