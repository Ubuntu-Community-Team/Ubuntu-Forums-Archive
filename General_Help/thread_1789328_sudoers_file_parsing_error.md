---
title: "sudoers file parsing error"
date: 2011-06-23
forum: General Help
---

### Post by sudipta_cht on 2011-06-23
Folks,
 I am trying to modify my /etc/sudoers file using visudo and I am getting a parsing error near line 9/10 of my config. Can someone please tell me what I am doing wrong? 

> 
# /etc/sudoers
# This file MUST be edited with the 'visudo' command as root.
# See the man page for details on how to write a sudoers file.

Defaults        env_reset

# Host alias specification

# User alias specification
User_Alias HTML_Group = user1, user2
User_Alias Admin_Group = user1,user3,user4
Runas_Alias WWW = www-data

# Cmnd alias specification
Cmnd_Alias LINK = /opt/www/www_data_command.sh

# User privilege specification
root    ALL=(ALL) ALL
Admin_Group ALL=ALL

# Every HTML developer can execute the link_www command
HTML_Group ALL= (WWW) LINK

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Add bitnami paths to sudo
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"


Somehow it doesn't seem to like my two User_Alias directives. 

Thanks in advance!

---

### Post by gmargo on 2011-06-23
Alias names must be a string of uppercase letters, numbers, and underscore characters, and must start with an uppercase letter.  You may not use lowercase letters.

See the **sudoers(5)** man page for full syntax.

---

### Post by MSPdwalt on 2011-06-23
Also you don't have spaces between

> User_Alias Admin_Group = user1,user3,user4

I think it should be user1, user3, user4

---

