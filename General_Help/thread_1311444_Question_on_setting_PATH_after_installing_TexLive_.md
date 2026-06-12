---
title: "Question on setting PATH after installing TexLive 2008"
date: 2009-11-02
forum: General Help
---

### Post by JamesM. on 2009-11-02
Greetings everyone,

This is my first post here.
Today I have been trying to install TexLive2008 into ubuntu 9.10

I followed this guide [http://ubuntuforums.org/showthread.php?t=1106025](http://ubuntuforums.org/showthread.php?t=1106025)

However, after I added these 3 lines into my .profile file under home directory, I was no longer able to log in ubuntu. So I had to reformat hard drive and reinstall ubuntu.  
I guess I might have done something wrong on setting PATH part, so I would like to know what is the right way to add these 3 lines or setting PATH for TexLive 2008.

Thanks

edit: the I added these 3 lines at the end of .profile file

---

### Post by jlamber on 2009-11-02
This happens to me also.  I have to reinstall my system.

I added the path to the /etc/environment file instead of the profile like in your case.  

How can I make TexLive available to all users.  What is the best place to put this?

---

### Post by flybytay on 2009-11-13
> **JamesM. said:**
> 
I followed this guide [http://ubuntuforums.org/showthread.php?t=1106025](http://ubuntuforums.org/showthread.php?t=1106025)

However, after I added these 3 lines into my .profile file under home directory, I was no longer able to log in ubuntu.
[This information can be obtained from the texlive documentation]("http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#x1-350003.4.3")
This is my ~/.profile (attention I use x86_64-linux )
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
if [ -d "/usr/local/texlive/2009/bin/x86_64-linux" ] ; then
    PATH="/usr/local/texlive/2009/bin/x86_64-linux:$PATH"
fi
if [ -d "/usr/local/texlive/2009/texmf" ] ; then
    export TEXMFMAIN="/usr/local/texlive/2009/texmf"
fi
if [ -d "/usr/local/texlive/2009/texmf-dist" ] ; then
    export TEXMFDIST="/usr/local/texlive/2009/texmf-dist"
fi
if [ -d "/usr/local/texlive/texmf-local" ] ; then
    export TEXMFLOCAL="/usr/local/texlive/texmf-local"
fi
if [ -d "$HOME/texmf" ] ; then
    export TEXMFHOME="$HOME/texmf"
fi
if [ -d "$HOME/.texlive2009/texmf-config" ] ; then
    export TEXMFCONFIG="$HOME"
fi
if [ -d "/usr/local/texlive/2009/texmf-config" ] ; then
    export TEXMFSYSCONFIG="/usr/local/texlive/2009/texmf-config"
fi
if [ -d "$HOME/.texlive2009/texmf-var" ] ; then
    export TEXMFVAR="$HOME"
fi
if [ -d "/usr/local/texlive/2009/texmf-var" ] ; then
    export TEXMFSYSVAR="/usr/local/texlive/2009/texmf-var"
fi
```

---

