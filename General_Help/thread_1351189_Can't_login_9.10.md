---
title: "Can't login 9.10"
date: 2009-12-10
forum: General Help
---

### Post by randome20170520 on 2009-12-10
I did a search and ran the suggested commands.  When I enter my user id and password, the display blanks out, and brings me back to the login screen.


It seems my .profile cannot be opened, but I am at a loss on how to proceed.  Any assistance would be appreciated.  


   chrisu@Zen-531-L:~$ cat .xsession-errors
  /etc/gdm/Xsession: Beginning session setup...
  Setting IM through im-switch for locale=en_US.
  Start IM through /home/chrisu/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/none.
  /etc/gdm/Xsession: Beginning session setup...
  .: 34: Can't open /home/chrisu/.profile
   
  chrisu@Zen-531-L:~$ ls -li .profile
  761862 -rwxr-xr-x 1 chrisu chrisu 675 2009-04-09 16:18 .profile
   
  chrisu@Zen-531-L:~$ cat .profile
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

---

