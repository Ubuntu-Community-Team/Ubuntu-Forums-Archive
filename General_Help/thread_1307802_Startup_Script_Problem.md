---
title: "Startup Script Problem"
date: 2009-10-31
forum: General Help
---

### Post by scumboss on 2009-10-31
Hi All

I have a script in my /etc/profile.d directory.  The script is executable and in the script is the following: -

export JAVA_HOME=/usr/lib/jvm/java-6-sun
export JAVA_OPTS="-server -Xms1024M -Xmx1536M -XX:MaxPermSize=768M"
export CATALINA_HOME=/usr/local/tomcat

All it does it sets some environment vars.  Anyway, when I reboot the server I have to type in source /etc/profile otherwise the env vars are not set to the above.  Why is this? I thought on boot up it would automatically do a source /etc/profile.

Any ideas?

---

### Post by Barriehie on 2009-10-31
Do you have this file **/etc/profile** ?  You can see how the first IF block sources *.sh files in /etc/profile.d directory.

Mine looks like this:
```

# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

```

Barrie

---

### Post by lswb on 2009-10-31
I believe that /etc/profile and /etc/profile.d/* are used as default profiles for bash, so variables loaded there would not necessarily be available for programs that were not running under an instance of bash. Also if you have a .bash_profile it is used instead of .profile.

Perhaps you could put your variables in /etc/environment

---

### Post by scumboss on 2009-10-31
Checked my /etc/profile and it's the same as yours Barriehie.  lswb I tried adding to the environment file but no luck.

---

### Post by Barriehie on 2009-11-01
Hey, I searched google and the forums and you're not the only one with this issue.  I found what might be a solution though, albeit it's like taking an 8 lb. sledge to drive a picture nail...  Add the necessary lines to rc.local
```

sudo gedit /etc/rc.local

```

I'm assuming you're not using a GUI, i.e. server = CLI.  If GUI then change command to:
```

gksudo gedit /etc/rc.local

```

Let us know!
Barrie

Edit: [This forum link might help](http://ubuntuforums.org/showthread.php?p=2611681#post2611681).

---

### Post by scumboss on 2009-11-02
Naa still the same problem.  :(

---

