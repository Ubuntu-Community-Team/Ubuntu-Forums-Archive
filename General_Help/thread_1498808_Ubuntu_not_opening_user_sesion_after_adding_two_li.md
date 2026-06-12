---
title: "Ubuntu not opening user sesion after adding two lines to .profile"
date: 2010-06-01
forum: General Help
---

### Post by dc740 on 2010-06-01
I can't seem to find the problem cause I don't know where do the logs go to. the thing is...

If I add these lines to ".profile":
```

export MAVEN_OPTS="-Xmx2048m -Xms128m -XX:+UseConcMarkSweepGC -XX:+UseParNewGC"
export ANT_OPTS=$MAVEN_OPTS

```

Ubuntu won't open an Xsession for that user.

It shows the log in screen, I enter the password, the log in screen disappears, (black screen here), and the log in screen is shown again.

There are no errors in the xserver log. cause it's not an xserver error.

If I comment those lines, then Ubuntu boots as always

Any Hints?

This is my full .profile:

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi


JDK_HOME="/home/jivuntu/svn/repos/jive_sbs_dm/trunk/dist/bin/java/Linux/x86_64/current"
export JDK_HOME

INTELLIJ='/home/jivuntu/Programs/idea-IU-93.94'
PATH="$INTELLIJ/bin:$PATH"
export SVN_EDITOR=vi

export MAVEN_OPTS="-Xmx2048m -Xms128m -XX:+UseConcMarkSweepGC -XX:+UseParNewGC"
export ANT_OPTS=$MAVEN_OPTS

```


I'm using Ubuntu 9.04 x64

---

### Post by rnerwein on 2010-06-01
hi
may be no solution but a question ! 
are you trying to start your java stuff in the ~/.bashrc and your box has not enough memory ??
what does the command "ulimit -a" tells you ( typed in a terminal -- for that user !!!! )
ciao
oh you can't look for that user because you can't login.
have a look at /etc/security/limits.conf if there is an entry for that user ( or system wide ).

---

### Post by dc740 on 2010-06-01
this is the output:
```
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

BTW: I can login now. I commented the two lines. I'm not a friend of the X server. so I'm pretty used to the command line.

no, there isn't anything "java related" in the .profile nor in the .bashrc

I just added those two lines to get my compilation environment a little bit more user friendly.

but it's weird. it should boot without problems

---

### Post by drmikeh on 2012-05-11
I just encountered this problem with Ubuntu 12.04 running under VMWare Workstation running under Windows 7. I could login as guest but not as my primary user. My workaround was to put the MAVEN_OPTS setting in .bashrc instead of in .profile.

---

### Post by oldos2er on 2012-05-11
Old thread closed.

---

