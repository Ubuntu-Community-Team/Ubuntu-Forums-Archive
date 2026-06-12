---
title: "Environment variables."
date: 2010-06-05
forum: General Help
---

### Post by rickierich on 2010-06-05
I have changed my java home environment variable

JAVA_HOME=/usr/lib/jvm/java-6-sun

this is the correct line. but when I run an ant file it is giving me this as my environment line

Perhaps JAVA_HOME does not point to the JDK.
It is currently set to "/usr/lib/jvm/java-6-openjdk/jre"


env output
========================

ORBIT_SOCKETDIR=/tmp/orbit-myusername
GPG_AGENT_INFO=/tmp/seahorse-BNVXql/S.gpg-agent:1595:1
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=c9b98b5d4bd4c00dc9e794ab4a36458c-1275775855.276279-1347583314
WINDOWID=67108868
GNOME_KEYRING_CONTROL=/tmp/keyring-a8bDjn
GTK_MODULES=canberra-gtk-module
USER=myusername
LS_COLORS=rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
SSH_AUTH_SOCK=/tmp/keyring-a8bDjn/ssh
SESSION_MANAGER=local/myusername-laptop:@/tmp/.ICE-unix/1551,unix/myusername-laptop:/tmp/.ICE-unix/1551
USERNAME=myusername
DEFAULTS_PATH=/usr/share/gconf/gnome.default.path
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome:/etc/xdg
DESKTOP_SESSION=gnome
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/myusername/microemulator/microemu-android
JAVA_HOME=/usr/lib/jvm/java-6-sun
GDM_KEYBOARD_LAYOUT=gb
LANG=en_GB.utf8
GNOME_KEYRING_PID=1533
MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path
GDM_LANG=en_GB.utf8
GDMSESSION=gnome
HISTCONTROL=ignoreboth
SPEECHD_PORT=7560
SHLVL=1
HOME=/home/myusername
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=myusername
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-JP7HhJMmil,guid=5335f4ce7d3f32697b29059c4c0acb6f
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
XAUTHORITY=/var/run/gdm/auth-for-myusername-NioxRw/database
COLORTERM=gnome-terminal
_=/usr/bin/env


ant output
=============

clean:
   [delete] Deleting directory /home/myusername/microemulator/microemu-android/bin

BUILD FAILED
/home/myusername/microemulator/microemu-android/build.xml:64: Unable to delete directory /home/myusername/microemulator/microemu-android/bin

Total time: 0 seconds
myusername@myusername-laptop:~/microemulator/microemu-android$ sudo ant
[sudo] password for myusername: 
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-openjdk/lib/tools.jar
Buildfile: build.xml

clean:
   [delete] Deleting directory /home/myusername/microemulator/microemu-android/bin

check:

dirs:
    [mkdir] Created dir: /home/myusername/microemulator/microemu-android/bin
    [mkdir] Created dir: /home/myusername/microemulator/microemu-android/bin/assets
    [mkdir] Created dir: /home/myusername/microemulator/microemu-android/bin/classes
    [mkdir] Created dir: /home/myusername/microemulator/microemu-android/bin/producer
    [mkdir] Created dir: /home/myusername/microemulator/microemu-android/bin/res
    [mkdir] Created dir: /home/myusername/microemulator/microemu-android/bin/libs

compile-producer:
    [javac] Compiling 2 source files to /home/myusername/microemulator/microemu-android/bin/producer

BUILD FAILED
/home/myusername/microemulator/microemu-android/build.xml:94: Unable to find a javac compiler;
com.sun.tools.javac.Main is not on the classpath.
Perhaps JAVA_HOME does not point to the JDK.
It is currently set to "/usr/lib/jvm/java-6-openjdk/jre"

Total time: 0 seconds

---

