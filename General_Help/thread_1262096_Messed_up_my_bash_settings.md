---
title: "Messed up my bash settings"
date: 2009-09-09
forum: General Help
---

### Post by Tsega on 2009-09-09
I have the same problem, but my I believe mine is a little bit complicated. I was trying to set my $JAVA_HOME enviornment variable and I think, I might have messed up my bash settings. Here is what I get after entering in my user name and password:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem."

The details of the ~/.xsession-errors

/etc/gdm/xsession Beginning session setup...
/etc/profile: 26: id: not found
[: 26: Illegal number
/etc/gdm/xsession: 179: grep: not found
/etc/gdm/xsession: 192: ls: not found
/etc/gdm/xsession: Executing default failed, will try to run x-terminal-emulator
exec: 205: x-terminal-emulator: not found

I have tried every suggestion in this thread [http://ubuntuforums.org/showthread.php?t=1248286](http://ubuntuforums.org/showthread.php?t=1248286) but I can't even log in using the failsafe sessions. I did manage to delete the extra entries from my /etc/profile, ~/.bashrc, /etc/bash.bashrc, but nothing seems to change same old error. I even had(meaning I removed it) this shell script in /etc/profile.d/javahome.sh that contained the following:

export JAVA_HOME="path yo my java directory"

Well anyways that's where I am right now, so can someone please help.

---

### Post by Slim Odds on 2009-09-09
It would help if we could actually see the file.

---

### Post by Tsega on 2009-09-09
Here is the content of my /etc/profile file:

```

#/etc/profile system-wide .profile file for the Bourne shell(sh(1))
#and Bourne compatible shells(bash(1), ksh(1), ash(1), ...).

if[-d /etc/profile.d]; then
  for i in /etc/profile.d/*.sh; do
    if[-r $i]; then
      .$i
    fi
  done
  unset i
fi

if["$PS1"]; then
  if["$BASH"]; then
    PS1 = '\u@\h:\w\$'
    if[ -f /etc/bash.bashrc]; then
      . /etc/bash.bashrc
    fi
    else
      if["id. -u`" -eq 0]; then
        PS='#'
      fi
      else
        PS='$'
      fi
  fi
fi

umask 022

```

Well that what it has, so anything that looks wrong?

---

### Post by Slim Odds on 2009-09-09
That looks like the original file.

What did you edit to cause the problem? and what does it look like?

---

### Post by Tsega on 2009-09-10
Well here is what I did,

Since I work heavily with the Netbeans, inorder to install it I added the JAVA_HOME & PATH entiries to my ~/.bashrc file manually, after manually installing the jdk, some where on my system.

The installer for netbeans automatically found my java installation and it worked fine. However, the "java -version" console command didn't bring up anything except the default list that you get when java is not installed. 

So I figured, the problem should be that the JAVA_HOME is not being found by the command (I also tried to run a java app and it showed me the error that JAVA_HOME is not set) and so I need to set it up. 

So I tried the suggestion I found here [http://blogs.i2m.dk/allan/2008/12/31/setting-java_home-on-ubuntu/](http://blogs.i2m.dk/allan/2008/12/31/setting-java_home-on-ubuntu/)

That is create a .sh file name javahome.sh containing this

```

export JAVA_HOME='path to my jvm'

```

in /etc/profile.d/ 

and added this in /etc/profile

```

for script in /etc/profile.d/*.sh ; do
if [ -r $script ] ; then
. $script
fi
done

```

and realized that this already exists in the /etc/profile itself so I removed it, after restarting my system I started to have the problems.

Sorry about the long response I'll make it short next time.

---

### Post by Tsega on 2009-09-10
FIXED IT!

Man what a bummer! I fixed it, you know what it was, I changed the /etc/enviornment file and added the export JAVA_HOME line and that was the problem. 

Thank you very much for your help **Slim Odds**. I was reading the post that I found here, [http://blogs.i2m.dk/allan/2008/12/31...ome-on-ubuntu/](http://blogs.i2m.dk/allan/2008/12/31...ome-on-ubuntu/) ,  then suddenly remembered I had changed the file so I went there and removed the lines and it worked. Thanks again for your help had it not been for you asking me questions, I would have reinstalled my system for this very silly mistake.

---

