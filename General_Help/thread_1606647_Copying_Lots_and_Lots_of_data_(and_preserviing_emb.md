---
title: "Copying Lots and Lots of data (and preserviing emblems)"
date: 2010-10-26
forum: General Help
---

### Post by jkounis on 2010-10-26
I am currently in the process of moving around 20TB of data from one server to another. Security is not a concern, since the data are freely available to anyone on our network anyway. There are a couple of things that I'm trying to decide on:

(1) protocol choice

Of all the choices I have--nfs, ftp, scp, rsync, samba--has anyone done any benchmarking to show which would be the fastest/most robust transfer protocol? I know nfs has slow write speeds for synchronous transfers. Asynchronous would be faster, but less robust. I'm leaning toward rsync since it performs md5sums to confirm the file transfers. (Remember if there's a 1 in a billion chance that a byte will get corrupted, then I'll have 20,000 corrupt bytes in the transfer.) 

Any comments?

(2) Nautilus emblems

We use emblems in Nautilus to categorize files. The old and the new server have the same directory structure.

Is there any way to copy the Nautilus emblems from the old server to the new server. What I want is that if a user had marked a particular file with a star on the old server, then that file would be marked with a star on the new server when he/she logs in.

---

### Post by jkounis on 2010-10-27
Since nobody indicated that they had done benchmarking, I ran my own tests. Here are the results for those who are interested: 
     nfs: 37 MB/s
     rsync via ssh: 22 MB/s
     rsync via daemon: 24 MB/s
     scp: 10 MB/s

nfs wins.

For the nfs test, the source machine was configured as the server, and the destination machine was the client. That way, the disk writes occurred locally and I didn't have to worry about the synchronous/asynchronous write issue.

---

