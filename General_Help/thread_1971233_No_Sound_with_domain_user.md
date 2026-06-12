---
title: "No Sound with domain user"
date: 2012-05-02
forum: General Help
---

### Post by ViViCode on 2012-05-02
Hi all!

I have recently installed Ubuntu 11.10 32-bit on my work PC, and joined it perfectly to our windows domain server using likewise-open.
Only problem is that when i login as a domain user, i have no sound, no hardware even shows up. In my local account it works flawlessly.

I have been going mad trying to get it to work, and i have searched all over the Internet.

Any help would be greatly appreciated :):popcorn:

Thank you!

---

### Post by albandy on 2012-05-02
try this:

if you enter your domain name to login try this:
sudo adduser DOMAIN\\username audio
else
sudo adduser username audio

---

### Post by ViViCode on 2012-05-02
Hi albandy,

Thank you for your quick reply.

I have already added my user with the domain\\ and by its self in my groups file, but i followed your steps and it tells me that they are already added to the group. I have also added it to the admin group but with no luck.

Thank you :)

---

### Post by albandy on 2012-05-02
With your domain user logged, type id in the console and post the result.

---

### Post by ViViCode on 2012-05-09
Thanks for the help! I managed to get it working by upgrading to ubuntu 12.04. Now it's working without a problem.

Thanks again!

---

