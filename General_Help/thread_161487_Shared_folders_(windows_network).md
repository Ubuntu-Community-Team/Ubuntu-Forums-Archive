---
title: "Shared folders (windows network)"
date: 2006-04-17
forum: General Help
---

### Post by Sonique on 2006-04-17
Hi guys, I need so help:

What I want is to have a shared folder ( /home/simon/Desktop/Shared ). So what I did was go System>Admin>Shared Folders. Pressed Add and filled in the details (Read only unticked, Allow browsing folder ticked). Pressed Ok. But the folder /home/simon/Desktop/Shared is now owned by root and I cannot drag any files into it as I don't have permission (I didnt have to log in to root when opening Shared Folders).

---

### Post by The Mekon on 2006-04-17
I don't quite know what you are trying to do but a quick and easy way to change Ownership or Premissions is:

Open a Terminal

Enter 'sudo nautilus', you will probably have to entre your password.

Locate the file you wish to change. right Click, select Properties followed by Permissions and you are presented with a nice window where you can change the ownership and permissions to your heart's desire.

Brian

---

### Post by kaph on 2006-04-17
Have you set up Samba (smb shares)? This will allow your to designated folders to be visible and compatable on your existing (or soon to exist) windows network. I'm not too sure what you mean either but maybe this has helped. As for further help with smb, ya'd better not take advice from me because i bumble my way through things and end up doing things the hardest way possible :) but i do get things done.......
Cheers, Kaph.

---

