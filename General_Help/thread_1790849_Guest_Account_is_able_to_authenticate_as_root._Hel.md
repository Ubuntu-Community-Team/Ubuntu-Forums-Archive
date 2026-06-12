---
title: "Guest Account is able to authenticate as root. Help!"
date: 2011-06-25
forum: General Help
---

### Post by ahears on 2011-06-25
[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] 				**Guest Account is able to authenticate as root. Help!** 			
 			 			 		   		 		 		I am trying to  use a guest account in Ubuntu 10.10 however I am unable to stop the  guest account from authenticating as a superuser and gaining root  permissions despite removing all permissions from the user-group control  panel. The new guest account I created is not part of the admin group.  However, with my new guest account I am unable to start a guest session  from the panel, AND if I use the guest session from the panel I dont  have the problem with the guest session being able to authenticate. How  do I prevent super user authentication from an account in this  situation? It seems that any  account can authenticate and my  /etc/sudoers file looks like this:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

