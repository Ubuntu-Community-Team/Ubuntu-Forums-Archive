---
title: "Terminal startup question."
date: 2009-06-30
forum: General Help
---

### Post by michy99 on 2009-06-30
Whenever I start a terminal, I get the following:```
declare -x CLASSPATH=":.:.."
declare -x COLORTERM="gnome-terminal"
declare -x DBUS_SESSION_BUS_ADDRESS="unix:abstract=/tmp/dbus-CsssGe57sp,guid=76001719ccf29829118f22014a4a1055"
declare -x DESKTOP_SESSION="default"
declare -x DISPLAY=":0.0"
declare -x GDMSESSION="default"
declare -x GDM_LANG="en_US.UTF-8"
declare -x GDM_XSERVER_LOCATION="local"
declare -x GNOME_DESKTOP_SESSION_ID="this-is-deprecated"
declare -x GNOME_KEYRING_PID="3102"
declare -x GNOME_KEYRING_SOCKET="/tmp/keyring-bR7jwH/socket"
declare -x GPG_AGENT_INFO="/tmp/seahorse-jYZwtV/S.gpg-agent:3275:1"
declare -x GTK_MODULES="canberra-gtk-module"
declare -x GTK_RC_FILES="/etc/gtk/gtkrc:/home/mike/.gtkrc-1.2-gnome2"
declare -x HISTCONTROL="ignoreboth"
declare -x HOME="/home/mike"
declare -x LANG="en_US.UTF-8"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="mike"
declare -x LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:"
declare -x OLDPWD
declare -x ORBIT_SOCKETDIR="/tmp/orbit-mike"
declare -x PATH="/home/mike/bin:/usr/games:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
declare -x PWD="/home/mike"
declare -x SESSION_MANAGER="local/ubuntumike:/tmp/.ICE-unix/3117"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_AGENT_PID="3251"
declare -x SSH_AUTH_SOCK="/tmp/keyring-bR7jwH/socket.ssh"
declare -x TERM="xterm"
declare -x USER="mike"
declare -x USERNAME="mike"
declare -x WINDOWID="52428851"
declare -x WINDOWPATH="7"
declare -x XAUTHORITY="/home/mike/.Xauthority"
declare -x XDG_DATA_DIRS="/usr/local/share/:/usr/share/:/usr/share/gdm/"
declare -x XDG_SESSION_COOKIE="958586ad43e1877ed9cfa8264a1dc83d-1246367827.676340-220587379"
mike@ubuntumike:~$ 
```

I want to go back to the default behavior of just getting the prompt, but I can't figure out what I did to mess it up.

---

### Post by drs305 on 2009-06-30
If the problem is with a bad profile, you can either remove or delete $HOME/.gconf/apps/gnome-terminal, which contains your gnome-terminal profiles. When/if you create a new profile, the folder will be recreated.

---

### Post by michy99 on 2009-06-30
That didn't seem to work, so I guess the problem is somewhere else.

---

### Post by mkrahmeh on 2009-06-30
check the /etc/environment file. to the best of my recollection, the declare -x *var* has to do with adding/replacing environment variables

---

### Post by michy99 on 2009-06-30
The only thing in /etc/environment is```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

---

### Post by mkrahmeh on 2009-07-01
can you post the output of 
```
echo $PATH
```
actually dont know why i want you to do this, but the PATH defined in /etc/environment is different than the one declared in the terminal !!

---

### Post by michy99 on 2009-07-01
```
mike@ubuntumike:~$ echo $PATH
/home/mike/bin:/usr/games:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/jdk1.6.0_13/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/usr/games:/home/mike/bin

```

---

### Post by michy99 on 2009-07-02
Slight bump.

---

### Post by mkrahmeh on 2009-07-02
just wanted to point out the difference, the path declared in terminal at startup is overriding the one defined in your /etc/environment..
sure the declare commands are stored somewhere, please post the output of
```
grep -r /home/mike/bin:/usr/games /etc
```
actually am suspecting some startup script in one of the rc's
 
not sure if this will help, just speculating, so you need to bump harder :)

---

### Post by tarps87 on 2009-07-06
What happens if you press ctrl+alt+F1 and then login? Does the same thing happen?

[SIZE="1"]ps. I think there's a thread killer about[/SIZE]

---

### Post by mkrahmeh on 2009-07-06
> **tarps87 said:**
> [SIZE="1"]ps. I think there's a thread killer about[/SIZE]


sssssssssshhhhh

---

### Post by drs305 on 2009-07-06
1. Does this happen no matter how you start the terminal?  If you make a shortcut to run "gnome-terminal" does it happen? How about "Applications, Accessories, Terminal"?

2. Create a new user. Does it happen to the new user as well? If not, it is something defined in your user settings.

2a. If it's only happening to one user, search your ~/.bash* files (.bashrc, .bash_login, etc) and .profile for the text string "declare -x". You can use the Places > Search for Files > Select more options > to search for text strings in files. You could do a search of your /home folder.
2b. If it happens to all users, check the /root/.bashrc file.

---

### Post by jluxenberg on 2009-07-11
I had the same problem.  For me, there was a line in my ~/.bashrc that amounted to "export".

It was actually this line:
export `bash /usr/share/java-common/jvm-find.sh `

but since that script "jvm-find" doesn't exist, the backticks evaluated to nothing.  The "declare -x ..." stuff is the output of the "export" shell command.

---

