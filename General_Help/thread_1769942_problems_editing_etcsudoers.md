---
title: "problems editing /etc/sudoers"
date: 2011-05-28
forum: General Help
---

### Post by 3xp10r3r|X13 on 2011-05-28
hello there,
I am having following problem:

I have created an account using the terminal and now this standard user doesn't seem to be able to perform sudo tasks, such as sudo apt-get update. (just an ubuntu example)

after a bit of research I found out that I had to edit /etc/sudoers. Unfortunately I wasn't able to follow the guides offered by the web. I didn't really get if I had to put my account on the same stage as root so:

user ALL=(ALL) ALL

or edit something else... (do I really have to use vim as an editor - referring to visudo?)

But basically what I want is a standard account which is able to perform root tasks by using sudo.

--> when I try to sudo something it always tells me that the password would be wrong, though it is the exact same password I always use to log in as root.

is somebody there who can give me a bit of support in this issue?

any help is really appreciated!!! 

PS: I am using slackware but I guess that should not be a problem at all

---

### Post by TeoBigusGeekus on 2011-05-28
```
su
```
to go into the root account and then
```
EDITOR=nano visudo
```
to edit the sudoers file with nano.
Add the line
```
your_new_username ALL=(ALL) ALL
```
save, exit, reboot, post what happened.

---

### Post by 3xp10r3r|X13 on 2011-05-28
wow, that was quick!
 
thanks for your quick reply,
but am I meant to edit the privileges, where root is listed as well? ( so just to get this right, I am allowed to use any editor I want, because in the document it says "use visudo" - guess that is just the preferred editor by the os) 

to sum up:
- edit the empty line beneath "root ALL ...."

---

### Post by TeoBigusGeekus on 2011-05-28
Just add the line I've posted you at the end of the file.

---

### Post by 3xp10r3r|X13 on 2011-05-28
Not working, it still doesn't accept the password...

suggestions?

---

### Post by Dave_L on 2011-05-28
If your /etc/sudoers file contains a line like this:

```
%admin ALL=(ALL) ALL
```

then another solution is to add the user to the "admin" group.  By default, only the first user (created during installation) is added to this group.

---

### Post by 3xp10r3r|X13 on 2011-05-29
that might represent a great possibility (the admin group)
--> in slackware, you've just got root...

I will tell you if it worked

thanks for the reply

---

### Post by 3xp10r3r|X13 on 2011-05-29
using the terminal and "su" I am able to log in as root, but if I try "sudo" it's still not working...

I have created an account and added it to the adm group (well at least I think I did). 
Can I edit /etc/group to change something or is there another password for sudo than root?

--> toor doesn't work as well

- please stick to this thread

I appreciate any help!!!

---

### Post by TeoBigusGeekus on 2011-05-29
Can you post us the contents of your sudoers file?

---

### Post by Dave_L on 2011-05-29
"adm" or "admin"?  Ubuntu has both groups, but the latter is the one in /etc/sudoers.

I think that you can add a user to a group by editing /etc/group, but the "usermod" command is the normal way to make that change.

---

### Post by 3xp10r3r|X13 on 2011-05-29
to Dave: I'm using slackware and not ubuntu so adm

to Teo: Here you go:

# sudoers file.
##
## This file MUST be edited with the 'visudo' command as root.
## Failure to use 'visudo' may result in syntax or file permission errors
## that prevent sudo from running.
##
## See the sudoers man page for the details on how to write a sudoers file.
##

##
## Host alias specification
##
## Groups of machines. These may include host names (optionally with wildcards),
## IP addresses, network numbers or netgroups.
# Host_Alias    WEBSERVERS = www1, www2, www3

##
## User alias specification
##
## Groups of users.  These may consist of user names, uids, Unix groups,
## or netgroups.
# User_Alias    ADMINS = millert, dowdy, mikef

##
## Cmnd alias specification
##
## Groups of commands.  Often used to group related commands together.
# Cmnd_Alias    PROCESSES = /usr/bin/nice, /bin/kill, /usr/bin/renice, \
#                           /usr/bin/pkill, /usr/bin/top

##
## Defaults specification
##
## You may wish to keep some of the following environment variables
## when running commands via sudo.
##
## Locale settings
# Defaults env_keep += "LANG LANGUAGE LINGUAS LC_* _XKB_CHARSET"
##
## Run X applications through sudo; HOME is used to find the
## .Xauthority file.  Note that other programs use HOME to find
## configuration files and this may lead to privilege escalation!
# Defaults env_keep += "HOME"
##
## X11 resource path settings
# Defaults env_keep += "XAPPLRESDIR XFILESEARCHPATH XUSERFILESEARCHPATH"
##
## Desktop path settings
# Defaults env_keep += "QTDIR KDEDIR"
##
## Allow sudo-run commands to inherit the callers' ConsoleKit session
# Defaults env_keep += "XDG_SESSION_COOKIE"
##
## Uncomment to enable special input methods.  Care should be taken as
## this may allow users to subvert the command being run via sudo.
# Defaults env_keep += "XMODIFIERS GTK_IM_MODULE QT_IM_MODULE QT_IM_SWITCHER"
##
## Uncomment to enable logging of a command's output, except for
## sudoreplay and reboot.  Use sudoreplay to play back logged sessions.
# Defaults log_output
# Defaults!/usr/bin/sudoreplay !log_output
# Defaults!/usr/local/bin/sudoreplay !log_output
# Defaults!/sbin/reboot !log_output

##
## Runas alias specification
####

##
## User privilege specification
##
root ALL=(ALL) ALL

## Uncomment to allow members of group wheel to execute any command
# %wheel ALL=(ALL) ALL

## Same thing without a password
# %wheel ALL=(ALL) NOPASSWD: ALL

## Uncomment to allow members of group sudo to execute any command
# %sudo ALL=(ALL) ALL

## Uncomment to allow any user to run sudo if they know the password
## of the user they are running the command as (root by default).
# Defaults targetpw  # Ask for the password of the target user
# ALL ALL=(ALL) ALL  # WARNING: only use this together with 'Defaults targetpw'

## Read drop-in files from /etc/sudoers.d
## (the '#' here does not indicate a comment)
#includedir /etc/sudoers.d

that's all

do you need my /etc/group as well?

---

### Post by 3xp10r3r|X13 on 2011-06-01
Well, as nobody has come up with a solution I will just leave this issue, because logging in as su (root) works fine.
It is only sudo which is still giving me troubles. - I guess I will have to use su instead. (might actually be an advantage, bacause you don't have to type sudo everytime,  you perform a root command)

However, thanks for your support :)

---

### Post by Dave_L on 2011-06-01
If you uncomment the line in /etc/sudoers for the group "sudo", and then add your user to that group, the user should be able to use sudo.

Edit /etc/sudoers and change:
```
## Uncomment to allow members of group sudo to execute any command
# %sudo ALL=(ALL) ALL
```

To:
```
## Uncomment to allow members of group sudo to execute any command
%sudo ALL=(ALL) ALL
```

---

### Post by 3xp10r3r|X13 on 2011-06-02
it is already set to just % without any restrictions, that just root is able to perform that command. (wouldn't make any sense if just the root user would be able to access the root user :) )

however, I am able to type sudo and it even asks me for the password. The only problem is that it is not accepting the root password.

But thanks, I didn't check that one XD

this error is really weird, isn't it?

---

