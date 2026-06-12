---
title: "Anyone successfully running Lucid or Maverick as an NFS client?"
date: 2010-09-19
forum: General Help
---

### Post by getnuked on 2010-09-19
A week ago I installed a fresh lucid 10.04 amd64 desktop onto a workstation (Athlon II 240, 4GB ECC RAM, 1TB SATAII disk). Within a day this machine locked up with no response to keyboard or mouse. I could ping it yet I couldn't ssh to it, luckily Magic sysrq + REISUB was able to sync the local disk, yet it wouldn't reboot. After looking at the logs I noticed the nfs and kswap errors that eventually brought me to **[launchpad bug #561210]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561210")**.

To make a long story short, the net result is that there is a bug with the nfs client in the kernel that is affecting Lucid and Maverick (I tested two kernels, 2.6.32 for Lucid and 2.6.35), that causes the client machine to lock up (others have commented that Karmic is also affected by this bug, yet I don't have any first hand experience to confirm or deny this). The most recent Ubuntu release that I know for a fact works reliably with nfs mounts is Jaunty (I have been using 9.04 without any nfs problems for over a year now on many workstations that I maintain).

Now I am aware of the many problems people are having with Lucid locking up their computers (including crashes). The problem I and many others are having is a lock up (lack of response to keyboard and mouse) that is related to nfs mounts, and can be easily reproduced (there are several test cases describe in the bug).

What I am hoping to do with this thread is to

[LIST=1]
[*]determine if there is anyone who has had any success with mounting via nfs in Lucid or Maverick so that I can try to determine what factors I, and the others who are affected by this bug can do to potentially work around it
[*]make more people aware of this bug so that if they are experiencing the same nfs lock ups they can hopefully benefit from any fix that might be forthcoming
[/LIST]

---

### Post by imbjr on 2010-09-20
> **getnuked said:**
> A week ago I installed a fresh lucid 10.04 amd64 desktop onto a workstation (Athlon II 240, 4GB ECC RAM, 1TB SATAII disk). Within a day this machine locked up with no response to keyboard or mouse. I could ping it yet I couldn't ssh to it, luckily Magic sysrq + REISUB was able to sync the local disk, yet it wouldn't reboot. After looking at the logs I noticed the nfs and kswap errors that eventually brought me to **[launchpad bug #561210]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561210")**.

To make a long story short, the net result is that there is a bug with the nfs client in the kernel that is affecting Lucid and Maverick (I tested two kernels, 2.6.32 for Lucid and 2.6.35), that causes the client machine to lock up (others have commented that Karmic is also affected by this bug, yet I don't have any first hand experience to confirm or deny this). The most recent Ubuntu release that I know for a fact works reliably with nfs mounts is Jaunty (I have been using 9.04 without any nfs problems for over a year now on many workstations that I maintain).

Now I am aware of the many problems people are having with Lucid locking up their computers (including crashes). The problem I and many others are having is a lock up (lack of response to keyboard and mouse) that is related to nfs mounts, and can be easily reproduced (there are several test cases describe in the bug).

What I am hoping to do with this thread is to

[LIST=1]
[*]determine if there is anyone who has had any success with mounting via nfs in Lucid or Maverick so that I can try to determine what factors I, and the others who are affected by this bug can do to potentially work around it
[*]make more people aware of this bug so that if they are experiencing the same nfs lock ups they can hopefully benefit from any fix that might be forthcoming
[/LIST]

I've experienced relatively minor lock-ups, i.e. Gnome locking on the shared directory, visibly twice now. The logs suggest though that 3 times the NFS server has just stopped responding and a reboot/restart of services was required. So far, this has only happened when listening to music shared on the server.

The logs have not indicated anything that would suggest a cause for this. I did suspect DHCP problems, but that does not appear to be the case.

---

### Post by getnuked on 2010-09-20
@imbjr it may very well be the same problem as the only way to recover from the lock up described in the bug is to reboot your computer. Were you able to recover your computer or did you have to reboot it? If you were forced to reboot, did the logs look similar to those shown in the bug?

---

### Post by imbjr on 2010-09-20
> **getnuked said:**
> @imbjr it may very well be the same problem as the only way to recover from the lock up described in the bug is to reboot your computer. Were you able to recover your computer or did you have to reboot it? If you were forced to reboot, did the logs look similar to those shown in the bug?

I attempted service restart, but I also logged out and back in. A combo, or one of the above, fixed it. Not a restart.

Next, time I shall attempt a service restart, now I know exactly what it is I should restart.

---

### Post by b00nish on 2010-10-13
Hello

Maybe I'm experiencing a smilar problem:
I'm running a NFS Server (Kubuntu 10.04) on which I accessed sucessfully with my Kubuntu 8.04 client for a long time. Now I upgraded the client to 10.10 and experience huge problems. My client totally locks up (freeze) on various NFS related actions:
Unzipping a big file from the NFS server to the NFS server -> always immediate freeze
Transfering big files from one NFS folder to another -> mostly immediate freeze
Viewing a movie which is on the NFS server -> sometimes freeze

For me NFS is of course totally useless like this and I'll have to downgrade again to 8.04 if I don't find a solution quickly.

---

### Post by davrosuk on 2010-10-13
I have a Lucid server running NFSv4 (v3 to start with but transitioned very quickly to v4). I'm serving Lucid and Maverick client machines. As far as I can tell I've yet to have a single issue - and thats not from lack of use... The server is hosting several mounts to a 6TB volume.

---

### Post by kirodude on 2010-10-15
Hi I just upgraded to Maverick (both server & clients) and I'm having the issues I'll describe below. I googled like crazy but I haven't yet find the solution.

For some reason, files dissappear at client level after a certain time, and only "reboot" makes them appear again (and they dissapear again after a certain time).

Exports in server are like this (HD_EXTX are USB external disk x 3):

/home/kiro/HD_EXT1   192.168.0.0/24(rw,nohide,insecure,async,no_subtree_check,fsid=1)
/home/kiro/HD_EXT2   192.168.0.0/24(rw,nohide,insecure,async,no_subtree_check,fsid=2)
/home/kiro/HD_EXT3   192.168.0.0/24(rw,nohide,insecure,async,no_subtree_check,fsid=3)
/home/kiro/xbmc      192.168.0.0/24(rw,nohide,insecure,async,no_subtree_check,fsid=99)

[[FSID=XX is my latest attempt to fix the issue, no luck though]]

Fstab in one of the clients:

storage:/home/kiro/HD_EXT1    /home/kiro/HD_EXT1  nfs4 _netdev,auto  0  0
storage:/home/kiro/HD_EXT2    /home/kiro/HD_EXT2  nfs4 _netdev,auto  0  0
storage:/home/kiro/HD_EXT3    /home/kiro/HD_EXT3  nfs4 _netdev,auto  0  0
storage:/home/kiro/xbmc       /home/kiro/.xbmc    nfs4 _netdev,auto  0  0

Everything connects fine, I see the mounts on the client perfectly, I can read, write, whatever.

In Nautilus (or even XBMC as you might have guessed I'm using), after a certain time, files disappear, but oddly enough, if I open a terminal in the client and browse the mounted shares, I see all the files.

When trying to view a video in XBMC, sometimes it will say that the file is no longer available, then insisting a couple of times might make it reappear, but most of the times not.

I'm starting to believe it has something to do with the shares on the server being USB disks (FAT32 formatted) , but I couldn't be sure.

These are my experiences with NFS and lucid/maverick.

---

### Post by amgalitz on 2010-10-29
I had similar problems traced to a network switch that needed a reboot after a ups failed. The switch was only passing 100Mb instead of 1000Mb. Also double check your cables and ensure they are good or swap with new ones (where possible).  

To reduce server load I set noatime for the shares on the server. I'm now getting large file copies at 30MB/sec from share to local drive with a non-raid server with moderately fast drives. During the problem I was getting as low as 1MB/sec which explained the client pauses.

this is my entry in the client /etc/fstab:
```
192.168.1.253:/ /server1 nfs4  _netdev,noatime,auto 0 0

```

I also have noatime for the folders on the server itself just in case. (I'm not an expert, just faking it<G>).

Working fine now.

cheers

---

### Post by b00nish on 2010-11-23
At the Bugtracker, there is currently this bug discussed:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661294](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661294)

It's about system lock-up when *receiving* big data amounts from NFS targets (so it seems to be the contrary to the bugreport mentioned above which is about lock-ups when *sending* big data amounts to a NFS target)

Hopefully this issue will be resolved. 
But when I see that the 'old' bug (#561210) hasn't been resolved since April I don't know if we can be very optimistic...

---

### Post by _K. on 2010-12-29
Not sure if this issue is solved or not, but I just installed Lucid 10.10 and am able to receive a large chunk of data (~7Gb) without any problem as an nfs client.

---

### Post by sean.clarke on 2011-02-16
Yep, I am continually hitting this issue on Maverick x64 running KVM images over NFS the system is unusable.

---

