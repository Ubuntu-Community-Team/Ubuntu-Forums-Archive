---
title: "Matlab desktop (JVM) won't open"
date: 2010-10-28
forum: General Help
---

### Post by martron88 on 2010-10-28
I'm suddenly having an odd problem after running Matlab successfully on my 10.10 system for a while.

When I try to open Matlab now with 
```
matlab -glnx86 -desktop
```

matlab only opens in console mode and doesn't load the jvm desktop.  It doesn't report any errors. The command
```
version('-java');
```
gives no response.

If I try to run a command in the console such as plot, I get the following warning:
```
Warning: This functionality is no longer supported under the -nojvm startup option
```

So, matlab is somehow starting with the -nojvm option even though I'm explicitly telling it not to with the -desktop flag.  I don't know how this has suddenly changed today.  When I first set Matlab up on Maverick a few weeks ago I followed [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB) to get the java stuff working properly.  

Does anyone have ideas on where -nojvm might be implicitly set or log files I can access to give me more info on why this might be happening?

Thanks

---

### Post by martron88 on 2010-10-28
In case it helps, here's what the console looks like:


```
martron@freyja:~$ /home/martron/programs/Matlab/bin/matlab -glnx86 -desktop
 
  To get started, type one of these: helpwin, helpdesk, or demo.
  For product information, visit www.mathworks.com.
 

  Student License -- for use in conjunction with courses offered at a 
  degree-granting institution.  Professional and commercial use prohibited.

EDU>> mm_preload
EDU>> plot(l);
Warning: This functionality is no longer supported under the -nojvm startup option. For more information, see "Changes to -nojvm Startup Option" in the MATLAB Release Notes. To view the release note in your system browser, run
web('http://www.mathworks.com/access/helpdesk/help/techdoc/rn/bropbi9-1.html#brubkzc-1', '-browser') 
> In gcf at 33
  In newplot at 70
EDU>> 
```

---

### Post by martron88 on 2010-10-28
More info:

```
martron@freyja:~$ /home/martron/programs/Matlab/bin/matlab -glnx86 -e
ARCH=glnx86
LESSOPEN=| /usr/bin/lesspipe %s
GDM_KEYBOARD_LAYOUT=us
HISTFILESIZE=6000
USER=martron
SSH_AGENT_PID=1254
SHLVL=1
LD_LIBRARY_PATH=/home/martron/programs/Matlab/sys/os/glnx86:/home/martron/programs/Matlab/bin/glnx86:/home/martron/programs/Matlab/extern/lib/glnx86:/usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib:/lib
ORBIT_SOCKETDIR=/tmp/orbit-martron
BASEMATLABPATH=
XKEYSYMDB=/home/martron/programs/Matlab/X11/app-defaults/XKeysymDB
AUTOMOUNT_MAP=
OLDPWD=/home/martron/programs/Matlab
HOME=/home/martron
DESKTOP_SESSION=gnome
XDG_SESSION_COOKIE=7899ab9939732028c2ae2f2f4cb50695-1288283804.476738-1975066691
GTK_MODULES=canberra-gtk-module
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-gn6kBZEnGO,guid=0192f18b1c585ed3e677104b4cc9a69c
GNOME_KEYRING_CONTROL=/tmp/keyring-ufiRuF
MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path
LOGNAME=martron
MATLABPATH=/home/martron/programs/Matlab/toolbox/local
_=/home/martron/programs/Matlab/bin/matlab
DESKTOP_AUTOSTART_ID=104a71fd74b8900784128828380525794400000012200000
DEFAULTS_PATH=/usr/share/gconf/gnome.default.path
USERNAME=martron
TERM=xterm
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
HISTCONTROL=ignoreboth
GDM_LANG=en_CA.utf8
SESSION_MANAGER=local/freyja:@/tmp/.ICE-unix/1220,unix/freyja:/tmp/.ICE-unix/1220
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/martron/scripts
TOOLBOX=/home/martron/programs/Matlab/toolbox
DISPLAY=:0.0
LANG=en_CA.utf8
XAUTHORITY=/var/run/gdm/auth-for-martron-33isSQ/database
LS_COLORS=rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
SSH_AUTH_SOCK=/tmp/keyring-ufiRuF/ssh
XFILESEARCHPATH=/usr/lib/jvm/java-6-openjdk/jre/lib/locale/%L/%T/%N%S:
MATLAB=/home/martron/programs/Matlab
SHELL=/bin/bash
GDMSESSION=gnome
LESSCLOSE=/usr/bin/lesspipe %s %s
OSG_LD_LIBRARY_PATH=/home/martron/programs/Matlab/sys/openscenegraph/lib/glnx86
XAPPLRESDIR=/home/martron/programs/Matlab/X11/app-defaults
SPEECHD_PORT=7560
JAVA_HOME=/usr/lib/jvm/java-6-openjdk
PWD=/home/martron
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome:/etc/xdg
HTML_TIDY=/home/martron/tidyConfig.conf

```

---

### Post by thameera on 2010-10-29
Are you sure that sun java is installed in your system? 10.10 doesn't have it in your repositories. Try adding the following sources and install it.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

---

### Post by martron88 on 2010-10-30
> **thameera said:**
> Are you sure that sun java is installed in your system? 10.10 doesn't have it in your repositories. Try adding the following sources and install it.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

It had been working for me with openjdk installed but I did try sun java to try and troubleshoot this problem.  It made no difference. I'm reinstalling matlab now to see if maybe that can solve my problems.

---

### Post by martron88 on 2010-10-30
> **martron88 said:**
> I'm reinstalling matlab now to see if maybe that can solve my problems.

Well reinstalling has fixed the problem though I'm not really sure what caused it in the first place.

---

