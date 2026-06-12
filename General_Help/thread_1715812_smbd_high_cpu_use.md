---
title: "smbd high cpu use"
date: 2011-03-27
forum: General Help
---

### Post by seldenr82 on 2011-03-27
I'm running ubuntu 10.10 x64, dualcore amd 1.9ghz, 2gb ram, soft raid 5 (4 x 1 TB, 64kb chunk), with samba serving two shares. Connecting to my server over a gigabit lan, i'm achieving write speeds of around 50MB/s, however htop indicates that smbd is pushing cpu core 1 to nearly 100%, and core 2 to around 30%. Below is a copy of my smb.conf, any suggestions on what I can do to reduce cpu utilization?

********************************************************
[global]
        workgroup = HOME
        netbios name = Mybox
        secuirty = user
        encrypt passwords = true
        socket options =IPTOS_LOWDELAY TCP_NODELAY SO_RCVBUF=65535 SO_SNDBUF=65535

[Data-RO]
        comment = Read Only
        path = /data
        valid users = robert, becky, elizabeth
        browsable = yes
        read only = yes
        guest ok = no

[Data-RW]
        comment = Read Write
        path = /data
        admin users = robert
        read only = no
        browsable = yes
        guest ok = no
        write cache size = 65535
**************************************************************

---

