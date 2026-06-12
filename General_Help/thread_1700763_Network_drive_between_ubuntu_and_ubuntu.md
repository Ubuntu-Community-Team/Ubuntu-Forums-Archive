---
title: "Network drive between ubuntu and ubuntu"
date: 2011-03-05
forum: General Help
---

### Post by mohsinhijazee on 2011-03-05
I have an Ubuntu 10.10 machine and a laptop with the same. My desktop machine has two hard drives. One is 40 GB with Linux installed and other contains mostly FAT32 partitions for data. How can I mount that drive as such that it is accessible to me from my laptop all the time?

I am sorry if the question is in the wrong forum or too naive.

---

### Post by maedox on 2011-03-05
You could use Samba, NFS or SSHfs. Samba is used if you right-click a directory and select "Sharing options". It's made to be easy to setup so it is mostly automatic and should show up under "Network" on your laptop as long as there isn't a firewall or anything stopping the communication.

---

### Post by mikewhatever on 2011-03-05
Samba sharing seems to be the easiest way to go. Just note, you don't mount hard drives, but partitions. Here is how to easily setup samba server.
[http://www.unixmen.com/linux-tutorials/1060-how-to-configure-samba-using-a-graphical-interface-in-ubuntu](http://www.unixmen.com/linux-tutorials/1060-how-to-configure-samba-using-a-graphical-interface-in-ubuntu)

When done, you should be able to see the shared folders from other computers by going Places->Network.

---

