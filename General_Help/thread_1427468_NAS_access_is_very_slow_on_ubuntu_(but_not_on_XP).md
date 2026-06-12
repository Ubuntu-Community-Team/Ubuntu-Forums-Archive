---
title: "NAS access is very slow on ubuntu (but not on XP)"
date: 2010-03-11
forum: General Help
---

### Post by zainka on 2010-03-11
Hi 

I have this sitecom MD-253 NAS disk using Raid-1 and equipped with two 1TB WD hdd's. The NAS firmware is Linux of some cind and I use the, pr. today, latest firmware.

However, as mounting the NAS server was not any challenge, the response time is in the most shamefully end of the scale. Even listing folder content is deadly slow, beeing from one to three second before list is shown. Both the linux laptop and the NAS is connected through cable via the router, the XP however, is wireless but access is no problem here.

I found a few tutorials around dealing with mounting the NAS drive but few which dealt with the speed issues and none solving my problems. I saw one post in another forum though discussing if the problem could be caching but they had no solution.

I have used different commands mounting, but at the moment i use this one in fstab:

```
//192.168.0.190/Projects /mnt/nas cifs username=zainka,password=********,_netdev,uid=zainka,gid=users 0 0

```

Response time is not affected though. That is, for FTP the responce time is actually higher but then I run into other issues like that mounting it like a disk is difficult and the link must be keept alive constantly 

I also seen some comments about using NFS but isn't this a proprietary MS protocol for file access???

Hope someone can help me.

My system is xubuntu.

---

### Post by dcstar on 2010-03-11
> **zainka said:**
> Hi 

I have this sitecom MD-253 NAS disk using Raid-1 and equipped with two 1TB WD hdd's. The NAS firmware is Linux of some cind and I use the, pr. today, latest firmware.

However, as mounting the NAS server was not any challenge, the response time is in the most shamefully end of the scale. Even listing folder content is deadly slow, beeing from one to three second before list is shown. Both the linux laptop and the NAS is connected through cable via the router, the XP however, is wireless but access is no problem here.

I found a few tutorials around dealing with mounting the NAS drive but few which dealt with the speed issues and none solving my problems. I saw one post in another forum though discussing if the problem could be caching but they had no solution.

I have used different commands mounting, but at the moment i use this one in fstab:

```
//192.168.0.190/Projects /mnt/nas cifs username=zainka,password=********,_netdev,uid=zainka,gid=users 0 0

```

Response time is not affected though. That is, for FTP the responce time is actually higher but then I run into other issues like that mounting it like a disk is difficult and the link must be keept alive constantly 

I also seen some comments about using NFS but isn't this a proprietary MS protocol for file access???

Hope someone can help me.

My system is xubuntu.

Try smbfs instead of cifs.

---

### Post by zainka on 2010-03-12
Done that, been there. That was the first try.

---

