---
title: "need help with boot screen"
date: 2010-09-30
forum: General Help
---

### Post by rwarwarwa on 2010-09-30
Hi there,

The computer I am working with has LucidLynx installed. It had the occassional freeze up happen which would require a hard reboot. I was away for a while. When I got back the others who were using the computer said the problem kept getting worse. Now the computer will only boot up to a screen that I don't understand. It looks to require a better understanding of linux commands than I have. Please help in any way thankyou.

THE PHOTO OF THE BOOT SCREEN IS ATTACHED.

rwa

---

### Post by searchfgold6789 on 2010-09-30
[[SIZE=3]Try this thread.[/SIZE]]("http://ubuntuforums.org/showthread.php?t=295508")

---

### Post by oldfred on 2010-09-30
Journal issues sound like a filecheck may help. Change entries below from sd[COLOR=Red]b1[/COLOR] to each linux partition you have. Use fdisk to see what partitions are linux.

From liveCD so everything is unmounted
sudo fdisk -l
sudo e2fsck -C0 -p -f -v /dev/sd[COLOR=Red]b1[/COLOR]
if errors:
sudo e2fsck -f -y -v /dev/sd[COLOR=Red]b1[/COLOR]

---

