---
title: "sudoers NOPASSWD not working"
date: 2012-01-25
forum: General Help
---

### Post by kingmob on 2012-01-25
I want to grant the users in the %sudo group the rights to run several commands without a password. Mostly because I run these commands remotely in a script via plink. However, where this worked fine before, I can not get it to work anymore on a new install and for the life of me can not figure out why it isn't working. Trying to find an answer just gives me the wisdom that the file is read from top to bottom over and over. This seems to be the common mistake but is certainly not the case here?
I have tried several variants of the NOPASSWD line, but a typo does not appear to be the problem.

```

#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/reboot, /sbin/halt

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# Allow members of group sudo to execute the following without password
%sudo   ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS, /etc/init.d/lightdm

#includedir /etc/sudoers.d

```

---

### Post by SteveDee on 2012-01-25
The format is generally:-
```

%admin ALL = NOPASSWD: /sbin/shutdown

```
...or for a user:-
```

myuser ALL = NOPASSWD: /sbin/shutdown

```
...and you still need to include sudo in your command, even though a password will not be requested:-
```

sudo shutdown -h now

```

---

### Post by Karlchen on 2012-01-25
```
# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# Allow members of group sudo to execute the following without password
%sudo   ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS, /etc/init.d/lightdm
```Hm, I guess the problem is that the group entry for the user group **sudo** appears twice and that going top down the first entry which does require entering the user's password will be found first and used by the sudo command. It will be used because it is the first line which matches and because the commands given in the next line are part of ALL commands. ALL commands match any command, no exceptions. So why should sudo check for a more restrictive commandline further down the file???

Moroever, you do not want the members of the **sudo** group to run the commands shutdown and lightdm as an arbitrary user, but as root only. Therefore I assume the relevant line should read ```
%sudo ALL=(root) NOPASSWD: SHUTDOWN_CMDS, /etc/init.d/lightdm
```Karl

---

### Post by kingmob on 2012-01-26
> **Karlchen said:**
> ```
# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# Allow members of group sudo to execute the following without password
%sudo   ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS, /etc/init.d/lightdm
```Hm, I guess the problem is that the group entry for the user group **sudo** appears twice and that going top down the first entry which does require entering the user's password will be found first and used by the sudo command. It will be used because it is the first line which matches and because the commands given in the next line are part of ALL commands. ALL commands match any command, no exceptions. So why should sudo check for a more restrictive commandline further down the file???

Moroever, you do not want the members of the **sudo** group to run the commands shutdown and lightdm as an arbitrary user, but as root only. Therefore I assume the relevant line should read ```
%sudo ALL=(root) NOPASSWD: SHUTDOWN_CMDS, /etc/init.d/lightdm
```Karl

Thanks, but I already tried those things and it doesn't work. The file is read from top to bottom and anything that is matched overwrites anything before. I tried setting it for a specific user anyway, but that doesn't make a difference sadly.

Why should these shutdown commands be run as root btw?

---

### Post by Karlchen on 2012-01-26
Hello, kingmob.
> Why should these shutdown commands be run as root btw?Why else would you want to prefix **sudo **to the commandline? If you prefix **sudo **to a commandline without adding the option **-u username** then **-u root **is assumed.
If you are user *A*, then running *shutdown *as user *B* does not make too much sense, but running *shutdown *as *root *does.

Have done a little homework and created two entries for one sample user group. This is possible and will have the desired effect provided each line is syntactically ok.
```
%testers ALL = (root) PASSWD: ALL
%testers ALL = (operator) NOPASSWD: /usr/bin/top
```Members of the tester group can run any command as root provided they enter their own password. They can run top as operator without giving a password.

So the lines ```
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/reboot, /sbin/halt
%sudo   ALL=(ALL:ALL) ALL
%sudo   ALL=(root) NOPASSWD: SHUTDOWN_CMDS, /etc/init.d/lightdm
``` should have the desired effect.

You simply stated, it did not work. As a rule Linux commands succeed silently, but they fail and tell you why they fail.
So can you please give an example of the command that you ran and the error message you received?

Kind regards,
Karl

---

### Post by kingmob on 2012-02-04
> **Karlchen said:**
> Hello, kingmob.
Why else would you want to prefix **sudo **to the commandline? If you prefix **sudo **to a commandline without adding the option **-u username** then **-u root **is assumed.
If you are user *A*, then running *shutdown *as user *B* does not make too much sense, but running *shutdown *as *root *does.

Have done a little homework and created two entries for one sample user group. This is possible and will have the desired effect provided each line is syntactically ok.
```
%testers ALL = (root) PASSWD: ALL
%testers ALL = (operator) NOPASSWD: /usr/bin/top
```Members of the tester group can run any command as root provided they enter their own password. They can run top as operator without giving a password.

So the lines ```
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/reboot, /sbin/halt
%sudo   ALL=(ALL:ALL) ALL
%sudo   ALL=(root) NOPASSWD: SHUTDOWN_CMDS, /etc/init.d/lightdm
``` should have the desired effect.

You simply stated, it did not work. As a rule Linux commands succeed silently, but they fail and tell you why they fail.
So can you please give an example of the command that you ran and the error message you received?

Kind regards,
Karl
Hi an thx for the elaborate answer. Ok, I see now I maybe skipped something in my explanation. It doesn't really 'fail', it seems like it isn't matched. Ubuntu simply asks for a password anyway, pretty much ignoring the last line. As you have tested, this should not happen. I am stumped :\

---

