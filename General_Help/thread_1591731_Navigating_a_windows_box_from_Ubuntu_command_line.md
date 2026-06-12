---
title: "Navigating a windows box from Ubuntu command line"
date: 2010-10-09
forum: General Help
---

### Post by malleeblue on 2010-10-09
I'm in Ubuntu and want to navigate the directories of a Windows box upstairs. I can see it and navigate around the shared folders using the file browser (the address bar shows smb://computername/shared-directory/) but how do I navigate around using the command line? The IP addy of the upstairs computer is 192.168.0.199.

FYI: If this is posted somewhere else I couldn't find it.

---

### Post by dcstar on 2010-10-09
> **malleeblue said:**
> I'm in Ubuntu and want to navigate the directories of a Windows box upstairs. I can see it and navigate around the shared folders using the file browser (the address bar shows smb://computername/shared-directory/) but how do I navigate around using the command line? The IP addy of the upstairs computer is 192.168.0.199.

FYI: If this is posted somewhere else I couldn't find it.

Put in a /etc/fstab entry for the device and then simply go to the mount point.

---

### Post by malleeblue on 2010-10-10
> **dcstar said:**
> Put in a /etc/fstab entry for the device and then simply go to the mount point.

Keep newbies in mind when writing replies as posts can and will be viewed by many people over time.

So with that said, please tell me how I would add the drives of the upstairs computer to my fstab. I know how to add a local drive or external HDD to fstab but not a networked computer or drive.

Thanks.

---

### Post by marshmallow1304 on 2010-10-10
By default, the windows share should mount in ~/.gvfs, so
```
cd ~/.gvfs/name-of-share
```

EDIT: Note that the name-of-share is usually long and complicated, so use tab-completion.

---

### Post by malleeblue on 2010-10-10
> **marshmallow1304 said:**
> By default, the windows share should mount in ~/.gvfs, so
```
cd ~/.gvfs/name-of-share
```

EDIT: Note that the name-of-share is usually long and complicated, so use tab-completion.

That's done it. Thanks **marshmallow1304**.

---

