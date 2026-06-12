---
title: "Evolution fails to &quot;Print to File&quot;"
date: 2010-02-24
forum: General Help
---

### Post by sparky2 on 2010-02-24
Up until recently in Evolution email I was able to "Print to File" any email. Now it fails to produce any file with no error message. However if I use "print preview" then print it reports an error that is has no permission to access the directory.

This happens for any directory, including those whcih it used to print to.

The only recent change, apart from accepting recommended updates, is that I removed my gnome keyring password so I didn't have to type a password whenever Evolution started. But after I added a password back in, the problem still occurs.

---

### Post by darolu on 2010-02-24
Check permissions of the target directory; saving to somewhere in your personal folder is usually a good idea, check if you didn't accidentally changed the default directory.

If you want to use another folder out of your personal one, you may need to change this directory's permissions.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by sparky2 on 2010-02-24
hmmmmm... I doubt it's permissions. the directories I've tried (several) were all writeable from Evolution in the past using Print to File. Also I haven't set any permissions (I'm the only user) and I can write to the directories outside Evolution OK

---

