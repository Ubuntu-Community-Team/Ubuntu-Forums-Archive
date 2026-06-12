---
title: "RFI: Dropbox to store local configuration files"
date: 2011-01-14
forum: General Help
---

### Post by eentonig on 2011-01-14
Hi all,

I work on several computers throughout the day or week and make extensive use of Dropbox to sync my files between them. 

One of the things that bugged me, was that bash/ssh/screen and other settings weren't synchronised between those new computers. And that I had to go through the hassle of having to recreate all those files when using a new computer. So I decided to start using Dropbox for this as well.

```
#!/bin/bash
# This folder contains my personal prefferences that I want to be able everywhere
# Basically, I keep my personal configuration for a few files stored on my Dropbox 
# and create symlinks to the required files


BASEDIR="$HOME/Dropbox/ubuntu_home"
DEFAULT_APPS=".local/share/applications"

f_symlinking ()
{
    
    #===  FUNCTION  ================================================================
    #          NAME:  f_symlinking
    #   DESCRIPTION:  Checks for the existance of Symbolic links and creates them
    #			if necesary
    #    PARAMETERS:  CONFIG
    #       RETURNS:  
    #===============================================================================
    INPUT=$1
    HOMEPATH="$HOME"
    CONFIG="$HOMEPATH/$INPUT"
    BU=$CONFIG"_old"
    if [ -L $CONFIG ] ; then
	echo -e "\t\tYour $INPUT is already linked."
	echo -e "\t\t\t INPUT = $INPUT -- CONFIG = $CONFIG"

    elif [ -f $CONFIG ]  ; then                 # check if the file exists
	mv $CONFIG $BU
	echo -e "\t\tYour current $INPUT is moved to $BU and a symbolic link is created"
	echo -e "\t\t\t BASEDIR = $BASEDIR -- INPUT = $INPUT -- CONFIG = $CONFIG"
	ln -s $BASEDIR/$INPUT $CONFIG
    elif [ -d $CONFIG ]  ; then                 # Or if it's a folder
	mv $CONFIG $BU
	echo -e "\t\tYour current $INPUT is moved to $BU and a symbolic link is created"
	echo -e "\t\t\t BASEDIR = $BASEDIR -- INPUT = $INPUT -- CONFIG = $CONFIG"
	ln -s $BASEDIR/$INPUT $CONFIG

    else
	echo -e "\t\tNo $INPUT or Symbolic link existed. Creating the Symbolic link now."
	echo -e "\t\t\t BASEDIR = $BASEDIR -- INPUT = $INPUT -- CONFIG = $CONFIG"
	ln -s $BASEDIR/$INPUT $CONFIG
    fi

}	# ----------  end of function f_symlinking  ----------



# ln -s $BASEDIR/.bashrc ~/.bashrc
# Full wrtitten out. The rest will use f_symlinking, which basically does the same.

if [ -L $HOME/.bashrc ] ; then
    echo -e "\t\tYour .bashrc is already linked."
elif [ -f $HOME/.bashrc ]  ; then
    mv $HOME/.bashrc $HOME/.bashrc_old
    echo -e "\t\tYour current .bashrc is moved to .bashrc_old and a symbolic link is created"
    ln -s $BASEDIR.bashrc $HOME/.bashrc
else
    echo -e "\t\tNo .bashrc or Symbolic link existed. Creating the Symbolic link now."
    ln -s $BASEDIR/.bashrc $HOME/.bashrc
fi

# ln -s $BASEDIR/.bash_aliases ~/.bash_aliases
f_symlinking .bash_aliases


# Vim related links
# 
f_symlinking .vim
f_symlinking .vimrc

# Check if the external requirements are fullfiled to use all plugins.
if [ -x /usr/bin/ctags-exuberant ] ; then
    echo -e "\t\t\t\'ctags-exuberant\' seems to be installed. You should be fine for using Gvim."
else
   echo -e "\t\t\t\'ctags-exuberant\' seems not to be installed, but is required for ctags pluging."
   echo -e "\t\t\tPlease consider installing with \'sudo apt-get install ctags-exuberant\'"
fi

# SSH related links
# 
f_symlinking .ssh/config

# .byobu
#
f_symlinking .byobu

# Default applications
#
f_symlinking $DEFAULT_APPS

# :TODO:01/12/2011 10:13:21 AM CET:: 
#	    Clean out $BASEDIR/hosts and create check

#sudo cat $BASEDIR\hosts >> /etc/hosts 

# Screen Configuration
# ln -s $BASEDIR/.byobu/ ~/.byobu
exit 0

```

In the current setup, this works like a charm. I need to include some additional checks to verify if all prerequisites are installed, but apart from that, the concept works. 

I was wondering. 
1. What additional personal config files could benefit from this setup?
2. Do you see any risk in using this setup?

---

### Post by howefield on 2011-01-14
Moved to General Help.

---

