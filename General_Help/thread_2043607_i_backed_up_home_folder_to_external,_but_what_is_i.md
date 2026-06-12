---
title: "i backed up home folder to external, but what is in there?"
date: 2012-08-16
forum: General Help
---

### Post by LLCoolJeff on 2012-08-16
I backed up my home folder to an external HD using the method here: [http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup) 

in case you didn't go to the link the code was:

```
rsync -av sourcedir destdir
```
in my case:
```
rsync -av /home/<computer> /media/<usbdrive>/backup
```

I thought I knew exaclty what I was backing up, my home folder right? but when the terminal was running I was seeing all sorts of things I didn't know were in the home folder like firefox caches for example.. so my question is what exactly did this backup?

and did it get all my bookmarks and other things in firefox as well? what else may be in the home folder that I do not know about?

---

### Post by unevenflow on 2012-08-16
Open usb and hit Ctrl+H to unhide hidden folders and check if there is a .mozilla folder if there is you're ok

---

### Post by LLCoolJeff on 2012-08-16
> **unevenflow said:**
> Open usb and hit Ctrl+H to unhide hidden folders and check if there is a .mozilla folder if there is you're ok

ah yes, forgot about those hidden files

thank you

---

### Post by oldfred on 2012-08-16
I was up until recently doing the exact same thing with rsync. But I noticed it was backing up cache and other temporary type things. So I tried to remember to houseclean cache first. Then I found these posts:

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Files to include or exclude from full system backup. Post #7
[http://ubuntuforums.org/showthread.php?t=1903085](http://ubuntuforums.org/showthread.php?t=1903085)

Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
/home/*/.cache
/home/*/.dbus
/home/*/.dropbox
/home/*/.gvfs
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**
/home/*/.qt
/home/*/.thumbnails
/home/*/Examples
/home/.encryptfs
/home/lost+found

If your /home is encrypted you may want to backup .encryptfs

---

### Post by newb85 on 2012-08-24
> **oldfred said:**
> If your /home is encrypted you may want to backup .encryptfs

...and if your /home is not encrypted, .encryptfs shouldn't exist.  So, why even list it as an exclusion?

---

