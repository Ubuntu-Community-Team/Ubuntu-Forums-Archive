---
title: "restore ${HOME} howto"
date: 2010-09-02
forum: General Help
---

### Post by tlroche on 2010-09-02
A few questions about the non-backup-tool-related parts of a restore (on a lucid box, if that makes a difference):

I have hostname=FOO running lucid (64-bit, if that makes a difference), on which I am user=foo. I regularly back FOO up to an external HD using `duplicity`. FOO needs to return home for service, which will take at least a week. My GF has a hostname=BAR, also running lucid (but 32-bit, if that makes a difference), on which I am user=bar. She'll let me use BAR while FOO is elsewhere, so I want to transfer FOO:/home/foo to BAR:/home/bar. I'm guessing the way to do this is

0 Ensure ubuntu and duplicity are uptodate on both FOO and BAR.

1 Backup FOO:/home/foo with

```
foo@FOO:~$ duplicity ${HOME} file:///media/HD/FOO/home/foo
```

2 Restore with

```
bar@BAR:~$ sudo duplicity file:///media/HD/FOO/home/foo ${HOME}-restore
```

 (duplicity won't restore to an existing directory, which seems safe. I sudo to create the restore dir on /home, which has a lotta free space.)

3 Replace BAR:/home/bar with BAR:/home/bar-restore. Since BAR has sufficient space, I'm planning to do

```
bar@BAR:~$ sudo -i
root@BAR:/root# mv /home/bar /home/bar-backup
root@BAR:/root# mv /home/bar-restore /home/bar
root@BAR:/root# exit

```

I'm wondering,

a Will step 3 work as intended, or should I do something different? Notably, will the root shell exit to user=bar appropriately after having $HOME forklifted out from under it? Should I instead do this from a virtual console, from a recovery shell, or anything else besides a root shell in an xterm? Instead of exiting, should I restart (e.g. `shutdown -r now`)?

b Is there a better way to do step 2? `sudo` was required to avoid duplicity errors: latter wants to create the folder given with $2, and folder creation only worked as su. The only problem I noted was that, while my files restored with appropriate metadata (e.g. rights, timestamp), duplicity created symlinks owned by root.

c Is there a better tool for backup/restore to/from local disk? Pointers to docs are appreciated.

TIA, Tom Roche [Tom_Roche@pobox.com]

---

