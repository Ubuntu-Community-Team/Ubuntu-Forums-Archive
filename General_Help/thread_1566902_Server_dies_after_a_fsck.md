---
title: "Server dies after a fsck"
date: 2010-09-03
forum: General Help
---

### Post by dynamo21 on 2010-09-03
HI THERE!  ):P

Anyone can help me???

Situation:

i have a ubuntu 10 server (as server LAMP) , i was trying to repair a couple of unix files with fsck command on directory, thinking it would apply only that directory, but it affected all system, in th end it says: "file system has changes, restart ubuntu", then services go down, after some directories fail, restart funtion do anything... i switched on again, but at start show error.

I got another ubuntu and installed damaged hard disc, but, i can see file sytem, i has been trying to repaired with TestDisk but i can't...  ](*,)

i want to recover mysql database at least, but a don't know what to do.... how a fsck get damaged SO

Please somebody heeeelp!!

---

### Post by dcstar on 2010-09-03
> **dynamo21 said:**
> HI THERE!  ):P

Anyone can help me???

Situation:

i have a ubuntu 10 server (as server LAMP) , i was trying to repair a couple of unix files with fsck command on directory, thinking it would apply only that directory, but it affected all system, in th end it says: "file system has changes, restart ubuntu", then services go down, after some directories fail, restart funtion do anything... i switched on again, but at start show error.

I got another ubuntu and installed damaged hard disc, but, i can see file sytem, i has been trying to repaired with TestDisk but i can't...  ](*,)

i want to recover mysql database at least, but a don't know what to do.... how a fsck get damaged SO

Please somebody heeeelp!!

Doing a fsck on a mounted partition is an invitation to disaster - that is why all those warning messages exist.

---

### Post by dynamo21 on 2010-09-03
> **dcstar said:**
> Doing a fsck on a mounted partition is an invitation to disaster - that is why all those warning messages exist.
 
 
Yes, i thought that fsck affect posicionated directory... but it take everything
 
There is some way for repair ir or extract files, a tool , or something??

---

