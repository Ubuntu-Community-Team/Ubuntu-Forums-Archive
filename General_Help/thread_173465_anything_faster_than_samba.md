---
title: "anything faster than samba?"
date: 2006-05-10
forum: General Help
---

### Post by xela321 on 2006-05-10
Is there any way of transfering files over a network that's faster than smaba? Right now I'm moving ~220GB of data to my ubuntu machine from my server2k3 machine and the throughput is HORRENDOUS (~20mbits/sec).  windows-to-windows transfers are about 300mbits a sec (i have gigabit ethernet).  All of my network cards are GigE, my switch even shows the ubuntu machine with a 1000mbps link light.  It seems that transfering the files takes up about 50% of my cpu, which never happened under windows.  The ubuntu machine is an athlon xp 2600 with a gig of ram.

---

### Post by IYY on 2006-05-10
You could try FTP.

---

### Post by xela321 on 2006-05-10
i just tried sftp and i'm getting the same results...

any ideas?

---

### Post by xela321 on 2006-05-10
also, after further investigation, smbd is taking up only 10% CPU usage...
Any guesses?

---

### Post by xela321 on 2006-05-10
Just changed snd and rcv buffers to 8192, i'm up to 40mbits/sec now... i was able to get 6 times that speed under windows :(
HELP!

---

### Post by aineko on 2006-05-10
[QUOTE=xela321]Just changed snd and rcv buffers to 8192, i'm up to 40mbits/sec now... i was able to get 6 times that speed under windows :(
HELP![/QUOTE]

I use NFS instead of Samba, so this may not work for you, but NFS is much faster over gigabit ethernet using 32K buffers.

For Windows to UNIX file transfers, I typically use rsync, so you might want to look into that.  You can install it on Windows under Cygwin.

It's also possible that you're running into disk limitations.  How much free memory does your Linux system have for disk cache?  How fast is your disk according to hdparm?  Are file/directory creation times eating up a lot of your time?

---

### Post by mjziegle on 2006-05-10
You should use ftp NOT sftp.  ssh and sftp have a protocol overhead limitation that will limit your transfer rates.  

Your problem isn't likely to be samba itself.  I can get 8-10 MB/s over 100Mbit ethernet over samba.  It's not unreasonable for cheap gibabit cards to use huge chunks of CPU if they don't have an onboard processor.  Also you might be having problems with authentication from windows to samba.

I recommend raw ftp.

Are you sure your are seeing 300 Mbit/s on Windows.  That's almost 40 MB/s.  That's about the maximum sustained transfer rate of most 7200rpm disks.  

Good luck.

-Matt

---

