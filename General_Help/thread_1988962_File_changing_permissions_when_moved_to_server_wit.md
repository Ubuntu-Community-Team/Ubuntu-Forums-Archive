---
title: "File changing permissions when moved to server with SSH"
date: 2012-05-28
forum: General Help
---

### Post by bike756 on 2012-05-28
I'm having trouble moving seemingly arbitrary files to a server with SSH. I'm connecting to my server with SSH through Nautilus and using that to move files around. Sometimes i notice a file that is on my server isn't showing up on my website, so I go and check it's permissions and sure enough it's set so that others have no access to read the file. At this point I right click on the file, go to properties->Permissions and try to change the settings(see attached image). But it keeps changing the setting back to none!

I tried logging into Nautilus as root, but it doesn't seem to want to let me connect to the server when I do that. I also tried changing the permissions locally as root and then uploading the file to the server again, but the permissions keep reverting to none.

How can I fix this? It's not worth much to be able to upload files to a server if I can't make them accessible!

---

### Post by maverickaddicted on 2012-05-29
Check the ownership of those files? Run this command in the folder, where you are trying to change the permission.
```
ls -l
```

---

