---
title: "Problems with permissions"
date: 2010-01-17
forum: General Help
---

### Post by lonewolff on 2010-01-17
Hi guys,

I am a Linux newbie (trying to break away from Windows) and I have just installed Ubuntu 9.10 today and so far so good!

I have made a RAID0 volume which I can now mount. I have added an entry in fstab and can auto mount my new volume (md0).

But, I can't write to the volume unless done through 'sudo'.

Here is my fstab file

> #<file system>                    <mount point>    <type>        <options>            <dump>    <pass>
proc                        /proc        proc        defaults            0    0

# / was on /dev/sda1 during installation
UUID=60695a84-eac6-42f6-b17d-1f361044189a    /        ext3        relatime,errors=remount-ro    0    1

# swap was on /dev/sda5 during installation
UUID=caba50d0-4b49-4c50-bbfe-b67f14db01fd    none        swap        sw                0    0

# CDROM (Not installed)
#/dev/scd0                    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8        0       0

# RAID0 volume
UUID=16890633-6f4d-4deb-99a6-efe13e6db246    /home/jason/Raid    ext2    rw,user,auto,sync        0    0I have tried doing various things here and also with chown. But, being a newbie, I don't really know what I am doing.

Could anyone shed some light on how I can make this volume read/write for any user?

Thanks in advance :)

---

### Post by jamesisin on 2010-01-17
Take a look at this post I wrote on adding additional drives to Ubuntu:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

The section on changing ownership will be of special interest to you.  You'll have to modify the arguments for your RAID (md instead of sd, for instance), but it should be pretty strait forward.

Let me know if you have questions (either here or there).

---

### Post by lonewolff on 2010-01-17
Excellent advice 'chmod 777 /.../... did the job!

I have bookmarked your article for reading in entirety.

---

### Post by jamesisin on 2010-01-17
Great.  Glad to be of service.

Remember to mark the thread as SOLVED under Thread Tools above.

---

### Post by lonewolff on 2010-01-17
Sure thing.

Thanks again. I am loving Ubuntu so far!

---

### Post by RobLikesBrunch on 2010-01-17
If you ever feel the inclination to use a GUI for this instead of a CLI, you can also try the package pysdm in Synaptic (but I think editing fstab is better, as you have done).

---

### Post by Paulgirardin on 2010-01-23
Thanks for the tips they helped me too.:)

---

