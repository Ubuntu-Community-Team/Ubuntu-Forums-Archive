---
title: "Change the default location of the thumbnails cache?"
date: 2012-07-21
forum: General Help
---

### Post by Stonecold1995 on 2012-07-21
I have my /tmp directory mounted as tmpfs, so it runs in RAM.  I have 16GB of RAM, which is plenty, so I thought, why don't I move the location of the thumbnails cache to /tmp to speed it up.  I tried moving .thumbnails to /tmp and creating a symlink to it in my home directory, but the problem with that is that /tmp is cleared each boot.  When I reboot and the symlink points to a deleted directory, the symlink is deleted and replaced with a real directory in home (which I don't want because /home is on a hard drive, not a RAM disk).  To try and fix this, I created a tiny script that I'd set to run at start (not boot or pre-KDE startup, but KDE startup).  Here is the script I wrote:
```
#!/bin/bash

# this script moves the location of the thumbnail cache to /tmp, which is mounted as tmpfs
rm -rf /tmp/thumbnails .thumbnails
mkdir -p /tmp/thumbnails/normal /tmp/thumbnails/large
ln -sn /tmp/thumbnails .thumbnails
exit 0

```

But for some reason, this script only half works!  "rm -rf /tmp/thumbnails .thumbnails" deletes /tmp/thumbnails if it exists, but won't touch .thumbnails.  Because .thumbnails isn't deleted, the symbolic link could not be created, and the script won't work.  To see what the problem was, I tried creating a script with only "rm -rf .thumbnails" as the contents of the script.  It didn't work.  So apparently I can't delete .thumbnails upon KDE start, even though the other commands work...

If I manually run "./tmpfs_thumbs.sh" (the name of my script), it works, so why won't it work for me at startup!?  It's an extremely simple script (and I'm not too new to bash), so I don't know what I could have possibly done wrong...

If anyone knows how to get this script to work or (even better) change the default location of .thumbnails, please tell me.

---

### Post by Zorael on 2012-07-24
That script requires the working path to be your home directory. Have you tried using an absolute path for the .thumbnails directory?

```
#!/bin/sh
# this script moves the location of the thumbnail cache to /tmp, which is mounted as tmpfs

rm -rf /tmp/thumbnails ~/.thumbnails
mkdir -p /tmp/thumbnails/{normal,large}
ln -sn /tmp/thumbnails ~/.thumbnails

exit 0
```

You can also use the **-f** flag with ln to have it overwrite whatever is there.

Semi-related, if you ever plan to use this as a pre-startup script (such as if placing it as a **.sh** file in **~/.kde/env**), never have it exit. Such files are sourced, not run, so exiting would stop the whole login sequence and likely return you to the greeter.

---

### Post by Stonecold1995 on 2012-07-24
> **Zorael said:**
> That script requires the working path to be your home directory. Have you tried using an absolute path for the .thumbnails directory?

```
#!/bin/sh
# this script moves the location of the thumbnail cache to /tmp, which is mounted as tmpfs

rm -rf /tmp/thumbnails ~/.thumbnails
mkdir -p /tmp/thumbnails/{normal,large}
ln -sn /tmp/thumbnails ~/.thumbnails

exit 0
```

You can also use the **-f** flag with ln to have it overwrite whatever is there.

Semi-related, if you ever plan to use this as a pre-startup script (such as if placing it as a **.sh** file in **~/.kde/env**), never have it exit. Such files are sourced, not run, so exiting would stop the whole login sequence and likely return you to the greeter.

Thank you very much!  I removed the "exit 0" and put it in ~/kde/env like you said and it's working perfectly!  Setting it as a startup script still doesn't work but setting it as a pre-KDE startup script worked perfectly!

Also, I tried using -f with ln and in doesn't *replace* .thumbnails, it places the symlink *in* it.  But anyways, it's working perfectly now.

---

