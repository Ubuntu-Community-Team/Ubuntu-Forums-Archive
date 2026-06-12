---
title: "Don not ask to me any password to mount the win7 part"
date: 2010-10-31
forum: General Help
---

### Post by Vegaxus on 2010-10-31
Hi again.

I have found a security bug in Ubuntu 10.10. Despite in the usr/share/polkit-1/actions/org.freedesktop.udisks.policy file show me "auth_admin_keep" in the action: "org.freedesktop.udisks.filesystem-mount-system-internal", Ubuntu 10.10 never ask me for the root password to mount the windows partition or when i made any change inner that partition (for example, remove a file of windows folder or create a new file in system32 folder, etc.)

I feel a bit unsafe about this, i could make a fatal action on that windows partition without ubuntu ask me for the password before. I would like to know how i may to set the root password again. 

I do not even know if others users of ubuntu 10.10 have the same problem or not, but what i know my username is not added in the /etc/sudoers file.

regards
********************* 

Ok, it does not matter. 

I just edit the "/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla" file and change the first text in the last line:
"ResultActive=yes" by "ResultActive=auth_admin_keep", now ask me for the root password.

---

### Post by Mark Phelps on 2010-10-31
I have two responses to your claim of this being a "problem" ...

First, Ubuntu defaults to mounting other OSs granting you full permissions.  With the freedom to do whatever you want comes the risk of causing major damage.  This is the price of "freedom" -- as Linux afficionados would have it.  So, I think others would not call this a "problem" as much as they would call this a "feature".

Second, I have found through personal experience, that is it a BAD idea to mount a Vista or Win7 OS partition read/write and then make changes to it inside Ubuntu.  I have encountered file system corruption more than once doing that -- to the degree, that I now have a desktop app that allows me to mount the partition only when I need it, and then umount it as soon as I am done.

Others will disagree, saying they have mounted hundreds of times without problems -- but that was true for me as well -- until the first time I had a filesystem corruption and had to fix it.

---

### Post by Rubi1200 on 2010-10-31
Just to add to what Mark Phelps just said:

physical access is equivalent to root access. This means that since you are the one with an account that has administrative privileges you are able to mount the partitions of other operating systems without being asked for a password. This has been the default action since 10.04 and is not a bug or a security flaw (though there may be those who disagree).

Of course, as you discovered, you can change that behavior to suit your own needs.

---

### Post by Vegaxus on 2010-11-17
Sure, but this solution is not fully acceptable one. Not only i had to use root privileges when i mounted another partition but if i wanted to mount a CD/DVD disk or USB Pendrive as well.

So i had to manage myself the way to improve that solution and now it is completely acceptable for me. I have changed the "var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla" file with the follow code to get the behavior what i was looking for:

```
[Mounting, checking, etc. of internal drives (CD/DVD, USB Pendrives, etc.)]
Identity=unix-group:admin
Action=org.freedesktop.udisks.filesystem-*
ResultActive=yes

[Mounting, checking, etc. of internal drives (SATA Hard-disk)]
Identity=unix-group:admin
Action=org.freedesktop.udisks.drive-ata-smart*
ResultActive=auth_admin_keep

...#rest the file code#...
```

So i am going to close this thread as a solved one.

---

