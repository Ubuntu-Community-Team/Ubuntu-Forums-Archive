---
title: "Managing users and groups"
date: 2011-06-13
forum: General Help
---

### Post by BandD on 2011-06-13
I have an "inconvenience" whereby I have a streaming music server (tied to hi-fi equipment) called Squeezebox Server installed on my 11.04 machine.  The way the porgram operates is to run as it's own user, namely squeezeboxserver, rather than the user that invoked it.  

Now I want this user (squeezeboxserver) to have access to my music that is stored in ~/Music, and ~/ is encrypted.  The only way I can seem to grant this (with my limited knowledge of users, groups, and permissions) is to ```
chmod -R 755 ~/
```

This is not ideal for me.  Granted there aren't really any other users created on this machine (other than what's there by default), but I don't really like the idea that if someone, somehow, through some security vulnerability or some such, gained access to one of those users, that they could just peruse my entire home directory.  Instead, I'd rather create a "music" group and squeezeboxserver and I are both a part of and then set the permissions accordingly.  

Trouble is, I don't really fully comprehend the right way to go about this.  I know how to change permissions.  I know how to add groups and add users to groups.  But I don't know how to give certain groups access to certain folders.  It would be a great help if someone could help walk me through the process, at least the logic behind what I need to do.

---

### Post by BandD on 2011-06-15
I just can't quite figure this out.  Can any one help?

---

