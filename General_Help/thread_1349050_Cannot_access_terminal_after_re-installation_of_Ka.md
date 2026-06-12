---
title: "Cannot access terminal after re-installation of Karmic"
date: 2009-12-07
forum: General Help
---

### Post by rezapiri09 on 2009-12-07
I re-installed Karmic and now I can't run commands out of the terminal anymore.  When it prompts me for the password I type in every password I have and it doesn't connect.  Did I miss something on re-install?  

when I type something like sudo apt-get install and it prompts for password it spits this out E: Invalid operation or when I try to login as SU it spits out : Authentication failure

When I go to the software center I am able to download using my password- what am I missing here and how do I fix?  Thanks!

---

### Post by jbrown96 on 2009-12-07
So your account password works fine to login? It also works with PolicyKit (adminstrative access for GUI apps)? But doesn't work for command line admin?

Sounds like you got dropped from a group or sudo is messed up.

Could you post the output of the following commands? 

1) ```
groups $USER
```
2) ```
cat /etc/sudoers
```

With #2, you will need to reboot and go into recovery mode. When you reboot you should get a Grub menu (if not then try pressing escape or shift), just choose the second entry (it will be marked recovery). Once that boots, "root shell." Now you can run #2. Here is mine > # /etc/sudoers                      
#                                   
# This file MUST be edited with the 'visudo' command as root.
#                                                            
# See the man page for details on how to write a sudoers file.
#                                                             

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL         

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)                                                 
# %sudo ALL=NOPASSWD: ALL                                          

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL                                 

%admin ALL=NOPASSWD: /usr/sbin/powertop
justin@viking:~$ sudo cat /etc/sudoers 
# /etc/sudoers                         
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

That last line is the only one that you need to make sure is there. 

If #1 did not report that you are in the "admin" group, then run this command while you are still in safe mode (actually, it wouldn't hurt to run it anways -- it can't do any harm). ```
usermod -aG admin USER
``` replace USER with your user name.

---

