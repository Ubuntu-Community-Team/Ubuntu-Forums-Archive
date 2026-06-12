---
title: "Emergency - Disk failure an error?"
date: 2010-07-11
forum: General Help
---

### Post by ve2 on 2010-07-11
Ok - so in the even of the system crashing. What can I do to back up my programs installed in Ubuntu. How can I recover from a error? Any suggestions? This has not happened, but in the event, what can one do - other than backing-up your personal items.

---

### Post by efflandt on 2010-07-11
If you are lucky, you may be able to fix things or copy files by booting from CD or connecting the drive to another PC (internally or with USB enclosure).  But that is not something you can count on if the drive self destructs or you dropped it and its heads are flopping around lose.  I have done the latter, but fortunately copied most of what was needed from the failing drive before dropping it at the store while looking for a replacement.

So it is better to be safe than sorry, and back up anything that you definitely do not want to lose, before you try something that does not work or have an unexpected catastrophic failure.

---

### Post by mike555 on 2010-07-11
to avoid downloading all updates after a reinstall:
ubuntu stores downloaded packages in /var/cache/apt/archives

save these files and after a new installation copy them to the same location.
after that do a apt-get update and apt-get upgrade


 You might want to use an online backup also , like Ubuntu-one or Dropbox .

---

### Post by ve2 on 2010-07-11
Example - My biggest effort will be installing several distro's of Linux, Windows and other OS's. In the event the system dies, is there any software I could use? I know Acronis could do the trick, but is there anything that Ubuntu has that will help? I don't really save anything on the root drive. I save everything either to USB or my back-up drive + burn to DVD.

---

