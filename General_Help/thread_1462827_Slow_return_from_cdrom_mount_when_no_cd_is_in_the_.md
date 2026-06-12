---
title: "Slow return from cdrom mount when no cd is in the drive"
date: 2010-04-26
forum: General Help
---

### Post by TMcC on 2010-04-26
I have a script that tries to mount a CDROM, by executing the following command:

```
mount -o ro,noauto,owner -t iso9660 /dev/cdrom /media/cdrom
```

Under 10.04 Lucid Lynx RC with no CDROM in the drive, this takes 15 seconds to return.

Under Fedora 10, return is almost instantaneous.

Doing an strace under Ubuntu shows this section repeated numerous times:

```
stat64("/sbin/mount.iso9660", 0xbfe08638) = -1 ENOENT (No such file or directory)
mount("/dev/sr0", "/media/cdrom", "iso9660", MS_MGC_VAL|MS_RDONLY|MS_NOSUID|MS_NODEV, NULL) = -1 ENOMEDIUM (No medium found)
rt_sigprocmask(SIG_UNBLOCK, ~[TRAP SEGV RTMIN RT_1], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGCHLD, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
nanosleep({3, 0}, 0xbfe08774)           = 0
rt_sigprocmask(SIG_BLOCK, ~[TRAP SEGV RTMIN RT_1], NULL, 8) = 0
``` 

The same strace under Fedora 10 shows only one attempt.

Anyone know how to stop Ubuntu from trying so hard? ;)

Thanks

---

### Post by TMcC on 2010-04-26
Would be useful if somebody could try this on their Ubuntu flavour, to let me know if it's the standard behaviour?

Thanks

---

### Post by TMcC on 2010-04-26
Hmm, this section from util-linux-ng 2.17.2, mount.c:

```
     case ENOMEDIUM:
      if (retries < CRDOM_NOMEDIUM_RETRIES) {
            if (verbose)
                  printf(_("mount: no medium found on %s ...trying again\n"),
                         spec);
              sleep(3);
            ++retries;
              goto mount_retry;
      }
      error(_("mount: no medium found on %s"), spec);
      break;
```

Is a pain in the proverbial. CRDOM_NOMEDIUM_RETRIES is set in blkdev.h to 5, rather than being a runtime config parameter. 

Toys. Pram. Floor.

---

### Post by TMcC on 2010-04-27
Fix commited by Karel Zak ([http://git.kernel.org/?p=utils/util-linux-ng/util-linux-ng.git;a=commit;h=ca55a451cdfa48f7640cd2f122aa25dedbd4edf5](http://git.kernel.org/?p=utils/util-linux-ng/util-linux-ng.git;a=commit;h=ca55a451cdfa48f7640cd2f122aa25dedbd4edf5))

---

