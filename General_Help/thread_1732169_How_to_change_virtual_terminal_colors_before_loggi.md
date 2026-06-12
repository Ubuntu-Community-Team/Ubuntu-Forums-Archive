---
title: "How to change virtual terminal colors before logging in?"
date: 2011-04-17
forum: General Help
---

### Post by l07 on 2011-04-17
I put
```
echo -e '\e[0;34m'
```
into /etc/profile, but it still doesn't work until I login.
I'd like it to work before that, so that all messages (like those displayed on boot up) have these default settings.
How to do so?

---

### Post by l07 on 2011-04-17
Also, once I run ```
ls --color=auto
``` the color changes back to default. How do I let it go back my specification after other commands change it?

---

### Post by blueridgedog on 2011-04-17
Have you tried setting up a .dircolors file globally or in your home directory?

Here are a few links:

[http://mute.nu/?p=81](http://mute.nu/?p=81)

[http://www.google.com/search?aq=0&oq=dircol&sourceid=chrome&ie=UTF-8&q=dircolors#sclient=psy&hl=en&source=hp&q=.dircolors+ubuntu&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=ee1a58bdef03b7c1](http://www.google.com/search?aq=0&oq=dircol&sourceid=chrome&ie=UTF-8&q=dircolors#sclient=psy&hl=en&source=hp&q=.dircolors+ubuntu&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=ee1a58bdef03b7c1)

---

### Post by l07 on 2011-04-17
I'd like to clarify: I'd like to have the color set by ```
echo -e '\e[0;34m'
``` unless another command explicitly produces its own colored output. After it does so, I'd like for ```
echo -e '\e[0;34m' 
``` to go back in effect. One way I can see is running it after every command. Is there a better way?

---

### Post by blueridgedog on 2011-04-18
Perhaps I do not follow what you are doing.

What is accomplished by "echo -e '\e[0;34m'"?  I recognize 34 as blue.

Dircolors will allow you to set a baseline colorization that will be used by all programs that color the terminal, so that they will be in harmony with your desired scheme.  Using dircolors will alleviate the need to echo desired commands each time.

Here is another example:

[http://linux-sxs.org/housekeeping/dircolor.html](http://linux-sxs.org/housekeeping/dircolor.html)

In your .bashrc is the section:

```
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi
```

So, if you have a .dircolors file in your home directory, it will be used.

---

### Post by l07 on 2011-04-21
I'll try to explain because I think you're talking about only about ls and such, as in .bashrc above.

I put "echo -e '\e[0;34m'" into /etc/profile so it runs whenever the shell (bash) is run, because I don't know yet what file to put it in so the color change takes effect on boot up. That would change the color of all the messages displayed as drivers are loaded, etc. on bootup.  In addition such a file might have a different way of coloring the text.

"echo -e '\e[0;34m'" changes the color of the prompt and all other console text (in this case, all foreground colors become blue). However, it only lasts until another command modifies the colors (e.g., ls). Then it goes back to default, white on black. I'm ok with ls printing colors as is, but I want the default text to be how I set it.

There are essentially two issues:
1. After ls or such is run, I need to run "echo -e '\e[0;34m'" again.
2. Putting "echo -e '\e[0;34m'" into /etc/profile changes the color only after I login. I want it to do so before logging-in as well.

Also, note that I'm talking specifically about virtual terminals, because  a terminal emulator, like gnome-terminal, doesn't have issue 1. And it  doesn't have anything to do with issue 2, since it starts optionally at a  later stage.

Hopefully I've allowed for us to understand each other better. I appreciate your help and am looking forward to suggestions.

---

### Post by blueridgedog on 2011-04-23
In that case, I would suggest using a .dircolors file in your home directory that colorizes the text for you:

You can use the following simple file:


```

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
TERM xterm
TERM vt100
# Attribute codes:
# 00=none 01=bold 04=underscore 05=blink 07=reverse 08=concealed
# Text color codes:
# 30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
# Background color codes:
# 40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white
NORMAL 00;34 # global default, although everything should be something.
FILE 00;34 # normal file
DIR 01;34 # directory

```

This should set the default to black background, blue foreground.

A more complex file that would colorize items based on extension is:

```
# Configuration file for dircolors, a utility to help you set the
# LS_COLORS environment variable used by GNU ls with the --color option.

# The keywords COLOR, OPTIONS, and EIGHTBIT (honored by the
# slackware version of dircolors) are recognized but ignored.

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
TERM xterm
TERM vt100

# Below are the color init strings for the basic file types. A color init
# string consists of one or more of the following numeric codes:
# Attribute codes:
# 00=none 01=bold 04=underscore 05=blink 07=reverse 08=concealed
# Text color codes:
# 30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
# Background color codes:
# 40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white
NORMAL 00;34 # global default, although everything should be something.
FILE 00;34 # normal file
DIR 01;34 # directory
LINK 01;36 # symbolic link
FIFO 40;33 # pipe
SOCK 01;35 # socket
BLK 40;33;01 # block device driver
CHR 40;33;01 # character device driver
ORPHAN 40;31;01 # symlink to nonexistent file

# This is for files with execute permission:
EXEC 01;32

# List any file extensions like '.gz' or '.tar' that you would like ls
# to colorize below. Put the extension, a space, and the color init string.
# (and any comments you want to add after a '#')

# If you use DOS-style suffixes, you may want to uncomment the following:
#.cmd 01;32 # executables (bright green)
#.exe 01;32
#.com 01;32
#.btm 01;32
#.bat 01;32

.tar 01;31 # archives or compressed (bright red)
..tgz 01;31
..arj 01;31
..taz 01;31
..lzh 01;31
..zip 01;31
..z 01;31
..Z 01;31
..gz 01;31
..deb 01;31
..png 01;35 # image formats
..png 01;35
..bmp 01;35
..ppm 01;35
..tga 01;35
..xbm 01;35
..xpm 01;35
..tif 01;35
..mpg 01;37
..avi 01;37
..gl 01;37
..dl 01;37

```

---

