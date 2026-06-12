---
title: "Samba Mount not appearing in when I try to attach"
date: 2010-08-06
forum: General Help
---

### Post by parisv on 2010-08-06
I've mounted a windows share in places. When I look at computer in places it shows down the left hand side.

When I write an email in Thunderbird and go to attach it does not show down the left. Firefox doesn't see it either when attaching from gmail. But open office and do a save as it does see it.

---

### Post by Morbius1 on 2010-08-06
Mounting a remote share in places creates a mount point at this location:
> /home/your_user_name/.gvfs/share_name on server_nameIt's the ".gvfs" part of that path that's the problem The developers are playing a practical joke on us users and made the mount point a "hidden directory"

When you're in Thunderbird and go to attachments an "Attach Files" dialog box opens up. Right click an empty space in that dialog box and select "Show Hidden Files". You should be able to go to the ,gvfs directory to find the remote share.

---

### Post by Kakers on 2010-08-06
You could also get around it by mounting the windows share as a drive. [http://industriousone.com/blog/mounting-windows-shares-linux](http://industriousone.com/blog/mounting-windows-shares-linux)

---

### Post by parisv on 2010-08-06
Thanks, strange how open office can see it though!

---

