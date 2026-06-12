---
title: "Long mount points on external drives"
date: 2009-12-21
forum: General Help
---

### Post by Silvernail on 2009-12-21
Recently I upgraded to KK from JJ. Under both my external USB drives would  mount as below:

dave@dave:~$ ls /media 
disk disk-1  cdrom  cdrom0
dave@dave:~$ 

Then, I did a reinstall on KK. I forgot and left the external drives plugged in to the USB slot. Now the external drive mount as below:

dave@dave:~$ ls /media
44fb04a3-444f-411c-8b07-98c4fd58686f  6cdedbb0-a45c-46e0-a472-78b0cfe562e7  cdrom  cdrom0
dave@dave:~$ 

This is not a problem if I use the GUI's but I do a lot of things from the command line. With  mount points like this, it gets somewhat cumbersome to type this mount point or go to another terminal to copy/paste it into my command line.

Is there as way I can rename these?

Thanks for  your response.
Dave

---

### Post by Dennis N on 2009-12-21
Give the mounted partition on the external drive a label. The drive will then mount at /media/label consistently.

See:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

and look at: Contents > Changing the Label

Note: 'Changing' also covers creating one.

---

### Post by Silvernail on 2009-12-21
Worked like a charm. Thanks.

---

