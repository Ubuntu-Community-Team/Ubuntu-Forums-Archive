---
title: "locales in jaunty."
date: 2011-09-30
forum: General Help
---

### Post by marcpons on 2011-09-30
Hi, I've got a ubuntu Jaunty version and got problems with UTF-8 code characters, I try export the hierarchy locale environment  variable (LC_ALL) by export without success. I think maybe another service over the system causes itself ignore the LC_ALL variable. There are these initscripts services running on my system:

/etc/rc2.d/S01policykit           /etc/rc2.d/S20hotkey-setup           /etc/rc2.d/S70bootlogs.sh
/etc/rc2.d/S10acpid               /etc/rc2.d/S20samba                  /etc/rc2.d/S70dns-clean
/etc/rc2.d/S10apmd                /etc/rc2.d/S20vboxdrv                /etc/rc2.d/S70pppd-dns
/etc/rc2.d/S10sysklogd            /etc/rc2.d/S20winbind                /etc/rc2.d/S89anacron
/etc/rc2.d/S11klogd               /etc/rc2.d/S24hal                    /etc/rc2.d/S89atd
/etc/rc2.d/S12dbus                /etc/rc2.d/S25bluetooth              /etc/rc2.d/S89cron
/etc/rc2.d/S16openvpn             /etc/rc2.d/S30gdm                    /etc/rc2.d/S90binfmt-support
/etc/rc2.d/S16ssh                 /etc/rc2.d/S50avahi-daemon           /etc/rc2.d/S98usplash
/etc/rc2.d/S17mysql-ndb-mgm       /etc/rc2.d/S50cups                   /etc/rc2.d/S99acpi-support
/etc/rc2.d/S18mysql-ndb           /etc/rc2.d/S50NetworkManager         /etc/rc2.d/S99laptop-mode
/etc/rc2.d/S19mysql               /etc/rc2.d/S50pulseaudio             /etc/rc2.d/S99ondemand
/etc/rc2.d/S19vmware              /etc/rc2.d/S50rsync                  /etc/rc2.d/S99rc.local
/etc/rc2.d/S20apport              /etc/rc2.d/S50saned                  /etc/rc2.d/S99rmnologin
/etc/rc2.d/S20dkms_autoinstaller  /etc/rc2.d/S50system-tools-backends  /etc/rc2.d/S99stop-readahead

For other way I edited and update (source command) the LC_ALL variable in these files with same results:

/etc/environment	LC_ALL=es_ES.UTF-8
/etc/defaults/locales	LC_ALL=es_ES.UTF-8
/etc/bash.bashrc	export LC_ALL=es_ES.UTF-8

also I tried with:
dpkg-reconfigure locales (display all locales in status up-to-date)
dpkg-reconfigure console-setup

no success. When I type locale, the stdrout display me correctly the variables:

HOME=/root
LANG=es_ES@euro
LANGUAGE=es_ES@euro
LC_ALL=es_ES@euro
LC_CTYPE=es_ES
LC_TYPE=es_ES@euro
LESSCLOSE=/usr/bin/lesspipe %s %s
LESSOPEN=| /usr/bin/lesspipe %s
LOGNAME=root
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
MAIL=/var/mail/root
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
PWD=/root
SHELL=/bin/bash
SHLVL=1
TERM=xterm
USER=root
_=/usr/bin/env
XDG_SESSION_COOKIE=5f0dad7dc468444af6951b374a9fd12a-1317283429.49828-531925320

Authentication by kerberos on a windows domain controller, do you think is this significant?. 

Thank you very much.

---

### Post by mörgæs on 2011-09-30
Hi, welcome to the fora.

9.04 has been unsupported for long time:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

I would recommend a fresh install of one of the new releases. After that we can take a look at locales, if it is still a problem.

---

