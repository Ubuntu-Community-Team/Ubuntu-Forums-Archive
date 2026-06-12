---
title: "Executing custom startup script?"
date: 2010-04-17
forum: General Help
---

### Post by RFrenette on 2010-04-17
I created a script, named mount_share.sh (in /etc/init.d), to mount the shared VirtBox  dir at boot so I don't have to do it manually every time I load the VM.  The script contains the following:

#!/bin/sh
sudo mount -t  vboxsf -o uid=1000 osx_shared /home/rob/ubuntu_shared

I made it executable:
sudo chmod +x mount_share.sh

Then I assigned it to run at startup:
sudo  update-rc.d mount_share.sh start 51 S .

I'm thinking it may be  either:
1) A pathing problem to the ubuntu_shared dir but, if I run  "ls -al" from inside /etc/init.d, it does find the ubunt_shared dir

2)  Trying to run as sudo from inside the script. But, since all startup  scripts run as the root user, I shouldn't even need the "sudo" in there  which I have tried to no avail.

I looked in the /var/log/debug  log but there were no errors.

Can anyone help me out with this?

---

### Post by sisco311 on 2010-04-17
Edit the /etc/fstab file & add this line:
```
osx_shared    /home/rob/ubuntu_shared    vboxsf    defaults,uid=1000
```

---

