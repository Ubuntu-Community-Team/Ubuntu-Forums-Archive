---
title: "visudo help needed"
date: 2010-01-02
forum: General Help
---

### Post by masterskop on 2010-01-02
Hi,

Is there a way to grant 'root' privileges to my user account?  My account name ... I'll call it 'masterskop' as it is my forum name here, but not on my computer.  Would it look like this in the sudoers' file?

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
[B]masterskop  ALL=(ALL) ALL
[/B]
# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


My purpose is to get access to all the folders and files in the 'File System'.  The root and lost+found folders have 'Xs' on them...No access! And for example, under properties of the 'var' folder it states that 'you are not the owner, so you cannot change these permissions.'  How can I get access to all of it everytime I login as the main user of my computer?  I do not have anyone else using this computer.

PS... I did edit this file and used my real user name ... logged out and logged back in and still I do not have access/edit these folders and files.

Any help is appreciated....
masterskop

---

### Post by Leppie on 2010-01-02
for this you should not have to edit the sudoers file.
if you want to access all files with root permissions, you can put yourself in the admin group (the main user should by default be in the admin group in ubuntu distro's).
to gain access to files and folders with root permissions, launch nautilus with root access:
```
gksudo nautilus --no-dekstop --browser  ##gksudo may be gksu on some systems
```

---

### Post by jonest1 on 2010-01-02
You should be able to type 'sudo su -' to have a shell as the root account.  In that shell, everything happens as root.  Use this option with caution.

For the graphical nautilus file manager, using 'gksudo nautilus' works for me.

BTW, Tmcfaulty, that was lame!

---

### Post by masterskop on 2010-01-02
Thanks for the replys! But, I do wish to make this a permanent situation however.

---

### Post by jonest1 on 2010-01-03
I've read over your post and had another think on this one.

What it sounds like to me is that you want to login and have root level privilege on everything you do.

The separation of privileges between the root account and user accounts is an essential part of the security of any system, even Windows.  By having this clear separation, we are protected from most of the virus/spyware/malware threats.  Simply put, if something runs on my system which is trying to edit system files or install software to start with my system, it will not be allowed without the password for regular sudo rights.  

There are other benefits in having root and the user account separated.  When I was doing PC support on machines where the user had admin rights (ie: win9x or winXP with local admin), there were many, many times where the end user made mistakes which were not intentional, but caused major problems.  The most common mistake was accidentally dragging and dropping a directory to the wrong location.

Of course, there are ways around just about everything, but I feel the essential question which has not been answered is why you need this level of access when sudo is available when the need arises?  Is there a special application which requires this type of access, or is it only for ease of use?  If it is for ease of use, how often does this requirement come up?

---

