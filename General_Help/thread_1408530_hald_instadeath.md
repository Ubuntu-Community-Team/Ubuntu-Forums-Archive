---
title: "hald instadeath"
date: 2010-02-16
forum: General Help
---

### Post by urgrue on 2010-02-16
I'm running the latest xubuntu with all patches.
hald has stopped working. But it works fine when started manually. Yet there is no difference in the command line and parameters used. 
When started with "start hal" or the init script, it dies on the fdi cache regeneration:

mmap_cache.c:126: Regenerating fdi cache..
Feb 16 19:35:58 myhost hald[11096]: 19:35:58.614 [E] hald_runner.c:882: Error running 'hald-generate-fdi-cache': org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Feb 16 19:35:58 myhost hald[11096]: 19:35:58.614 [I] mmap_cache.c:104: In regen_cache_cb exit_type=2, return_code=0
Feb 16 19:35:58 myhost hald[11096]: 19:35:58.614 [E] mmap_cache.c:153: fdi cache regeneration failed!
Feb 16 19:35:58 myhost hald[11096]: 19:35:58.614 [I] mmap_cache.c:156: fdi cache generation done
Feb 16 19:35:58 myhost hald[11096]: 19:35:58.614 [I] mmap_cache.c:278: cache mtime is 1264790743

This results in all hald processes stopping, and it endlessly tries to respawn itself. My ps looks like this:
11568 ?        Ss     0:00 hald --daemon=yes
11569 ?        Ss     0:00  \_ hald --daemon=yes
11570 ?        S      0:00      \_ hald-runner
11571 ?        R      0:00          \_ /usr/lib/hal/hald-generate-fdi-cache

And every second they all die and respawn.

When started manually, all is well:
11587 ?        Ss     0:00 hald --daemon=yes
11588 ?        S      0:00  \_ hald-runner
11629 ?        S      0:00      \_ hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
11640 ?        S      0:00      \_ hald-addon-input: Listening on /dev/input/event0 /dev/input/event1
11641 ?        S      0:00      \_ hald-addon-storage: polling /dev/sr0 (every 2 sec)

The difference is when started by me, instead of doing the fdi regeneration bit the log shows:
Feb 16 19:47:12 myhost hald[11208]: 19:47:12.069 [I] mmap_cache.c:278: cache mtime is 1264790743
Feb 16 19:47:12 myhost hald[11208]: 19:47:12.069 [I] mmap_cache.c:83: preprobe: offset=00000014, size=538764
Feb 16 19:47:12 myhost hald[11208]: 19:47:12.069 [I] mmap_cache.c:85: information: offset=000838a0, size=449088
Feb 16 19:47:12 myhost hald[11208]: 19:47:12.069 [I] mmap_cache.c:87: policy: offset=000f12e0, size=44672

Anyone have any suggestions?

---

