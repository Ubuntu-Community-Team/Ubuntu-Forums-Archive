---
title: "Would like to make a bash script for auto start the progamme"
date: 2012-10-12
forum: General Help
---

### Post by captainfreeky on 2012-10-12
I have Ubuntu 12.04lts there is  folder in my home called FlexHub in which there is a file which first loads lua and then the file ( ./lua ./FlexHub.lua ) 
I always have to cd FlexHub then give command ./lua /FlexHub in terminal 
rather i would like to switch to tty1 and login and the script auto loads the flexhub 
this is used for non gui ./lua ./FlexHub.lua --nogui
I am new be in linux i have no knowledge of bash thoug i tried to find out from google but i could make it.Can some one help me out in this ?
If possible plz give step by step that would be good :) so i wont make mistake and then come knocking again

---

### Post by Rexilion on 2012-10-13
For the TTY, you can put the command in

~/.bashrc

Like this:

```
if [[ $- = *i* ]] ; then
	FlexHub/lua FlexHub/FlexHub.lua --nogui
fi
```

For X sessions, you can use the DE's startup manager to load it. Or, maybe with the use of .xsession, like this:

```
FlexHub/lua FlexHub/FlexHub.lua &
```

---

### Post by captainfreeky on 2012-10-13
Well how can i make a boot script in init.d which can boot at everytime when it is either rebooted or kept on ? flexhub should start with nongui that would be done in setting

---

### Post by Rexilion on 2012-10-14
That was not your initial question, why would you want this?

It's not safe to execute programs and scripts as root that reside in a user directory.

---

### Post by captainfreeky on 2012-10-14
I wanted this as i login in ttyl1 i dont need to type cd FlexHub and then teh command instead when i log in i need to auto start i tried GUI but it dint worked as once i can run this i will turn to nongui.

---

### Post by captainfreeky on 2012-10-17
This is what i have written started with all bin bash i have not written that 

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="FlexHub"
NAME=FlexHub.sh
USER=nameofuser
DIR=/home/$username/Flexhub/ # path to flexhub dir
SCRIPTNAME=/etc/init.d/$NAME

set -e

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

if [ "$1" = "start" ]; then
        ping -c 1 google.com
        if [ $? != 0 ]; then
                sleep 30
        fi
fi
cd $DIR
sudo -u $USER ./lua ./FlexHub.sh --nogui

---

