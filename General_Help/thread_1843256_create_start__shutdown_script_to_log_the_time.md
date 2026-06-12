---
title: "create start / shutdown script to log the time"
date: 2011-09-13
forum: General Help
---

### Post by dashbm on 2011-09-13
hey guys,

I'd like to log the time I spend working with a script
that runs when I start my PC in the morning and when I
shut it down in the evening.

We are using ubuntu terminal server accounts.
The only place where I can store files is my home directory.
There is a profile in my home directory, too.
That's where I tried to get the script running:

/home/myusername/.profile

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
date >> /home/myusername/time.txt
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

That should be the place where a script could be run when the pc is started..
do you guys have an idea how i could do this? 

I was thinking about a script that I run manually, to log the time when I leave like:

#!/bin/bash
date >> /home/username/time.txt
shutdown now

but that needs to be root and unfortunately I don't have the sudo rights on my user.
Is there another way to create an automatic shutdown script?

Cheers guys,

dash

---

