---
title: "DBUS issues"
date: 2009-08-24
forum: General Help
---

### Post by SiberianBear on 2009-08-24
I seem to be having issues with dbus.

i have the following in my .xsession :

#!/bin/bash

## test for an existing bus daemon, just to be safe
if test -z "$DBUS_SESSION_BUS_ADDRESS" ; then
    ## if not found, launch a new one
    eval `dbus-launch --sh-syntax --exit-with-session`
fi
#xset r rate 250 50  &           # ok
urxvtd -o -q -f &               # ok
gnome-settings-daemon &
xxkb &
awesome
xsetroot -solid gray38&
#gnome-session
xrandr --output DVI-0 --right-of DVI-1


once I sign in, I see the following in  the output of 'env', for instance:
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-jnNpT8SMb6,guid=925f7bbec932fdf5145d43ec4a92d6f5

however, when I look in /tmp I see that it doesn't actually exist:
vxp@csibox:~$ ls -l /tmp
total 32
-rw------- 1 tomcat6   tomcat6      0 Aug 24 13:52 3060.jsvc_up
srwxr-xr-x 1 vxp       vxp,mking    0 Aug 24 14:11 OSL_PIPE_1001_SingleOfficeIPC_c160dde5eddb5339908ce543cb45fba5
drwx------ 2 tomcat6   tomcat6   4096 Aug 24 13:52 hsperfdata_tomcat6
drwxr-xr-x 2 vxp       vxp,mking 4096 Aug 24 14:21 hsperfdata_vxp
drwx------ 2 vpolyakov vpolyakov 4096 Aug 24 14:05 kde-vpolyakov
drwx------ 2 vpolyakov vpolyakov 4096 Aug 24 14:05 ksocket-vpolyakov
drwx------ 2 vpolyakov vpolyakov 4096 Dec 31  1969 orbit-vpolyakov
drwx------ 2 vxp       vxp,mking 4096 Dec 31  1969 orbit-vxp
drwxr-xr-x 2 vxp       vxp,mking 4096 Aug 24 14:27 svajp.tmp
drwxr-xr-x 2 tomcat6   root      4096 Aug 24 13:52 tomcat6-temp
vxp@csibox:~$ 

this obviously causes issues with everything that uses dbus.

I've issues with firefox, evolution / kmail, etc ...

if i launch kmail for instance:
vxp@csibox:~$ kmail
<unknown program name>(7852)/: Cannot find the D-Bus session server 
vxp@csibox:~$ echo $?
255
vxp@csibox:~$ 



how do I fix this?

---

### Post by SiberianBear on 2009-08-24
I seem to be having issues with dbus.

i have the following in my .xsession :

#!/bin/bash

## test for an existing bus daemon, just to be safe
if test -z "$DBUS_SESSION_BUS_ADDRESS" ; then
    ## if not found, launch a new one
    eval `dbus-launch --sh-syntax --exit-with-session`
fi
#xset r rate 250 50  &           # ok
urxvtd -o -q -f &               # ok
gnome-settings-daemon &
xxkb &
awesome
xsetroot -solid gray38&
#gnome-session
xrandr --output DVI-0 --right-of DVI-1


once I sign in, I see the following in  the output of 'env', for instance:
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-jnNpT8SMb6,guid=925f7bbec932fdf5145d43ec4a92d6f5

however, when I look in /tmp I see that it doesn't actually exist:
vxp@csibox:~$ ls -l /tmp
total 32
-rw------- 1 tomcat6   tomcat6      0 Aug 24 13:52 3060.jsvc_up
srwxr-xr-x 1 vxp       vxp,mking    0 Aug 24 14:11 OSL_PIPE_1001_SingleOfficeIPC_c160dde5eddb5339908c  e543cb45fba5
drwx------ 2 tomcat6   tomcat6   4096 Aug 24 13:52 hsperfdata_tomcat6
drwxr-xr-x 2 vxp       vxp,mking 4096 Aug 24 14:21 hsperfdata_vxp
drwx------ 2 vpolyakov vpolyakov 4096 Aug 24 14:05 kde-vpolyakov
drwx------ 2 vpolyakov vpolyakov 4096 Aug 24 14:05 ksocket-vpolyakov
drwx------ 2 vpolyakov vpolyakov 4096 Dec 31  1969 orbit-vpolyakov
drwx------ 2 vxp       vxp,mking 4096 Dec 31  1969 orbit-vxp
drwxr-xr-x 2 vxp       vxp,mking 4096 Aug 24 14:27 svajp.tmp
drwxr-xr-x 2 tomcat6   root      4096 Aug 24 13:52 tomcat6-temp
vxp@csibox:~$ 

this obviously causes issues with everything that uses dbus.

I've issues with firefox, evolution / kmail, etc ...

if i launch kmail for instance:
vxp@csibox:~$ kmail
<unknown program name>(7852)/: Cannot find the D-Bus session server 
vxp@csibox:~$ echo $?
255
vxp@csibox:~$ 



how do I fix this?

---

### Post by SiberianBear on 2009-08-24
I seem to be having issues with dbus.

i have the following in my .xsession :

#!/bin/bash

## test for an existing bus daemon, just to be safe
if test -z "$DBUS_SESSION_BUS_ADDRESS" ; then
    ## if not found, launch a new one
    eval `dbus-launch --sh-syntax --exit-with-session`
fi
#xset r rate 250 50  &           # ok
urxvtd -o -q -f &               # ok
gnome-settings-daemon &
xxkb &
awesome
xsetroot -solid gray38&
#gnome-session
xrandr --output DVI-0 --right-of DVI-1


once I sign in, I see the following in  the output of 'env', for instance:
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-jnNpT8SMb6,guid=925f7bbec932fdf5145d43ec4a92d6f5

however, when I look in /tmp I see that it doesn't actually exist:
vxp@csibox:~$ ls -l /tmp
total 32
-rw------- 1 tomcat6   tomcat6      0 Aug 24 13:52 3060.jsvc_up
srwxr-xr-x 1 vxp       vxp,mking    0 Aug 24 14:11 OSL_PIPE_1001_SingleOfficeIPC_c160dde5eddb5339908c  e543cb45fba5
drwx------ 2 tomcat6   tomcat6   4096 Aug 24 13:52 hsperfdata_tomcat6
drwxr-xr-x 2 vxp       vxp,mking 4096 Aug 24 14:21 hsperfdata_vxp
drwx------ 2 vpolyakov vpolyakov 4096 Aug 24 14:05 kde-vpolyakov
drwx------ 2 vpolyakov vpolyakov 4096 Aug 24 14:05 ksocket-vpolyakov
drwx------ 2 vpolyakov vpolyakov 4096 Dec 31  1969 orbit-vpolyakov
drwx------ 2 vxp       vxp,mking 4096 Dec 31  1969 orbit-vxp
drwxr-xr-x 2 vxp       vxp,mking 4096 Aug 24 14:27 svajp.tmp
drwxr-xr-x 2 tomcat6   root      4096 Aug 24 13:52 tomcat6-temp
vxp@csibox:~$ 

this obviously causes issues with everything that uses dbus.

I've issues with firefox, evolution / kmail, etc ...

if i launch kmail for instance:
vxp@csibox:~$ kmail
<unknown program name>(7852)/: Cannot find the D-Bus session server 
vxp@csibox:~$ echo $?
255
vxp@csibox:~$ 



how do I fix this?

---

