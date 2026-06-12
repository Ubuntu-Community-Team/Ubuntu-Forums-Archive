---
title: "editing $PATH"
date: 2009-07-13
forum: General Help
---

### Post by gos1 on 2009-07-13
When I try to edit my $PATH via 

    ~ nano .profile 
 
    I am getting an empty page. But whatever I put in that file goes in my $path . Now I have made an error in inserting an address to the $PATH how can I fix that . 
 
    I mean how can I directly edit the $PATH ?

---

### Post by benj1 on 2009-07-13
so ./profile is blank now ?
you can just edit the paths in that file, this is my .profile file (default) if you deleted it.

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
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
```

---

### Post by Keith Hedger on 2009-07-13
I may be mistaken but I thought the best place to add to the PATH variable was in the .bashrc file as that is available from any login shell (that's where mine is anyway)

---

### Post by master_kernel on 2009-07-13
> **Keith Hedger said:**
> I may be mistaken but I thought the best place to add to the PATH variable was in the .bashrc file as that is available from any login shell (that's where mine is anyway)
That's correct.

---

### Post by bab1 on 2009-07-13
> **gos1 said:**
> When I try to edit my $PATH via 

    ~ nano .profile 

As @Keith Hedger and master_kernel have said the best place is the .bashrc file rather than .profile.> 
 
    I am getting an empty page. But whatever I put in that file goes in my $path . Now I have made an error in inserting an address to the $PATH how can I fix that . 
 
I mean how can I directly edit the $PATH ?

One does not "edit" the $PATH.  It is a variable.  You assign data to the variable $PATH.  If you change it to something else, it changes.  If you assign a completely new path via a $var=data is retained in memory.  Adding it to the file retains it for the next time the shell is started.

Add the new path to the .bashrc and delete it in the .profile.  The restart the shell.

---

### Post by Keith Hedger on 2009-07-13
This is the last couple of lines of my .bashrc file you may want to use something similar, as it shows the format for thye PATH variable.

DEVPREFIX=/media/LinuxData/Development64/local
PATH=.:${DEVPREFIX}/bin:${DEVPREFIX}/sbin:/usr/local:/usr/local/bin:"${PATH}"

As you can see I set a Variable DEVPREFIX that I use for compiling software and put this at the front of the PATH var so that executables I have compiled are favoured over pre-installed executables, the final "${PATH}" just appends any other alterations that have been made to PATH to the end of the PATH var.
Hope this clears the water a bit.

---

