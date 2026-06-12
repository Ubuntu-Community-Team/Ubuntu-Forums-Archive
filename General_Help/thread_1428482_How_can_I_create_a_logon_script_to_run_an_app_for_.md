---
title: "How can I create a logon script to run an app for all users?"
date: 2010-03-12
forum: General Help
---

### Post by mpemburn on 2010-03-12
Hi All,

I'm working on the design of a system that will serve Ubuntu virtual machines to users (via the FreeNX server and [NoMachine]("http://www.nomachine.com")'s NX Web Companion plugin) and I'd like to launch a specific application a soon as someone logs into the VM.  What is the best way to do this?  Specifics would be helpful since I'm 95% software developer and 5% Linux administrator.

Thanks in advance,

Mark

---

### Post by cjhabs on 2010-03-12
> **mpemburn said:**
> Hi All,

I'm working on the design of a system that will serve Ubuntu virtual machines to users (via the FreeNX server and [NoMachine]("http://www.nomachine.com")'s NX Web Companion plugin) and I'd like to launch a specific application a soon as someone logs into the VM.  What is the best way to do this?  Specifics would be helpful since I'm 95% software developer and 5% Linux administrator.

Thanks in advance,

Mark

How about this?
Go into System->Preferences->Sessions and add the program there. It will start up when you login.
You would need to do this for each user.

There is probably a more elegant method that I am not aware of.

---

### Post by Agent ME on 2010-03-12
The commands in ~/.profile will run on logon, so that would be an easier place to add a command for a specific user.

I *think* /etc/profile might work similarly, but for all users.

---

### Post by mpemburn on 2010-03-13
Thanks for your replies.  I need some hand-holding, however.  The app I want to run is:

**/opt/s3Upload/bin/s3Upload**

The /etc/profile looks like this: 

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
```So, where do I put the command to make this work?

Thanks,

Mark

---

### Post by cjhabs on 2010-03-14
From the snippet of code above, you would need to create a file named something like myscript.sh and place it in /etc/profile.d (you'll need to do it with sudo)
Make sure it has read permissions:
sudo chmod +r /etc/profile.d/myscript.sh
 
myscript.sh will contain your desired command line.

---

### Post by mpemburn on 2010-03-14
Well, some progress.  I created a file called 'run-s3upload.sh' in the /etc/profile.d directory and containing only the line:

[FONT=Courier New][SIZE=3]/opt/s3Upload/bin/s3Upload[/SIZE][/FONT]

I tested it by running:

[FONT=Courier New][SIZE=3]mpemburn@ubuntu:/etc/profile.d$ ./run-s3upload.sh[/SIZE][/FONT]

. . . which worked.  Next, I launched a virtual machine to see whether the command would run on start up.  It didn't.  Curious, I logged out of my 'real' Ubuntu machine (which is actually a VM running under Parallels on my MacBook)  and logged back in.  The app (s3Upload) actually *did* launch -- but it came up *before* the login screen, totally blocking it and preventing me from logging in.  If it were not for the fact that I could still spawn VM's, I'd be hosed.  I went in and wiped out run-s3upload.sh and, only then was I able to log back in.  Phew!  I suppose there's some other way to recover if this happens but I have no idea of what it is.

So, really guys, does anyone know for sure how to set up a script that runs _after_ login?

Mark

---

### Post by d3v1150m471c on 2010-03-14
Where and what is the command that launches the virtual machine?

---

### Post by mpemburn on 2010-03-14
d3v1150m471c sez:
> Where and what is the command that launches the virtual machineAs I mentioned above, my Ubuntu (9.10) 'machine' has FreeNX installed.  It runs on top of sshd ****(openssh-server) to serve X Windows sessions via the NoMachine client.  The actual launch of the VM is controlled by a Java applet called "NX Web Companion".  It's a complex little dance and I don't understand it fully.  My guide to setting the system up comes from here:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

-- Mark

---

