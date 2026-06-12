---
title: "File properties takes a long time to open"
date: 2010-05-06
forum: General Help
---

### Post by Daliz on 2010-05-06
Hey all ):P

I have a newly installed Kubuntu 10.04 running here, works fine except for one thing.

I have a kind of "fileserver" and it has a samba share that I have mounted in the home folder of my desktop computer ("/home/xxx/fileserver", the server is running an older version of Ubuntu, can't exactly remember what it is but the filesystem is ext2, if that's of any importance).

I have large files on the server, mostly video. When I use Dolphin (or Konqueror, doesn't make any difference) and right click one of these large files and choose Properties, it takes a LONG time to load the properties window. As if it copies the file to local hd before opening properties, or something.

The reason why I posted here and not in the networking section is, that I had the exact same setup with my previous installation which was Kubuntu 8.04, and also at least three different Ubuntu's before that. Never had this problem before, so I think my server and networking thingies are okay.

Any ideas?

---

### Post by werepacman on 2010-05-27
I don`t use samba and don`t have file server.
But i have the same problem with dolphin.

I noticed dolphin uses about 5% CPU before shows file properties. It reminds me nepomuk. So I guess it related to some resourses hungry function which is possible to switch off. Previous versions of Kubuntu haven`t this problem.

---

