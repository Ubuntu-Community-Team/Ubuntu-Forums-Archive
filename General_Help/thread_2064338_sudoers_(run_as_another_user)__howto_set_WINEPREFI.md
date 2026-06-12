---
title: "sudoers (run as another user)  howto set WINEPREFIX"
date: 2012-09-29
forum: General Help
---

### Post by go4unkwn on 2012-09-29
hello sudoers experts

i run some windows applications under wine 1.4.
i set up wine for a multiuser environment (see Howto: Install Wine applications for Multiple Users).further i set for each windows application its own wine environment using the environment variable WINEPREFIX. example:

WINEPREFIX=/home/userfoo/.wine-foobar
WINEPREFIX=/home/userfoo/.wine-songbird

i adapted sudores how it is explained in "Howto: Install Wine applications for Multiple Users".

```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
Defaults:USERFOO_USERS env_reset
Defaults:USERFOO_USERS env_keep += DISPLAY
Defaults:USERFOO_USERS env_keep += XAUTHORITY

# Host alias specification

# User alias specification
User_Alias USERFOO_USERS = user1, user2, user3

# Cmnd alias specification
Cmnd_Alias USERFOO = /usr/bin/wine,/usr/bin/winecfg

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

# run wine under user nonet
USERFOO_USERS ALL = (userfoo) NOPASSWD: USERFOO

```in order to run the wine applications i use a bash script, so that user1, user2 and user3 run the wine applications as userfoo.

```
#!/bin/bash

wineprog="foobar2000.exe"
pid=$(pgrep ${wineprog})

if [ $? -ne 0 ]; then
    #sudo -u userfoo -H export WINEPREFIX=/home/userfoo/.wine-foobar2000/
    #export WINEPREFIX=/home/userfoo/.wine-foobar2000/
    xhost +local:userfoo
    sudo -u userfoo -H WINEPREFIX=/home/userfoo/.wine-foobar2000/ wine /home/userfoo/.wine-foobar2000/drive_c/Program Files/foobar2000/"${wineprog}"
else
    exit 0
fi

```unfortunately i couldn't manage to set the WINEPREFIX in the bash script.
sudo complains that the userX has not enough priviliges to set the WINEPREFIX; and therefore wine creats a .wine directory and the wine applications fails to start.

if i set the last line in sudoers from:

```
USERFOO_USERS ALL = (userfoo) NOPASSWD: USERFOO
```to

```
USERFOO_USERS ALL = (userfoo) NOPASSWD: ALL
```everthing works. but i dislike to do this. what do i have to add to the sudoers file, in order the user1, user2 and user3 have the privilieges to set the WINEPREFIX?

any hint is welcome!

kind regards, go4unkwn

---

