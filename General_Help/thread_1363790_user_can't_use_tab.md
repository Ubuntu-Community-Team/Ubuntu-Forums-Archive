---
title: "user can't use tab"
date: 2009-12-24
forum: General Help
---

### Post by scambro on 2009-12-24
I just setup a new user on my ubuntu box, and when I'm logged in as that user, I cannot use the tab key to fill in filenames, folders, etc.  I also see just the dollar sign at the beginning of a line instead of user@box:$ like I do with the other users.  

What have I missed?  Thanks!

---

### Post by taurus on 2009-12-24
Does that user have a ~/.bashrc?  You just need to set PS1 in there to whatever you want the prompt to look like.

---

### Post by Dark_Stang on 2009-12-24
I'd look at a few things....
What type of user is it?
What group is the user in?
What permissions did you give the user?

---

### Post by falconindy on 2009-12-24
copy over the contents of /etc/skel to the new user's home folder.

---

### Post by scambro on 2009-12-25
I did not have any .bash files in the home directory for this user, so I copied over the .bash_history, .bash_logout, .bashrc, and .profile files from another user that I wanted to mimic.  I logged out, logged back in, but no change.  Is there something else I need to do for it to take affect? 

Thanks!

---

### Post by bodhi.zazen on 2009-12-25
Well, what shell are you using ? (my guess is sh)

```
echo $SHELL
```

if it is not bash, change to bash with chsh

chsh user_name

enter password, change shell to /bin/bash

---

### Post by scambro on 2009-12-25
I don't recall ever having to set this before when creating new users, so I must have messed something up there...

```
$ chsh
Password:
Changing the login shell for rt
Enter the new value, or press ENTER for the default
        Login Shell [/bin/sh]: /bin/bash
$ echo $shell

$ echo $0
-sh
$
```

```
$ set
HOME='/home/rt'
IFS='
'
LOGNAME='rt'
MAIL='/var/mail/rt'
OLDPWD='/home/rt/data'
OPTIND='1'
PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'
PPID='32751'
PS1='$ '
PS2='> '
PS4='+ '
PWD='/home/rt/data/done'
SHELL='/bin/sh'
SSH_CLIENT='1.1.1.1 49182 22'
SSH_CONNECTION='1.1.1.1 49182 2.2.2.2 22'
SSH_TTY='/dev/pts/2'
TERM='xterm'
USER='rt'
XDG_SESSION_COOKIE='acb4188bd96cd0075a20f4bb4b336c3b-1261721250.259256-801733561'
_='echo'
$ s
```

Is it just that I haven't really logged out since I made the .bash changes?  I closed my connection and reopened it, because when I tried to logout:

> $ logout
-sh: logout: not found


Thanks!

---

### Post by bodhi.zazen on 2009-12-25
You should be good to go now.

It is echo $SHELL not $shell

You will need to log out and back in =)

How did you add a user ?

---

### Post by scambro on 2009-12-25
Ah, I closed my connection and then just waited it out a bit and now it's better.

I don't have my hisory saved that far back, but I thought I had used the adduser command, but I've had to do some searches on a few things I do not recall needing to manually do before.

Thanks for the help!

---

### Post by bodhi.zazen on 2009-12-25
look at the difference between adduser and useradd =)

---

### Post by scambro on 2009-12-25
> **bodhi.zazen said:**
> look at the difference between adduser and useradd =)
D'oh!  I don't add users often enough to have done that before, so I just went from memory and the command "worked" so I thought, good.  Oops.  :)

---

