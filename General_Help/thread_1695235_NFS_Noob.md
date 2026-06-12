---
title: "NFS Noob"
date: 2011-02-25
forum: General Help
---

### Post by bodam on 2011-02-25
I'm new to NFS mounting.  I just bought a NAS (QNAP TS-419) and have successfully mounted shares on the NAS from my Ubuntu 10.04 laptop.

I have a share on the NAS called Multimedia where pictures, videos and music are stored.  In my home directory I created a folder called NASMedia and can use the command

mount NASNAME1:/multimedia /home/userid/NASMedia

and it works fine.  Now I want to have it do this automatically.  I know that I need to edit fstab but I really don't get the verbiage I see examples that include things like "rsize=8192,wsize=8192,timeo=14,intr,bg,retry=1,nob ootwait".  Can someone explain to me what I should use in fstab?

I also want to make sure that putting this in FSTAB won't cause boot problems if the NAS is not available.  This is my laptop and if I'm not at home, I don't have NAS access.  I don't want to have issues in this situation.

Thanks for whatever help you can give.

---

### Post by fragos on 2011-02-25
I also found using fstab to mount an NFS share a bit daunting so I created a shell script with my mount command and put it in /usr/local/bin. When I need to mount I open a terminal window and enter the the more user friendly script name and respond to the request for your password. Your script would look like the following two lines:


#!/bin/bash
sudo mount NASNAME1:/multimedia /home/userid/NASMedia

---

### Post by rubylaser on 2011-02-25
Here's a quick example of an /etc/fstab file with your settings...
```
NASNAME1:/multimedia /home/userid/NASMedia nfs intr,rsize=8192,wsize=8192,async, 0 0
```

This is what I use at home, and I'm able to max out my gigabit connection from my fileserver to my other boxes.  I've used these options for years.  Good luck.

---

### Post by bodam on 2011-03-01
Thanks both of you.

---

