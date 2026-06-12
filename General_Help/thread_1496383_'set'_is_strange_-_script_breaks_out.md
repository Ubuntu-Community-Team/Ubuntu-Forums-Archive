---
title: "'set' is strange - script breaks out?"
date: 2010-05-29
forum: General Help
---

### Post by bulwynkl on 2010-05-29
set has very strange output... - first 200 lines

notice at line 81 it goes rather strange - this goes on for another 9000 odd lines and looks like the set script is broken out and cat-ing to the screen - can't prove this as I've not been able to find the set script that is invoked...

any help???

e.g.

uname@Sol:~$ set |head -200
BASH=/bin/bash
BASHOPTS=checkwinsize:cmdhist:expand_aliases:extgl ob:extquote:force_fignore:histappend:interactive_c omments:progcomp:promptvars:sourcepath
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
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-xLgJf4zMVU,guid=a_guid
DEFAULTS_PATH=/usr/share/gconf/gnome.default.path
DESKTOP_SESSION=gnome
DIRSTACK=()
DISPLAY=:0.0
EUID=1000
GDMSESSION=gnome
GDM_KEYBOARD_LAYOUT=$'us\tintl'
GDM_LANG=en_AU.utf8
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
GNOME_KEYRING_CONTROL=/tmp/keyring-RSs6hg
GNOME_KEYRING_PID=1971
GROUPS=()
GTK_MODULES=canberra-gtk-module
HISTCONTROL=ignoredups:ignorespace
HISTFILE=/home/bulwynkl/.bash_history
HISTFILESIZE=2000
HISTSIZE=1000
HOME=/home/username
HOSTNAME=host
HOSTTYPE=x86_64
IFS=$' \t\n'
LANG=en_AU.utf8
LESSCLOSE='/usr/bin/lesspipe %s %s'
LESSOPEN='| /usr/bin/lesspipe %s'
LINES=49
LOGNAME=uname
LS_COLORS='rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;3 3:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40; 31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42 :st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=0 1;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01 ;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz 2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=0 1;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01; 31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31: *.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:* .pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.x bm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.pn g=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx =01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v= 01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01 ;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;3 5:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35: *.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*. gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv= 01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01 ;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;3 6:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36 :*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*. oga=00;36:*.spx=00;36:*.xspf=00;36:'
MACHTYPE=x86_64-pc-linux-gnu
MAILCHECK=60
MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path
OPTERR=1
OPTIND=1
ORBIT_SOCKETDIR=/tmp/orbit-bulwynkl
OSTYPE=linux-gnu
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PIPESTATUS=([0]="0")
PPID=7780
PS1='\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
PS2='> '
PS4='+ '
PWD=/home/bulwynkl
SESSION_MANAGER=local/host:@/tmp/.ICE-unix/1989,unix/Sol:/tmp/.ICE-unix/1989
SHELL=/bin/bash
SHELLOPTS=braceexpand:emacs:hashall:histexpand:his tory:interactive-comments:monitor
SHLVL=1
SPEECHD_PORT=7560
SSH_AGENT_PID=2023
SSH_AUTH_SOCK=/tmp/keyring-RSs6hg/ssh
TERM=xterm
UID=1000
USER=uname
USERNAME=uname
WINDOWID=81788932
WINDOWPATH=7
XAUTHORITY=/var/run/gdm/auth-for-uname-tr3TPV/database
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome:/etc/xdg
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
XDG_SESSION_COOKIE=
_=clear
__pkcon_commandlist=$'\n accept-eula\n get-actions\n get-depends\n get-details\n get-distro-upgrades\n get-files\n get-filters\n get-groups\n get-packages\n download\n get-requires\n get-time\n get-transactions\n get-update-detail\n get-updates\n get-categories\n list-create\n list-diff\n list-install\n install\n install-local\n refresh\n remove\n repo-disable\n repo-enable\n repo-list\n repo-set-data\n resolve\n search\n update\n '
bash205='4.1.5(1)-release'
bash205b='4.1.5(1)-release'
bash3='4.1.5(1)-release'
bash4='4.1.5(1)-release'
_ImageMagick ()
{
local prev;
prev=${COMP_WORDS[COMP_CWORD-1]};
case "$prev" in
-channel)
COMPREPLY=($( compgen -W 'Red Green Blue Opacity \
Matte Cyan Magenta Yellow Black' -- "$cur" ));
return 0
;;
-colormap)
COMPREPLY=($( compgen -W 'shared private' -- "$cur" ));
return 0
;;
-colorspace)
COMPREPLY=($( compgen -W 'GRAY OHTA RGB Transparent \
XYZ YCbCr YIQ YPbPr YUV CMYK' -- "$cur" ));
return 0
;;
-compose)
COMPREPLY=($( compgen -W 'Over In Out Atop Xor Plus \
Minus Add Subtract Difference Multiply Bumpmap\
Copy CopyRed CopyGreen CopyBlue CopyOpacity' -- "$cur" ));
return 0
;;
-compress)
COMPREPLY=($( compgen -W 'None BZip Fax Group4 JPEG \
Lossless LZW RLE Zip' -- "$cur" ));
return 0
;;
-dispose)
COMPREPLY=($( compgen -W 'Undefined None Background Previous' -- "$cur" ));
return 0
;;
-encoding)
COMPREPLY=($( compgen -W 'AdobeCustom AdobeExpert \
AdobeStandard AppleRoman BIG5 GB2312 Latin2 \
None SJIScode Symbol Unicode Wansung' -- "$cur"));
return 0
;;
-endian)
COMPREPLY=($( compgen -W 'MSB LSB' -- "$cur" ));
return 0
;;
-filter)
COMPREPLY=($( compgen -W 'Point Box Triangle Hermite \
Hanning Hamming Blackman Gaussian Quadratic \
Cubic Catrom Mitchell Lanczos Bessel Sinc' -- "$cur" ));
return 0
;;
-format)
COMPREPLY=($( compgen -W "$( convert -list format | awk '/ [r-][w-][+-] / {print $1}' | tr -d '*' | tr [:upper:] [:lower:] )" -- "$cur" ));
return 0
;;
-gravity)
COMPREPLY=($( compgen -W 'Northwest North NorthEast \
West Center East SouthWest South SouthEast' -- "$cur" ));
return 0
;;
-intent)
COMPREPLY=($( compgen -W 'Absolute Perceptual \
Relative Saturation' -- "$cur" ));
return 0
;;
-interlace)
COMPREPLY=($( compgen -W 'None Line Plane Partition' -- "$cur" ));
return 0
;;
-limit)
COMPREPLY=($( compgen -W 'Disk File Map Memory' -- "$cur" ));
return 0
;;
-list)
COMPREPLY=($( compgen -W 'Delegate Format Magic Module Resource \
Type' -- "$cur" ));
return 0
;;
-map)
COMPREPLY=($( compgen -W 'best default gray red green blue' -- "$cur" ));
_filedir;
return 0
;;
-noise)
COMPREPLY=($( compgen -W 'Uniform Gaussian Multiplicative \
Impulse Laplacian Poisson' -- "$cur" ));
return 0
;;
-preview)
COMPREPLY=($( compgen -W 'Rotate Shear Roll Hue \
Saturation Brightness Gamma Spiff \
Dull Grayscale Quantize Despeckle \
ReduceNoise AddNoise Sharpen Blur \
Treshold EdgeDetect Spread Shade \
Raise Segment Solarize Swirl Implode \
Wave OilPaint CharcoalDrawing JPEG' -- "$cur" ));
return 0
;;
-@(mask|profile|texture|tile|write))
_filedir;
return 0
;;
-type)
COMPREPLY=($( compgen -W 'Bilevel Grayscale Palette PaletteMatte \
TrueColor TrueColorMatte ColorSeparation ColorSeparationlMatte \
Optimize' -- "$cur" ));
return 0
;;
-units)
COMPREPLY=($( compgen -W 'Undefined PixelsPerInch \
PixelsPerCentimeter' -- "$cur" ));
return 0
;;
-virtual-pixel)
COMPREPLY=($( compgen -W 'Constant Edge mirror tile' -- "$cur" ));
return 0
;;
-visual)
COMPREPLY=($( compgen -W 'StaticGray GrayScale StaticColor \
PseudoColor TrueColor DirectColor defaut visualid' -- "$cur" ));
return 0
bash: set: write error: Broken pipe

---

### Post by sisco311 on 2010-05-29
There is nothing wrong with the output. It prints out the functions used by bash-completion.

---

