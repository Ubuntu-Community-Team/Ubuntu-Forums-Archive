---
title: "Either a networked drive issue, or a bunch of other issues :)"
date: 2009-10-27
forum: General Help
---

### Post by schwim on 2009-10-27
Hi there everyone,

I've got two networked drives that are win shares, one with my audio and one with my work files.  I mount them via fstab, sometimes manually and sometimes automatically at bootup, depending on whether Ubuntu opts to start the network before or after trying to mount the network drives.  Here's my mount strings:

```

//192.168.1.199/Websites /mnt/websites cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0
//192.168.1.199/Audio /mnt/audio cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0

```

I have no issue playing the music, saving files to the folders, etc. However, in Gedit, if I save a new file, it does fine.  When I try to save over an existing file though, it states that it can not be done.  Please note that it does actually save the file though.  If I do the same in Scite, the file saves without any error.

My second issue: I needed to alter some id3 tags on some mp3's to try to get rid of the rhythmbox errors nagging about non-existent addons.  I opened easytag and browsed to tried to choose my music folder, but it didn't show any folder hierarchy and wouldn't let me drill through to subfolders.  I tried manually entering the path and my music shows there, but it is greyed out and I'm not allowed to select it.

It seems as if some applications find my files to be readonly, when in fact they aren't.  I'm just not sure if the problem is my mounting method or if it's some other issues I'm experiencing.  Almost all applications(FTP, other text editors, OO.o) work in those directories just fine, I've only experienced issues so far with Gedit and easytag.

Any thoughts would be greatly appreciated.

thanks,
json

---

### Post by Giblet5 on 2009-10-27
First issue is that the remote share (samba?) is allowing you to create new files, but setting the permissions on those new files so that you do not have permission to overwrite or delete them.

With samba, that's a configuration issue.

The second problem is a permissions problem as well.

Permissions = ownership and mode

Let's say that there is a file, /home/shares/myfile.txt:

```
ls -l /home/shares/myfile.txt
-rw-r--r-- 1 samba samba 2666 2009-10-27 myfile.txt
```

User "guest" may have been allowed to create that file via samba, but he doesn't own it. You can read it, but only user samba can write to it now. That's a config issue.

Look in the config for a line like ```
create mode = 0644
```

That is what you need to change. Making it 0666 will allow anyone to overwrite it.

---

### Post by schwim on 2009-10-27
Thanks for the response, giblet.

My confusion arises from the fact that I can modify and overwrite files.  As stated, although Gedit balks at me when overwriting a file, it does in fact overwrite it.  In fact, it notifies me that the file has been altered and refreshes the updated file :)

Second issue also is dependent on application.  Audacity for instance can alter the files, easytag just won't access them.

thanks,
json

---

### Post by Giblet5 on 2009-10-27
> **schwim said:**
> Thanks for the response, giblet.

My confusion arises from the fact that I can modify and overwrite files.  As stated, although Gedit balks at me when overwriting a file, it does in fact overwrite it.  In fact, it notifies me that the file has been altered and refreshes the updated file :)

Second issue also is dependent on application.  Audacity for instance can alter the files, easytag just won't access them.

thanks,
json

Weird! And just in time for Halloween...

This is why I use NFS for the same purposes that you're using shares.

NFS works with unix permissions. Windows shares don't.

Samba to provide shares.
NFS to provide native linux shared access.

Everybody smiles.

---

### Post by schwim on 2009-10-27
Hi there Giblet,

I'm not familiar with using NFS to retrieve shares.  Is there a tutorial or link you could share that would explain it and maybe provide a representative setup?

thanks,
json

---

