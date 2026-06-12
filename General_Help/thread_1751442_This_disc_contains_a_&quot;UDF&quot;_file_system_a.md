---
title: "This disc contains a &quot;UDF&quot; file system and requires an operating system that supports"
date: 2011-05-06
forum: General Help
---

### Post by sefs on 2011-05-06
I have made an iso that I want to add some files too.  I have tried ISO Master.  But when I open it with ISO Master, there is just one txt file in the ISO that says

```

This disc contains a "UDF" file system and requires an operating system
that supports the ISO-13346 "UDF" file system specification.

```

How am I able to open this iso in ubuntu and add some files to it and the close it back so that I have the iso with the added files.

Thanks.

---

### Post by sefs on 2011-05-07
Ok I got it done.

What I did was to download MagicISO for Windows (May work in wine? I did not try).  And that was able to recognize the ISO and was able to add and re-save the ISO in MagicISO.

---

### Post by Eric B on 2011-07-08
This is so not what I would call solved, yet this windows nonsense is at the top of my google search results.

---

### Post by srs5694 on 2011-07-08
Linux supports UDF just fine, but you may need to explicitly specify it as a UDF. You can do this at a command line prompt like this:

```

sudo mount -t udf /dev/dvd /mnt

```

You can add more options, change the mount point, etc.; see the mount man page for details. If the disc was created to enable read/write support, Linux's UDF driver might enable writing to the disc. If not, you could copy the files to a temporary disk directory, modify them, and burn a new disc with growisofs or your favorite GUI CD/DVD utility.

I'm not sure how you'd do this with a GUI tool like Nautilus. It might recognize and favor UDF over ISO-9660 or it might not; I've never checked to see.

---

### Post by sefs on 2011-07-08
> **Eric B said:**
> This is so not what I would call solved, yet this windows nonsense is at the top of my google search results.

LOL really?  Well we better get a proper solution going here....

From what I gather by default the ubuntu fstab has for it's cd/dvd mount line

```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

if you change the udf,iso9660 bit to auto, like below, then ubuntu should automount udf...

```

/dev/scd0       /media/cdrom0   auto user,noauto,exec,utf8 0       0

```

---

