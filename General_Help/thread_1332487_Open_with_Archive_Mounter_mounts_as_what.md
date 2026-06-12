---
title: "Open with Archive Mounter mounts as what?"
date: 2009-11-20
forum: General Help
---

### Post by nowhere@cox.net on 2009-11-20
Question:
I recently tried out the Open with Archive Mounter option on the nautilus right click menu to mount and iso file. In the past I used a script or I used```
sudo mount -o loop file.iso mount_point_folder
```

If I did either of these, the CD icon would pop up on the desktop with the name of the iso file as the name of the icon (no .iso extension) and I could right click it and Open with Movie Player if it was a DVD. When I use the Open with Archive Mounter option, I get an icon on the desktop of a different type, the .iso extension is in the name on the icon and I cannot use the Open with Movie player. In fact all I can do is open it from the right click menu. There isn't even an :"Open with other application" option.

Not sure what to do about it...

Any ideas?

---

### Post by Giblet5 on 2009-11-20
Archive manager is more to let you grab files from an iso.

If you want a GUI tool to mount them, install the gmountiso package. It just does the mount -o loop thing, but from a GUI! ;)

---

### Post by rahilm on 2009-11-20
I think Archive mounter uses gvfs-mount to mount all types of files. This is a different method of mounting which doesn't require root privilege.
I've seen that almost all dvd iso or data cd iso have a ;1 extension added to them, so the Totem doesn't recognise it as a dvd.
Try to see if the mounted dvd has ;1 sufix added to each file.

---

### Post by nowhere@cox.net on 2009-11-20
No numerical extension on mine on the desktop or in the .gvfs folder. Just the .iso. 

I used to use the one of the mount gui's but it was tiresome entering the password all the time and it got out of sync all the time and I ended up having to cd to the mount location and umount it from the command line.

Also the gui's all want an existing folder to mount on and I didn't want to create a bunch of folders. Also, the name of the disk wasn't visible just the name of the mount folder and that got confusing when more than one were mounted. 

I'm wondering where the Archive Mounter (Not Archive Manager) functionality is so perhaps I can modify it?

---

