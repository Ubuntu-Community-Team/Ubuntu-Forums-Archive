---
title: "Binary Files - odd problem"
date: 2010-11-17
forum: General Help
---

### Post by john1923 on 2010-11-17
I use Ubuntu 10.04, 64bit

I can run a binary file when I drag it into the terminal, creating a line like this.

> '/home/john/mira_3.2.1rc2_prod_linux-gnu_x86_64_static/bin/mira' I cannot run the binary file if I navigate to the directory containing the binary file (mira) and type mira, or 'mira'. Nor does it work if I add the directory /home/john/mira_3.2.1rc2_prod_linux-gnu_x86_64_static/bin/ to my PATH.

Any ideas?

The binary file that I am using is the mira genome assembler, which is distributed as a set of pre-compiled binary files, however this problem happens on my computer with any binary file.

mira can be found here
[http://sourceforge.net/projects/mira-assembler/files/](http://sourceforge.net/projects/mira-assembler/files/)

Technicaly I can make the program work, but I would rather type mira than '/home/john/mira_3.2.1rc2_prod_linux-gnu_x86_64_static/bin/mira' every time I want to run it.

Thankyou for your help

---

### Post by J&#7885;hn on 2010-11-17
If you navigate to the folder containing mira and type

./mira

Does that run?

Also, please type 'set' and paste here the path line.

---

### Post by john1923 on 2010-11-17
./mira does work.

Typing set gives a very long response.  typing 

> echo $PATH gives > /home/john/home/john/mira_3.2.1rc2_prod_linux-gnu_x86_64_static/bin:”/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games”After posting this question I copied all of the binaries into > /usr/local/binnow mira works as it should. Ie I type mira into any terminal and it runs normally.

Do you know why?

---

### Post by john1923 on 2010-11-17
Here is the useful bit of the set output

> BASH=/bin/bash
BASHOPTS=checkwinsize:cmdhist:expand_aliases:extglob:extquote:force_fignore:histappend:interactive_comments:progcomp:promptvars:sourcepath
BASH_ALIASES=()
BASH_ARGC=()
BASH_ARGV=()
BASH_CMDS=()
BASH_COMPLETION=/etc/bash_completion
BASH_COMPLETION_COMPAT_DIR=/etc/bash_completion.d
BASH_COMPLETION_DIR=/etc/bash_completion.d
BASH_LINENO=()
BASH_SOURCE=()
BASH_VERSINFO=([0]="4" [1]="1" [2]="5" [3]="1" [4]="release" [5]="x86_64-pc-linux-gnu")
BASH_VERSION='4.1.5(1)-release'
COLORTERM=gnome-terminal
COLUMNS=80
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-db2AZM218A,guid=6df9dc185e5a28b62f3e5f284cc7dcbd
DEFAULTS_PATH=/usr/share/gconf/gnome.default.path
DESKTOP_SESSION=gnome
DIRSTACK=()
DISPLAY=:0.0
EUID=1000
GDMSESSION=gnome
GDM_KEYBOARD_LAYOUT=gb
GDM_LANG=en_GB.utf8
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
GNOME_KEYRING_CONTROL=/tmp/keyring-4uDvU2
GNOME_KEYRING_PID=1602
GROUPS=()
GTK_MODULES=canberra-gtk-module
HISTCONTROL=ignoredups:ignorespace
HISTFILE=/home/john/.bash_history
HISTFILESIZE=2000
HISTSIZE=1000
HOME=/home/john
HOSTNAME=john-desktop
HOSTTYPE=x86_64
IFS=$' \t\n'
LANG=en_GB.utf8
LESSCLOSE='/usr/bin/lesspipe %s %s'
LESSOPEN='| /usr/bin/lesspipe %s'
LINES=24
LOGNAME=john
LS_COLORS='rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:'
MACHTYPE=x86_64-pc-linux-gnu
MAILCHECK=60
MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path
OLDPWD=/home/john/mira_3.2.1rc2_prod_linux-gnu_x86_64_static/bin
OPTERR=1
OPTIND=1
ORBIT_SOCKETDIR=/tmp/orbit-john
OSTYPE=linux-gnu
PATH=$'/home/john/home/john/mira_3.2.1rc2_prod_linux-gnu_x86_64_static/bin:\342\200\235/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games\342\200\235'
PIPESTATUS=([0]="2")
PPID=17969
PS1='\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
PS2='> '
PS4='+ '
PWD='/home/john/Downloads/mira_3.2.1rc2_prod_linux-gnu_x86_64_static (2)/bin'
SESSION_MANAGER=local/john-desktop:@/tmp/.ICE-unix/1620,unix/john-desktop:/tmp/.ICE-unix/1620
SHELL=/bin/bash
SHELLOPTS=braceexpand:emacs:hashall:histexpand:history:interactive-comments:monitor
SHLVL=1
SPEECHD_PORT=7560
SSH_AGENT_PID=1654
SSH_AUTH_SOCK=/tmp/keyring-4uDvU2/ssh
TERM=xterm
UID=1000
USER=john
USERNAME=john
WINDOWID=117691254
XAUTHORITY=/var/run/gdm/auth-for-john-QcTIjX/database
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome:/etc/xdg
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
XDG_SESSION_COOKIE=810b4e809719d19170b446074c24d061-1288166588.826854-501066509
_=--help
__pkcon_commandlist=$'\n    accept-eula\n    get-actions\n    get-depends\n    get-details\n    get-distro-upgrades\n    get-files\n    get-filters\n    get-groups\n    get-packages\n    download\n    get-requires\n    get-time\n    get-transactions\n    get-update-detail\n    get-updates\n    get-categories\n    list-create\n    list-diff\n    list-install\n    install\n    install-local\n    refresh\n    remove\n    repo-disable\n    repo-enable\n    repo-list\n    repo-set-data\n    resolve\n    search\n    update\n    '
bash205='4.1.5(1)-release'
bash205b='4.1.5(1)-release'
bash3='4.1.5(1)-release'
bash4='4.1.5(1)-release'
_ImageMagick () Image Magick puts another 6542 lines onto the end of this output

---

### Post by J&#7885;hn on 2010-11-17
Oops I should've said

set |grep PATH

That path line looks a bit of a mess. Have you set it permanently? If not, I'd edit .bash_profile in your home directory, and add a line like this to the end, then log out and back in.

  export PATH=$PATH:/home/john/Downloads/mira_3.2.1rc2_prod_linux-gnu_x86_64_static/bin

---

### Post by john1923 on 2010-11-17
I copied the binaries into usr/local/bin and that made everything work, now I have the small problem of working out how to use mira. but that is a different problem entirely.

Thank you for your help

---

