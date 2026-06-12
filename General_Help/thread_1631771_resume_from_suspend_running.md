---
title: "resume from suspend running"
date: 2010-11-27
forum: General Help
---

### Post by yanf.jiang on 2010-11-27
I am pretty new with linux. Now I am trying to disable my wireless card when it boots up. I found that I can add a new application in the <preference<startup with the following command: (I have no idea what it means, but it works)

dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:false

however, every time when the system resumes from suspend, the wireless card is back on. I know that I can write a scipt and put it in the etc/pm/sleep.d to solve this problem, but I don't know how to write it. anyone can help out with that? I really appreciate it.

---

### Post by yanf.jiang on 2010-11-27
I just figure it out,

I have change another file: /usr/lib/pm-utils/sleep.d/55NetworkManger

put the command after resume_nm() like:

case "$1" in
    hibernate|suspend)
        suspend_nm
        ;;
    thaw|resume)
        resume_nm
        dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set  string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:false
        ;;
    *) exit $NA
        ;;
esac



I guess I can put it in the resume_nm function too, I guess it woundn't be different

---

### Post by gradinaruvasile on 2010-11-27
I dont know the exact specifics of pm utils, but a "man pm-utils" in a terminal should enlighten you. It has the locations of scripts, maning conventions etc (google up the rest).

Generally speaking a script is a text file that contains a command or more commands.
Entering a few consecutive commands, each in a new line and calling (executing) the script will execute the commands in order.
The first line should contain the

#!/bin/bash

line. After that, the commands that you want to execute.
Edit the file in a text editor and save it on the desired location and name.
Saving in other than /home and its subfolders or /tmp generally will need root rights (sudo). So you have to execute the text editor with sudo like this:

in a terminal (both graphical or text mode) or in the alt+f2 box (only graphical text editors) enter:

sudo editorname

for terminal/text mode

or gksudo editorname

for gui mode (alt+f2 box)

where editorname is gedit (default gnome text editor), nano (default text mode text editor) etc (the editor of your choice's executable name).
After saving the file, you must make it executable with:

chmod +x filename-with-full-path

where filename-with-full-path is the file name you saved with full path. If the file is in a system area (such as /etc) you have to precede the command with sudo.
This ideally is done from terminal, otherwise you have to launch some file manager with sudo/gksudo, browse to the file, right click on it and tick the executable box.

Also, the wireless (and bluetooth also) can be turned on/off with the rfkill command - this state will be saved across the whole session (until reboot/shutdown for good that is) - resuming/suspending will have this state saved and applied on resume.

rfkill --help 

in a terminal is enough for its syntax, it has a clear and extremely simple syntax.

Network-manager on the other hand will lose the applied setting after resume.

Edit: you posted quicker than me. At least try the rfkill part, it is more efficient than the network manager route.

---

### Post by yanf.jiang on 2010-11-27
thanks a lot for these information, really help me to improve

---

