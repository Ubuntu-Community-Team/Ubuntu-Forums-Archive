---
title: "How to improve samba server performance"
date: 2012-05-05
forum: General Help
---

### Post by Kantalias on 2012-05-05
I see performance issues related to samba, especially for reads of > 1MB in Ubuntu 12.04 32-bit.  I took some data by mounting a share from Windows 7 (64-bit with 12 GB of RAM) and running iozone from the mount point ("iozone -a -i 0 -i 1 -s 16G").  I am comparing the results to running iozone locally on the Ubuntu machine ("iozone -a -i 0 -i 1 -s 8G").  Here is a chart of both data sets:
[IMG]http://i1075.photobucket.com/albums/w427/Kantalias/ThroughputChart.png[/IMG]

The server is my home theater PC which was installed from mythbuntu 12.04, but my my issue seems to relate generically to samba.  

I watched processor utilization throughout the test and never saw the samba thread above 25% in htop.  The 1 minute utilization shown in htop was general around ~ 1.0 during >70 MB/s reads (less utilization for lower throughput reads or any write).

Here is my hardware configuration, there is only one HDD:
[IMG]http://i1075.photobucket.com/albums/w427/Kantalias/System.png[/IMG]

What can I do to increase samba performance for reads > 1 MB?

---

### Post by dcstar on 2012-05-05
> **Kantalias said:**
> 
........
What can I do to increase samba performance for reads > 1 MB?

See if this helps:

[http://ubuntuforums.org/showthread.php?t=1429532&page=3](http://ubuntuforums.org/showthread.php?t=1429532&page=3)

---

### Post by Kantalias on 2012-05-06
> **dcstar said:**
> See if this helps:

[http://ubuntuforums.org/showthread.php?t=1429532&page=3](http://ubuntuforums.org/showthread.php?t=1429532&page=3)

Thanks for your reply.  The thread you linked discusses CIFSMaxBufSize which I understand is a parameter in the client.  In my case, Ubuntu is the server and Windows 7 is the client.  I tried to find the analogy for CIFSMaxBufSize in Windows but wasn't successful.

I was able to increase the send and receive buffers in my client NIC and enable jumbo frame support.  This did not seem to have much impact (I only tested at 1, 2, and 4 megabyte record sizes because the tests take so long to run).

[IMG]http://i1075.photobucket.com/albums/w427/Kantalias/NICchanges.png[/IMG]

The 1 megabyte and 2 megabyte read performance did not appear to change at all, larger record sizes may get some read and write performance increase from the changes.

Anyone know if there are client-side parameters that can/should be adjusted in Windows?

---

### Post by Kantalias on 2012-05-07
Could there be a server-side setting that needs to be optimized?

---

### Post by Kantalias on 2012-05-14
Would I have better luck getting help if I used an Ubuntu client as well as Ubuntu server?

---

