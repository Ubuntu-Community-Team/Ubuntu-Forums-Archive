---
title: "I broke it! CD-ROM USB automount mount blank media"
date: 2009-12-23
forum: General Help
---

### Post by musashi39 on 2009-12-23
It all started on a dark and stormy night. The DM was getting bored and decided to resurrect old pc parts..... 

I attempted to share my cdrom drive via Samba. Some error msg poped up telling me exactly what to add to smb.conf so I could do what I wanted. Yay! It worked, or so I thought. Couldn't access the share from the network and I had apparently lost permission to unmount/eject the share. So I changed smb.conf back. No dice... I deleted the cdrom0 directory and restarted hoping all would be well. No dice... I then manually recreated the cdrom0 directory owned by root:root. Finally I figured out that it needed to be root:cdrom. So now I can read cdroms. Yay! Our hero saves the day! But wait a sequel:

Now, for whatever reason, I can't read or write to blank media, and usb won't automount.

Thanks in advance oh glorious gods of Ubuntu![-o<

---

### Post by musashi39 on 2009-12-23
I'm using Ubuntu 9.10 not Ubuntu Mobile. Can't figure out how to change it.

---

