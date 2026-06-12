---
title: "su -p -c not preserving env"
date: 2011-05-02
forum: General Help
---

### Post by tyce on 2011-05-02
Since going to 11.04 last week, I have noticed that $PATH in env no longer gets preserved when running commands as another user on the system.  Here's an example of what I'm talking about:

root@malakim:~# env |grep PATH | grep -v LD
PATH=/usr/local/perltests/bin:/usr/test/torque/bin:/usr/test/torque/sbin:/usr/test/moab/bin:/usr/test/moab/sbin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

root@malakim:~# su -p -c "env |grep PATH | grep -v LD" tuser1
PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games

I have verified this on a few different machines at my office.  Any help with where I might look as to what changed from 10.10 to 11.04 would be greatly appreciated.

---

### Post by lloyd_b on 2011-05-02
> **tyce said:**
> Since going to 11.04 last week, I have noticed that $PATH in env no longer gets preserved when running commands as another user on the system.  Here's an example of what I'm talking about:

root@malakim:~# env |grep PATH | grep -v LD
PATH=/usr/local/perltests/bin:/usr/test/torque/bin:/usr/test/torque/sbin:/usr/test/moab/bin:/usr/test/moab/sbin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

root@malakim:~# su -p -c "env |grep PATH | grep -v LD" tuser1
PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games

I have verified this on a few different machines at my office.  Any help with where I might look as to what changed from 10.10 to 11.04 would be greatly appreciated.

First off, it should *never* have worked the way you are expecting.  From the su man page:```
-m, -p, --preserve-environment
           Preserve the current environment, except for:

           $PATH
               reset according to the /etc/login.defs options ENV_PATH or
               ENV_SUPATH (see below);

           $IFS
               reset to &#8220;<space><tab><newline>&#8221;, if it was set.

           If the target user has a restricted shell, this option has no
           effect (unless su is called by root).

           Note that the default behavior for the environment is the
           following:

               The $HOME, $SHELL, $USER, $LOGNAME, $PATH, and $IFS environment
               variables are reset.

               If --login is not used, the environment is copied, except for
               the variables above.

               If --login is used, the $TERM, $COLORTERM, $DISPLAY, and
               $XAUTHORITY environment variables are copied if they were set.

               Other environment might be set by PAM modules.
```For security reasons (such as preventing someone from tricking a user into adding a "bad" directory into a PATH and then passing that directory along if the user su's to root), the PATH is supposed to be arbitrarily reset to a specified value.  Looks like someone noticed it not resetting the PATH and fixed it.

Take a look at using the 'sudo' command instead - it *does* have an option to preserve all environment variables (though you'll have to configure it to allow the -E option via the sudoers file).  Alternately, you could use the "-l" option for 'su' to specify a login shell, which will include sourcing the user's ~/.bashrc, thus giving you the same PATH that the user would normally have.

Lloyd B.

---

