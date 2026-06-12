---
title: "On new install of Lynx, find constantly runs and uses much cpu"
date: 2010-05-26
forum: General Help
---

### Post by bobdobbs on 2010-05-26
Hi all.

I recently upgraded from 9.10 to Lynx.

The upgrade was not totally smooth, but I got there in the end.

However, much of the time, much of my cpu is being used by 'find' running from root.

I notice this because I can hear a hd writing, and my operations on my computer are slow or jittery. So I run 'top', and see that find is running near the top of the table.

I kill it. But eventually a cpu hungry 'find' process from root will start running again.

What could be happening here?

---

### Post by andrewc6l on 2010-05-26
It could be a problem with the locate command (and in particular with the database it builds using updatedb). Here's some doc:

[http://www.devdaily.com/blog/post/linux-unix/use-linux-locate-command](http://www.devdaily.com/blog/post/linux-unix/use-linux-locate-command)
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

If you regularly boot up your machine, use it for a while, then shut it down - you might be getting a locate database being built every time. If you leave the machine on, it's possible that the locate database is set to build with a high enough frequency that the file system can't keep up. Or maybe there's something that causes the build to crash.

I know on some Linuxes, updatedb is run by /etc/cron.weekly/slocate (or /etc/cron.daily/slocate) - I can't remember if Ubuntu puts it there or not.

---

### Post by bobdobbs on 2010-05-26
I don't reboot all that often.
I generally leave my computer running days at time.

---

### Post by andrewc6l on 2010-06-03
You might be able to get a little more information about what is running the find using the following commands:

```

ps -eo pid,args | grep find
ps axe | grep find

```

They will tell you the full command line and the environment used for the find. (Be careful you aren't looking at the 'grep find' that you run as part of the command :-) )

---

### Post by bobdobbs on 2010-06-03
Hi Andrew.

Interesting results. Pasted below.

Looks like an application is trying to catalogue my media.
Might be related to mpd perhaps?

```
ps axe | grep find
22031 ?        D      0:03 find . -type f -iname *.mp3 -o -iname *.oga -o -iname *.ogg -o -iname *.wav -o -iname *.flac HOME=/root OLDPWD=/root LOGNAME=root PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin SHELL=/bin/sh PWD=/
```


```
ps axe | grep find
22031 ?        D      0:03 find . -type f -iname *.mp3 -o -iname *.oga -o -iname *.ogg -o -iname *.wav -o -iname *.flac HOME=/root OLDPWD=/root LOGNAME=root PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin SHELL=/bin/sh PWD=/
22040 pts/0    S+     0:00 grep find ORBIT_SOCKETDIR=/tmp/orbit-mantis SSH_AGENT_PID=1799 SHELL=/bin/bash TERM=xterm XDG_SESSION_COOKIE=095d8c458d8b2348633d54ba4aeecaaf-1275491853.198541-1055781394 WINDOWID=67121372 GNOME_KEYRING_CONTROL=/tmp/keyring-s9PBkR GTK_MODULES=canberra-gtk-module MATTM=/var/www/hosts/mattm USER=root LS_COLORS=rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36: SSH_AUTH_SOCK=/tmp/keyring-s9PBkR/ssh USERNAME=mantis SESSION_MANAGER=local/faustina:@/tmp/.ICE-unix/1727,unix/faustina:/tmp/.ICE-unix/1727 DEFAULTS_PATH=/usr/share/gconf/gnome.default.path CLOJURE_EXT=/home/mantis/.clojure XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome:/usr/share/ubuntustudio-menu/:/etc/xdg/ ZICI=/var/www/hosts/zici-test MAIL=/var/mail/root PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games DESKTOP_SESSION=gnome PWD=/var/www/hosts/test2 GDM_KEYBOARD_LAYOUT=us LANG=en_NZ.UTF-8 GDM_LANG=en_NZ.UTF-8 MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path HD2=/media/ HD3=/media/ GDMSESSION=gnome HISTCONTROL=ignoreboth SPEECHD_PORT=7560 HOME=/root SHLVL=2 BK=/media/HD2/sunil_bk/mantispalm GNOME_DESKTOP_SESSION_ID=this-is-deprecated MUSIC=/media/sdb1/shared/Music LOGNAME=root PYTHONPATH=/usr/lib/python2.5/site-packages DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-EUcFpXGLv2,guid=f20bb5d44dd2de0000c5b3c34bfda510 XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/ LESSOPEN=| /usr/bin/lesspipe %s DISPLAY=:0.0 LESSCLOSE=/usr/bin/lesspipe %s %s COLORTERM=gnome-terminal XAUTHORITY=/var/run/gdm/auth-for-mantis-CgGGzw/database _=/bin/grep
```

---

### Post by andrewc6l on 2010-06-07
That appears to be running as root, so it's probably being done either somewhere in /etc or from a setuid program. I don't have 10.04 installed, so I can't say for sure. Hopefully it's a script. Try the following:
```

sudo sh
find /etc -name \* -print | xargs grep mp3 | grep find > /tmp/findresults
find /home/(user you log in as) -name \* -print | xargs grep mp3 | grep find >> /tmp/findresults
exit
cat /tmp/findresults

```

where (user you log in as) is replaced with your regular username. Maybe that will show something worthwhile.

---

### Post by bobdobbs on 2010-06-08
> **andrewc6l said:**
> That appears to be running as root, so it's probably being done either somewhere in /etc or from a setuid program. I don't have 10.04 installed, so I can't say for sure. Hopefully it's a script. Try the following:
```

sudo sh
find /etc -name \* -print | xargs grep mp3 | grep find > /tmp/findresults
find /home/(user you log in as) -name \* -print | xargs grep mp3 | grep find >> /tmp/findresults
exit
cat /tmp/findresults

```

where (user you log in as) is replaced with your regular username. Maybe that will show something worthwhile.

Hi Andrew.

The first command revealed existence of a chron job that runs every hour, and related to something called "musica".
It'd be good if this job was nice'd.
I might find out out what this musica thing is, and file a bug with the developers.

Thanks for your help.

---

### Post by andrewc6l on 2010-06-09
If you don't use it, you can probably remove it:

[http://packages.ubuntu.com/lucid/musica](http://packages.ubuntu.com/lucid/musica)

(and there's a link there to the homepage / place to report defects as well.)

---

### Post by bobdobbs on 2010-06-09
> **andrewc6l said:**
> If you don't use it, you can probably remove it:

[http://packages.ubuntu.com/lucid/musica](http://packages.ubuntu.com/lucid/musica)

(and there's a link there to the homepage / place to report defects as well.)

Thanks Andrew.
For some reason I didn't actually think of removing it.
I've taken it out now.

I usually use mpd for managing and listening to music.
Because it's a daemon, I can control my stereo from anywhere in my house with my iphone, or from my bed with my laptop :)

---

