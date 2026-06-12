---
title: "Copying /home to USB drive, is it enough to do &quot;cp -ar&quot;?"
date: 2010-11-21
forum: General Help
---

### Post by pgagy on 2010-11-21
I want to just copy my /home dir to a USB drive for backup purposes.  Is it enough to just do cp -ar, which should preserve all permissions and do it recursively?  Or should I throw some other options in there?  Will all hidden files get copied too?  I currently have a no GUI install running.

Thanks!

---

### Post by HermanAB on 2010-11-21
Howdy,

I would either make a tar ball or use rsync.  Rsync is especially good the second time around, since then it will only copy the parts of files that changed, which will be fast.

---

### Post by pgagy on 2010-11-21
I'd love to do tar, but I have over 100gb of data, and the USB drive is Fat32.  So I would need to split it..and for some reason that does not work. I get a permission denied.  I can tar no problem into one file, but when I do |split -d -b 3900m I get errors.  I tried all kinds of stuff, and no go. I sudo I do everything.  All fails.  So I figured I'll just copy instead of tar.  Plus it's faster to just copy.  Unless you know why I'm getting permission denied with splitting tar files, then I could split.  I followed the how-to on ubuntu forums...

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

but it was no go.  

> **HermanAB said:**
> Howdy,

I would either make a tar ball or use rsync.  Rsync is especially good the second time around, since then it will only copy the parts of files that changed, which will be fast.

---

### Post by Artemis3 on 2010-11-21
You could use 7z with the volume option (package name is p7zip).

---

### Post by skillet-thief on 2010-11-21
> I'd love to do tar, but I have over 100gb

You don't need to go to a file, you can pipe the output from tar to another instance of tar. You should check the docs, but it would look something like this:

```
cd /target/dir && tar cz /src/dir | tar xz
``` 

Warning pseudocode!!!! I don't have time to look up the specifics right now, but I know this can be done.  On the other hand, rsync might be a better choice.

---

