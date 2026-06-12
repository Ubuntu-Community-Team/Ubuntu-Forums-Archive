---
title: "file_permission"
date: 2012-02-27
forum: General Help
---

### Post by gnakul on 2012-02-27
Hi all, i am new to linux.
I have a ubuntu 10.04 server and i am sharing files with windows computers through samba. i have /home/share and i have shared the directory 'share' which is under /home. The problem is the files inside the share directory will be read only to other users except root, when we login remotely from windows computer. If i change the permission as read and write, it will go back to read only again after sometime automatically. What to do?

Thanks in advance for help
-Nakul

---

### Post by raja.genupula on 2012-02-27
Hi may be this could help you 
[https://help.ubuntu.com/community/Samba/SambaServerGuide#Global_Settings](https://help.ubuntu.com/community/Samba/SambaServerGuide#Global_Settings)

---

### Post by gnakul on 2012-02-27
@raja.genupula: Thanks for reply. As per the link you suggested I have given writaable as yes.


[Share]
        path = /home/Share/
        writeable = yes
;       browseable = yes
        guest ok = yes

But files inside 'share'folder i need to click right mouse button everytime and give permission as Read and Write. But again after sometime it will change automatically to read only.

Thanks.

---

