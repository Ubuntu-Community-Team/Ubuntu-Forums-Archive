---
title: "trouble moving files to trash (mounting issue maybe)"
date: 2011-05-06
forum: General Help
---

### Post by 200k on 2011-05-06
Hello all I am running 11.04 x64 and have mounted my 2tb hdd in fstab as the following:

dev/sdb1 /media/sdb1 ntfs-3g defaults 0 0

Whenever I go to any directory in the drive and try to delete any file or folder I get the following message:

Cannot move file to trash, do you want to delete immediately?

I did notice in the root of the hdd there is no .Trashes-1000 folder, would this be the problem?

Also in any other file system for example my flash drives, or hdd ubuntu is installed on, if i attempt to delete a file or folder it auto moves it to the trash, isnt it standard to ask before moving to the trash?

What should I do to fix this?
Thanks in advance!

---

### Post by spikoley on 2011-05-07
I am not an expert on this, but I have noticed that files deleted from a removable device add it to the trash folder on that device.  I think you are on to something with the removable device not having its own trash.  I am not sure how to fix it.  Try manually creating the trash folder on the drive.

---

### Post by Morbius1 on 2011-05-07
>  dev/sdb1 /media/sdb1 ntfs-3g defaults 0 0That line in fstab will mount with owner = root and with read / write permissions to everyone.

When you as non-root user attempt to send something to the trash the system will try to comply by sending it to the owner of the trash and that's root. Since you are not root you get an error.

Take possession of the mounted partition and trash becomes yours:
>  dev/sdb1 /media/sdb1 ntfs-3g defaults,uid=1000 0 0[I]Yet another reason not to use ntfs-config :wink:

[COLOR=Blue]**EDIT:**[/COLOR] Forgot a couple of steps. Changing fstab by itself will not get you an immediate result. You will have to unmount the partition:
[/I]```
* sudo umount /media/sdb1*
```[I]
Then run the following command to mount with the new parameters:
[/I]```
*sudo mount -a*
```

---

### Post by sam1948 on 2011-05-07
hi,
i saw the problem when using fstab for mount instead of the default ubuntu auto-mount.
have you tried not to mount it manually but letting ubuntu mount it automatically ?
there are many discussions about how to mount using fstab and still allow .Trash to work but i didn't dig into it.

---

