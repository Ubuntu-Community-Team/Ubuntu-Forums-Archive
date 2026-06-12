---
title: "Have to log out of a virtual terminal twice"
date: 2010-02-19
forum: General Help
---

### Post by narnie on 2010-02-19
Strange problem.

I have to log out of a virtual terminal by typing exit, then exit again as in:

```
woodnt@toshiba-laptop ~ $ exit
logout
woodnt@toshiba-laptop ~ $ exit
logout

```

I DON'T have to do this when I'm using gnome-terminal or xterm. It just exits.

I do notice that if I have done this in xterm for example:

```
woodnt@toshiba-laptop ~ $ bash
woodnt@toshiba-laptop ~ $ bash
woodnt@toshiba-laptop ~ $ exit
exit
woodnt@toshiba-laptop ~ $ exit
exit
woodnt@toshiba-laptop ~ $
``` 

It lists exit instead of logout after typing exit.

Now lest one thinks it is that I have typed bash in the vtty, that is not the case. Also, echoing $SHLVL gives:

```
woodnt@toshiba-laptop ~ $ echo $SHLVL 
1
```

so I'm not in subshells.

I have mv ~/.profile ~/.profile.bak and mv ~/.bashrc ~/.bashrc.bak to make sure that it is nothing that I have done.

Other users can log in a vtty and completely exit with one command.

I'm not sure how the vtty's work nor how to begin to toubleshoot this further.

Any ideas?

With thanks,
Narnie

---

### Post by narnie on 2010-02-20
btw, I have also renamed my .bash_logout script as well so it isn't in that. However, one wouldn't think it would be there anyway as I'd never be able to log out.

It is something that is different about a vtty (via getty) vs windowed terminal.

A check of getty process shows:

```
woodnt@toshiba-laptop ~ $ ps auxf|grep -v grep|grep tty
root      1245  8.1  3.1 243252 126236 tty7    Ss+  Feb19  11:38      \_ /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-QfOGCe/database -nolisten tcp vt7
root      1395  0.0  0.0   5988   492 tty4     Ss+  Feb19   0:00 /sbin/getty -8 38400 tty4
root      1411  0.0  0.0   5988   492 tty5     Ss+  Feb19   0:00 /sbin/getty -8 38400 tty5
root      1441  0.0  0.0   5988   492 tty2     Ss+  Feb19   0:00 /sbin/getty -8 38400 tty2
root      1442  0.0  0.0   5988   492 tty3     Ss+  Feb19   0:00 /sbin/getty -8 38400 tty3
root      1444  0.0  0.0   5988   492 tty6     Ss+  Feb19   0:00 /sbin/getty -8 38400 tty6
root      3968  0.0  0.0   5988   492 tty1     Ss+  Feb19   0:00 /sbin/getty -8 38400 tty1

```

---

### Post by narnie on 2010-02-24
I have tracked this problem down to a ecrypts issue.

I have a the Private ecrypts directory set up as usual except that I don't like it's automounting behaviour.

The original listing of the dir looks like:

```
woodnt@toshiba-laptop ~ $ ls .ecryptfs/
auto-mount   Private.mnt  sig-cache.txt.bak
auto-umount  Private.sig  wrapped-passphrase
```

I have renamed auto-mount to this, which prevents the auto-mounting of the ecrypts folder, which I manually mount if needed.

```
woodnt@toshiba-laptop ~ $ ls .ecryptfs/
NO_auto-mount   Private.mnt  sig-cache.txt.bak
auto-umount  Private.sig  wrapped-passphrase
```

If have have auto-mount as the original name, then I don't have to log out twice from a vtty. When I have auto-mount renamed so that ecrypt doesn't see it, I have to log out of vtty twice. This is very highly reproducible in that it occurs EVERY time. Also of note, it doesn't really matter if the private dir is "mounted" or not, which caused me to miss this. It is just renaming that one file that breaks it like this.

Anyone have any idea as to a fix?

I'll be posting a bug report in view of this as well.

Thanks,
Narnie

---

### Post by narnie on 2010-02-24
Here is the bug report link:

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/526868]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/526868")

---

