---
title: "automount problem - ntfs-3g, FUSE, setuid...?"
date: 2012-02-06
forum: General Help
---

### Post by ohnonot on 2012-02-06
hello,

i'm trying to get my external hd mounted on boot. it's ntfs.
i actually already succeeded with the help of this article:

[Fstab - Examples]("https://help.ubuntu.com/community/Fstab#Examples") [https://help.ubuntu.com/community/Fstab#Examples](https://help.ubuntu.com/community/Fstab#Examples)

- i used the example fstab entry and it worked fine!

now while messing around with mobile broadband dongle and wvdial (which is now working nicely)
i changed some user privileges, and had this situation afterwards:

the external hd mounts, but when i start browsing it and especially after adding a shortcut to the sidepane, i suddenly get this error:


Failed to mount xxxx:

Error mounting: mount exited with exit code 1: helper failed with:
Mount is denied because setuid and setgid root ntfs-3g is insecure with the
external FUSE library. Either remove the setuid/setgid bit from the binary
or rebuild NTFS-3G with integrated FUSE support and make it setuid root.
Please see more information at
[http://tuxera.com/community/ntfs-3g-faq/#unprivileged](http://tuxera.com/community/ntfs-3g-faq/#unprivileged)

...after which i can't access the drive anymore...

thinking it has sth to do with those user privileges i start changing them back, rebooting, changing back and forth and rebooting mayb 5 times, but no change.

so i check out the link in the error message, where it says:

... The root user can make an ntfs-3g binary setuid-root as shown below
chown root $(which ntfs-3g)
chmod 4755 $(which ntfs-3g) In such case the driver will also be able...

and i happpily went and did this only to find *afterwards* that one is "strongly discouraged" to do that. 
:(

anyway, after rebooting, there's no change to the problem, but my mouse pointer has changed.

so first of all i want to undo the setuid-thing i did!
can someone help with that?

secondly, i want that automount at startup to work again.
can someone help with that?

also i'd like to understand what actually happened. or is happening.

any help appreciated. thanks.

ps: my first hd first partition is windows/ntfs, too, but that one doesn't seem to be affected.

---

### Post by Linux Dutchman on 2012-02-06
Try this wiki: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
 
You know that you need to add the line(s) in the file fstab? Editing the fstab file:
- open a terminal
- type: sudo gedit /etc/fstab
- edit the file and save the file

---

### Post by ohnonot on 2012-02-06
> **Linux Dutchman said:**
> Try this wiki: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
 
You know that you need to add the line(s) in the file fstab? Editing the fstab file:
- open a terminal
- type: sudo gedit /etc/fstab
- edit the file and save the file

did you actually read my post?

bump.

---

### Post by ohnonot on 2012-02-06
the weirdness continues.
tonight i was working on my computer, watching a movie, everything worked fine, then, while populating gmusicbrowsers library, it started again. seems like something (?) is unmounting the drive while i'm working with it.

anyway my computer starts to behave weirdly in other ways, too, especially during boot. i can't really describe it, but the bootup process looks different almost everytime, also the mouse pointer changes.
it feels very unpredictible, almost like having a virus under windows
;)

i guess this is not about mounting external drives, but about the setuid-root chown thing i did.

did i wreck my installation?

any help, please!

---

### Post by oldfred on 2012-02-06
Is your external separately powered or thru USB port? 

Some have reported issues where internal power was not enough and caused weird things to happen.

---

### Post by ohnonot on 2012-02-07
it's separately powered.

---

