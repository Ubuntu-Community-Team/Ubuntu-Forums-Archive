---
title: "Changing the colors BASH uses to display permissions"
date: 2009-11-04
forum: General Help
---

### Post by Curtis.Everingham on 2009-11-04
I use terminal/SSH on my macbook to manage my 9.04 Ubuntu server. I've noticed when listing directories, ubuntu uses colors to denote permissions, filetypes, etc. I was wondering if/how I can customize the colors it uses to display such things. I am mostly new to ubuntu, and somewhat new to using Bash. Any help would be greatly appreciated.

---

### Post by Curtis.Everingham on 2009-11-04
After searching around a bit, I pulled up an example ~/.bashrc file. I searched through it a bit, and found this line:

alias ls='ls --color=auto

removing that entry from the ~/.bashrc file on my computer gets rid of the colors completely, so that is the entry I want to be editing. If anyone knows how to edit this in a way that customized the colors displayed, any advice would be much appreciated. Thanks in advance

---

### Post by todak on 2009-11-04
Look at [this page]("http://www.systhread.net/texts/200703bashish.php") and see if it has the information you seek.

---

### Post by Curtis.Everingham on 2009-11-04
Thank you! a page like that was exactly what I needed. for anyone looking for this answer in the future who might come across this thread, this is the section of that page that tells you what you need:

File Colors

Colors in the shell are controlled by codes. Files and the prompt can be colorized, however, they are done differently. Files are colored by using ls --color which can be aliased as ls=`ls --color'. The default location of file color schemes varies from system to system. To use individual colors first build a file (or copy the default one) and put it in $HOME/.dir_colors. Following is an example dircolors file:

COLOR tty
OPTIONS -F -T 0
# Below, there should be one TERM entry for each termtype that is colorizable
TERM linux
TERM console
TERM con132x25
TERM con132x30
TERM con132x43
TERM con132x60
TERM con80x25
TERM con80x28
TERM con80x30
TERM con80x43
TERM con80x50
TERM con80x60
TERM cons25
TERM xterm
TERM rxvt
TERM xterm-color
TERM color-xterm
TERM vt100
TERM dtterm
TERM color_xterm
TERM ansi
TERM screen
TERM screen.linux
TERM kon
TERM kterm
TERM gnome
TERM konsole

EIGHTBIT 1

# Text color codes:
# 30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
# Background color codes:
# 40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white
NORMAL 00   # global default, although everything should be something.
FILE 00     # normal file
DIR 00;36   # directory
LINK 00;35  # symbolic link
FIFO 40;33  # pipe
SOCK 01;35  # socket
BLK 40;32;00    # block device driver
CHR 40;32;00    # character device driver
ORPHAN 01;05;37;41  # orphaned syminks
MISSING 01;05;37;41 # ... and the files they point to
# This is for files with execute permission:
EXEC 00;33

# List any file extensions like '.gz' or '.tar' that you would like ls
# to colorize below. Put the extension, a space, and the color init string.
# (and any comments you want to add after a '#')
.cmd 00;32 # executables (bright green)
.exe 00;32
.com 00;32
.btm 00;32
.bat 00;32
.sh  00;32
.csh 00;32
.tar 00;31 # archives or compressed (bright red)
.tgz 00;31
.arj 00;31
.taz 00;31
.lzh 00;31
.zip 00;31
.z   00;31
.Z   00;31
.gz  00;31
.bz2 00;31
.bz  00;31
.tz  00;31
.rpm 00;31
.cpio 00;31
.jpg 00;35 # image formats
.gif 00;35
.bmp 00;35
.xbm 00;35
.xpm 00;35
.png 00;35
.tif 00;35

#**end of example dircolors file

To change a color, simply use the color values desired. Using the colors requires an eval statement in a login file, for instance the $HOME/.bashrc:

eval `dircolors $HOME/.dir_colors`

---

