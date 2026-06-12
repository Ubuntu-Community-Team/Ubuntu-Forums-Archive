---
title: "Environment variables screwed up in Ubuntu"
date: 2004-10-24
forum: General Help
---

### Post by salmankhilji on 2004-10-24
I do not know if this is GNOME 2.8 related or ubuntu related.  The "standard" way to setting system wide environment variables is to edit /etc/profile (or /etc/profile.local for SuSE).  It is highly desired to specify environment variables in /etc/profile as opposed to ~/.bashrc because the latter is in effect only if you have opened a terminal.  If you specify an environment variable in the latter file and you try to do an ALT-F2 and run a command in GNOME or KDE, the environment variable will not have been defined---instead you must open a terminal window and type a command there.

The reason changing the PATH environment variable has no effect is that after fooling with it for about half-an-hour, I found out that the PATH is overridden in /etc/gdm/gdm.conf.  Another disadvantage of this approach as opposed to editing /etc/profile is that you must reboot your computer as opposed to simply logging off and logging back on for the changes to take effect.

Anyways I did that and specified my new PATH environment variable.  I now have another problem.  I want to modify LD_LIBRARY_PATH.  I added the following to /etc/profile, but this is not taking effect.

export LD_LIBRARY_PATH=/opt/lib:$LD_LIBRARY_PATH

/etc/gdm/gdm.conf overrides PATH but not LD_LIBRARY_PATH.  Where do I put this statement so that it takes effect?

Salman

---

### Post by beesee on 2004-10-24
Try ~/.bash_profile.  That gets sourced whenever you log in.  This is where I've always set my environment variables like PATH.

---

### Post by salmankhilji on 2004-10-24
I will try that, but it is UNACCEPTABLE.  This means I cannot set system-wide environment variables for all users.  I must go to each individual account and chagne ~/.bash_profile.

This is exactly what /etc/profile is supposed to do.  But it does not work in Ubuntu.

Salman

---

### Post by salmankhilji on 2004-10-24
[QUOTE=beesee]Try ~/.bash_profile.  That gets sourced whenever you log in.  This is where I've always set my environment variables like PATH.[/QUOTE]
 Ok.  Tried this in ~/.bash_profile:

export LD_LIBRARY_PATH=/opt/lib:$LD_LIBRARY_PATH

It does not work.  I even rebooted the computer.  Environment variable settings in Ubuntu is non-standard and is messed up.  I don't want to RTFM and go thru mailinglists and online forums just to set an environment variable.  This sucks :-(  Please stick to the "standard" way---please.

Which file do I set the variable in so that it will be in effect when I do ALT-F2 and type a command myself.  I don't want .bashrc because I will then have to start a terminal the launch a command from there.

---

### Post by elwis on 2004-10-24
[QUOTE=salmankhilji]Ok.  Tried this in ~/.bash_profile:

export LD_LIBRARY_PATH=/opt/lib:$LD_LIBRARY_PATH

It does not work.  I even rebooted the computer.  Environment variable settings in Ubuntu is non-standard and is messed up.  I don't want to RTFM and go thru mailinglists and online forums just to set an environment variable.  This sucks :-(  Please stick to the "standard" way---please.

Which file do I set the variable in so that it will be in effect when I do ALT-F2 and type a command myself.  I don't want .bashrc because I will then have to start a terminal the launch a command from there.[/QUOTE]
 I have to agree with you. I spent a day with this too, starting to wonder if I was totally stupid or something, trying all the .profile versions I ever learned.

Putting things like this in .bashrc can't possibly be acceptable according to LSB, could it?
I've learned that /etc/profile or even better, profile.local are the right ways to go.

---

### Post by salmankhilji on 2004-10-24
But /etc/profile is NOT getting read!!!  I put a statement something like export JUNK=crap in /etc/profile.  Logged out and logged back in.  The variable did not exist.

/etc/gdm/Xsession is getting read.  I put the above JUNK variable in it and noticed that it was taking effect.  HOWEVER, setting LD_LIBRARY_PATH to something else did not take effect.  It seems like there is another script that is getting read that resets LD_LIBRARY_PATH back to null.  Where is that bloody script file.

In Windows, all you do is right click on My Computer, go to advanced tab, click on Environment varialbles and set them there.  In Linux, you can do the same thing as you can in Windows only it is going to take about 1000 times longer.  I have been trying to set LD_LIBRARY_PATH for  more than 24 hours now.

Looks like I should go back to Fedora!!!  environment variables work as expected and they have the nice profile.d directory that makes in a breeze.

Salman

---

### Post by asimon on 2004-10-24
The best would be to put something like this into /etc/gdm/Xsession
```

case $SHELL in
  */bash)
    [ -z "$BASH" ] && exec $SHELL $0 "$@"
    set +o posix
    [ -f /etc/profile ] && . /etc/profile
    if [ -f $HOME/.bash_profile ]; then
      . $HOME/.bash_profile
    elif [ -f $HOME/.bash_login ]; then
      . $HOME/.bash_login
    elif [ -f $HOME/.profile ]; then
      . $HOME/.profile
    fi
    ;;
  */zsh)
    [ -z "$ZSH_NAME" ] && exec $SHELL $0 "$@"
    emulate -R zsh
    [ -d /etc/zsh ] && zdir=/etc/zsh || zdir=/etc
    zhome=${ZDOTDIR:-$HOME}
    # zshenv is always sourced automatically.
    [ -f $zdir/zprofile ] && . $zdir/zprofile
    [ -f $zhome/.zprofile ] && . $zhome/.zprofile
    [ -f $zdir/zlogin ] && . $zdir/zlogin
    [ -f $zhome/.zlogin ] && . $zhome/.zlogin
    ;;
  */csh|*/tcsh)
    # [t]cshrc is always sourced automatically.
    # Note that sourcing csh.login after .cshrc is non-standard.
    set -a
    eval `$SHELL -c 'if (-f /etc/csh.login) source /etc/csh.login > /dev/null; if (-f ~/.login) source ~/.login > /dev/null; pr
intenv       | egrep -v "^(BASH_VERSINFO|EUID|PPID|UID|GROUPS|SHELLOPTS|_)="'`
    set +a
    ;;
  *) # Plain sh, ksh, and anything we don't know.
    [ -f /etc/profile ] && . /etc/profile
    [ -f $HOME/.profile ] && . $HOME/.profile
    ;;
esac

```
The Code sniplet is from kdm's default Xsession.

I don't use Gnome or gdm but I have this in the Xsession from kdm and with it /etc/profile gets evaluated.

---

### Post by beesee on 2004-10-25
> I put a statement something like export JUNK=crap in /etc/profile. Logged out and logged back in. The variable did not exist.
This means that for whatever reason, you're not getting logged in as a "login shell."  /etc/profile (and ~/.bash_profile) are only sourced by login shells.  Although I normally don't use display managers, like GDM, I'm fairly certain that this is not the correct behavior.  Maybe someone should file a bug?

---

### Post by salmankhilji on 2004-10-25
Could you please file this bug?  You seem to be more familiar with this term named "login shell".  Call me stupid, but after using Linux for about 3 years, I still do not know what a login shell is---other than what you just described here.

Hopefull, this will get fixed in the next release.

Salman

---

### Post by beesee on 2004-10-25
Basically, a login shell is started when you log in.  However, when you open up an xterm, bash won't be invoked as a login shell (unless you start xterm with the --ls option).  /etc/profile and ~/.bash_profile are only sourced for login shells.  For more information, read the "invocation" section of the bash man page.  Here's an excerpt:
> When  bash is invoked as an interactive login shell, or as a non-inter-
active shell with the --login option, it first reads and executes  com-
mands  from  the file /etc/profile, if that file exists.  After reading
that file, it looks for ~/.bash_profile, ~/.bash_login, and ~/.profile,
in  that order, and reads and executes commands from the first one that
exists and is readable.  The --noprofile option may be  used  when  the
shell is started to inhibit this behavior.

When  a  login  shell  exits, bash reads and executes commands from the
file ~/.bash_logout, if it exists.

When an interactive shell that is not a login shell  is  started,  bash
reads  and  executes  commands  from /etc/bash.bashrc and ~/.bashrc, if
these files exist.  This may be inhibited by using the  --norc  option.
The  --rcfile  file option will force bash to read and execute commands
from file instead of /etc/bash.bashrc and ~/.bashrc.

---

### Post by beesee on 2004-10-25
Actually, I just realized the solution to all of this (I think).  Put all the environment stuff in ~/.gnomerc.  Create it if it doesn't exist.

It also occurred to me that bash doesn't even get invoked when you log in through GDM.  That's why /etc/profile isn't getting sourced.

---

### Post by Arun on 2004-11-01
Hello all, 

This is how i got the /etc/profile to be read all the time i open a gnome-terminal or an xterm
this is only for those who want to go the /etc/profile way. 

I may be stupid here, but it worked for me..

1. I disabled the gdm. Iyour runlevels may be different)
sudo mv /etc/rc2.d/S99gdm /etc/rc2.d/K99gdm
So i use startx to launch gnome

2. Once you are inside gnome, every time you launch an xterm, launch it with -ls option, so it reads the /etc/profile file every single time.
if you like the gnome-terminal, then open the profile you are using in gnome-terminal, i am using the default profile, in the second tab, "title and command" make sure the check box against "Run command as login shell" is checked.
Then everytime you launch the gnome-terminal, with this profile you just modified, it will always read the /etc/profile.

Hope this helps,

---

### Post by Bob Collins on 2004-11-01
I asked this question yesterday and the answer I got was to put system wide environment variables in /etc/environment. I worked for me.

See [http://ubuntuforums.org/showthread.php?t=2793](http://ubuntuforums.org/showthread.php?t=2793)

Bob Collins
Sunnyvale CA USA

---

