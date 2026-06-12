---
title: "Runaway processes"
date: 2009-08-04
forum: General Help
---

### Post by sam_uk on 2009-08-04
Hi all

I was using intrepid until recently. I did a fair bit of hacking about in a amateurish kind of way and at one stage set up apache and some web apps called opentaps.

I did something wrong and everytime I open a terminal it says this;

declare -x ANT_HOME="/usr/share/ant"
declare -x CATALINA_BASE="/var/lib/tomcat5.5"
declare -x CATALINA_HOME="/usr/share/tomcat5.5"
declare -x CATALINA_OPTS="-server -Xms384M -Xmx512M -XX:MaxPermSize=256M"
declare -x COLORTERM="gnome-terminal"
declare -x DBUS_SESSION_BUS_ADDRESS="unix:abstract=/tmp/dbus-1P3p0R3EWA,guid=7a2882269bef85d276b1e3724a789a38"
declare -x DESKTOP_SESSION="GDM_Failsafe.GNOME"
declare -x DISPLAY=":0.0"
declare -x GDMSESSION="GDM_Failsafe.GNOME"
declare -x GDM_LANG="en_GB.UTF-8"
declare -x GDM_XSERVER_LOCATION="local"
declare -x GNOME_DESKTOP_SESSION_ID="this-is-deprecated"
declare -x GNOME_KEYRING_PID="3682"
declare -x GNOME_KEYRING_SOCKET="/tmp/keyring-0E53HJ/socket"
declare -x GTK_RC_FILES="/etc/gtk/gtkrc:/home/user/.gtkrc-1.2-gnome2"
declare -x HISTCONTROL="ignoreboth"
declare -x HOME="/home/user"
declare -x JAVA_HOME="/usr/lib/j2sdk1.5-sun/"
declare -x LANG="en_GB.UTF-8"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="user"
declare -x LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:"
declare -x OLDPWD
declare -x ORBIT_SOCKETDIR="/tmp/orbit-user"
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
declare -x PWD="/home/user"
declare -x SESSION_MANAGER="local/laptop:/tmp/.ICE-unix/3695"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_AUTH_SOCK="/tmp/keyring-0E53HJ/socket.ssh"
declare -x TERM="xterm"
declare -x USER="user"
declare -x USERNAME="user"
declare -x WINDOWID="50334194"
declare -x WINDOWPATH="7"
declare -x XAUTHORITY="/tmp/.gdmVFDVXU"
declare -x XDG_DATA_DIRS="/usr/local/share/:/usr/share/:/usr/share/gdm/"
declare -x XDG_SESSION_COOKIE="814989b18cf60054326002ba486f74a8-1249417780.648115-1717898560"


There is more at the top but I do not know how to cut'n paste that.



My laptop is becoming increasingly erratic and tends to get a runaway process after about 30 mins use.

So I upgraded to Jaunty and hoped that a new kernel, new gnome etc would fix it. 

It hasn't I still get a runaway process every 10 - 30 mins. 

It seems to be related to the Xserver as that usually locks up and I have to hard reboot.

Any ideas? is it a complete re-install job?

Thanks

Sam

---

### Post by sam_uk on 2009-08-05
bump

---

### Post by sam_uk on 2009-08-18
Anyone care to venture an opinion?

Thanks

Sam

---

