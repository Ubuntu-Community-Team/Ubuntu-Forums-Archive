---
title: "Directory permission, Operation not permitted."
date: 2009-10-15
forum: General Help
---

### Post by iTheBadGuy on 2009-10-15
I typed 

```
chmod -R 775 /usr/share/vuze
```but keep getting "Operation not permitted". What am i doing wrong?.

Reason i want to change the permission is, Vuze is telling me it needs permission to its directory so it can update correctly, and something about vuze's security not working properly if it doesn't have access to the directory.

I'm a newbie, i've only been using Ubuntu for about a month.. but i'm lovin' it :D

---

### Post by iKonaK on 2009-10-15
Try with sudo: 
```
 sudo chmod -R 775 /usr/share/vuze
```
...assuming that 775 is what you need...

---

### Post by iTheBadGuy on 2009-10-15
Well, isn't 775 what i need? i just need to give vuze permission to use the directory, i installed it with my account, not root... so should giving me permission to the directory be enough?. 

I gave myself permission to the directory, read+write. But vuze continues to give me the error.. i'll try running vuze in terminal with sudo, lets see if like this it doesn't give me problems...

God.. i ran it with sudo, it didn't give me any problem.. no errors no nothing.. But now it doesn't let me add a torrent. when i add the torrent it freezes, and i have to force quit. nice...

Is there a good torrent downloader that looks something like uTorrent? ( simple interface, easy to use.. etc etc.. )

---

### Post by iKonaK on 2009-10-15
Well, chmod dosen't give permissions to applications but users, and now that I look closer that 755 should fix the problem. :|
Also you should try avoid using root for anything ;)

---

### Post by iKonaK on 2009-10-15
> **iTheBadGuy said:**
> 
Is there a good torrent downloader that looks something like uTorrent? ( simple interface, easy to use.. etc etc.. )
You should try Transmission and/or Deluge.
Also try 777, if only works with "rwx".

---

### Post by iTheBadGuy on 2009-10-15
Thank, i decided to just use Deluge..

---

