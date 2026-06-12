---
title: "fuse"
date: 2009-10-07
forum: General Help
---

### Post by textas on 2009-10-07
Hi - completely new to ubuntu, so please excuse me if my question sounds dumb
i'm discovering flickrfs and the magics it involves; i really would like to get this working and learn more about this fuse system and how i could use it

at the moment it seems i'm having troubles with mounting when i'm trying to get Flickrfs to run; i follow the instruction and get stuck with step 2 (not far) from [URL="http://manishrjain.googlepages.com/flickrfs#ubuntu"]http://manishrjain.googlepages.com/flickrfs#ubuntu
[/URL] ```
sudo modprobe fuse
```terminal returns:
```
FATAL: Module fuse not found.
```* it also seems like there's nothing like [FONT=trebuchet ms][COLOR=#663300]/usr/bin/fusermount [COLOR=Black]
is it coming from the distinction in between module and kernel?
if so, how can i translate the instructions?[/COLOR][/COLOR][/FONT]

i've been reading a few thread on the forum but nothing solved it (user fuse group is ok)
i tried to use sshfs (i understand fuse and sshfs are related in some yet-obscure ways)
and got a similar error:
running:```
sshfs -o idmap=user %USER@domain.net:/distantDir ~/distantDir
```returns:```
fusermount: mount failed: Operation not permitted
```The distribution is Jaunty 9.04 - not sure if any other details are needed, please advise and let me know. Many thanks in advance

---

### Post by BarsMonster2 on 2009-10-23
Same error here, Ubuntu Server 9.04 64-bit :-(

---

### Post by iDVB on 2010-04-18
Triple that. I have the same issue. 9.04

---

