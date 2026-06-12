---
title: "Unable to Mount USB Disk - Not Authorized"
date: 2011-02-24
forum: General Help
---

### Post by user68 on 2011-02-24
I'm using X11 over SSH to remotely access a headless 10.04 PC but cannot access an attached external USB disk. I've done a search and found a solution that works for some but not for me. This is the advice I followed so far:

1. I replaced /etc/X11/Xsession.d/90consolekit with 

CK_GET_X11_DISPLAY_DEVICE=/usr/lib/ConsoleKit/ck-get-x11-display-device
CK_LIST_SESSIONS=/usr/bin/ck-list-sessions
CK_LAUNCH_SESSION=/usr/bin/ck-launch-session

if [ -x "$CK_GET_X11_DISPLAY_DEVICE" -a -x "$CK_LIST_SESSIONS" -a -x "$CK_LAUNCH_SESSION" ] ; then
    if [ "$($CK_LIST_SESSIONS | grep "$($CK_GET_X11_DISPLAY_DEVICE)")" = "" ] ; then
        STARTUP="$CK_LAUNCH_SESSION $STARTUP"
    fi
fi

2. I edited /etc/X11/xinit/xinitrc adding the lines

export XDG_MENU_PREFIX=gnome-
exec ck-launch-session gnome-sessions

These haven't worked for me. Can anyone please suggest any other solutions to try?

---

