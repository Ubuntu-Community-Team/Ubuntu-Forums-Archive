---
title: "Access windows data in ubuntu 9.04 and vice versa"
date: 2009-07-17
forum: General Help
---

### Post by nipunreddevil on 2009-07-17
I recently installed ubuntu 9..04 inside windows vista and am not able to access my windows data in ubuntu and vice versa.
Was able to access windows data in ubuntu with earlier versions when i had installed ubuntu on a separate drive.

---

### Post by Tman5293 on 2009-07-17
You need to set up share folders on both operating systems

---

### Post by nipunreddevil on 2009-07-17
Thank you for your response.
But how do we setup shared folders on both.

---

### Post by litspliff on 2009-07-17
ubuntu can use smb and windows uses smb natively for sharing.

windows can not use NFS without doing some bullsht.


this is not a windows forum, so in brief, in the windows machine, right click on the folder you want shared, then setup a fileshare under properties.


once you mount that windows fileshare on your ubuntu machine, you can share files seamlessly. i use smb4k, but i think ubuntu comes with crappy smb support that might work. 

it doesn't authenticate with my windows servers properly, so if you have trouble on the ubuntu machine, just "sudo apt-get install smb4k", run it, go to settings->configure then setup your kwallet password and your default login information. after that, you can bookmark the windows share, and easily keep it mounted on your ubuntu machine.

---

### Post by nipunreddevil on 2009-07-18
I found a better way .
your windows drive is under filesystem/host
i think this problem arised since i used wubi to install ubuntu in windows
in a clean install this does not happen.
still trying to figure out how to see ubuntu data in windows

---

