---
title: "xterm, urxvt, vim , and screen color problems"
date: 2009-07-31
forum: General Help
---

### Post by bp1509 on 2009-07-31
Ok the more I try to fix my problem it seems the more complicated it gets.  What I want, I thought was simple:

[LIST]
[*]a 256 color capable terminal
[*]that will display 256 colors in vim
[*]that will display 256 colors in screen
[*]that will display 256 colors in vim in screen
[*]that has clickable links (only urxvt)
[*]that doesn't make vim and other cli apps go crazy when I ssh into another box because of the uset term type.  I log into 50-60 boxes a day.
[/LIST]

Now xterm seems to be the most workable solution, I guess I can give up on having clickable links, so that can go on the back burner.  But these are the problems i'm having.

Here's the problem point by point:

[SIZE="4"]**Urxvt**[/SIZE]
$ echo $TERM
xterm-256color

Urxvt will run a [perl script I have to display 256 colors.]("http://tuxtraining.com/wp-content/uploads/2009/07/256colors")  Except is does not show the grayscale ramp shown here:

[IMG]http://tuxtraining.com/wp-content/uploads/2009/07/256colors.png[/IMG]

VIM in urxvt does NOT show any colors.  It's all white text.

This is my .vimrc
```

$ cat .vimrc                                                                                                                       
syntax on
set ignorecase
set smartcase
set incsearch
set hlsearch
let g:netrw_http_cmd = "wget -q -O"
if &t_Co == 256
    colorscheme xoria256
else
	colorscheme desert 
endif

```

_in urxvt Gnu Screen_
echo $TERM 
screen-256color-bce

the perl script does not display 256 colors like it should.

vim in urxvt in screen again, does not show any colors. all white text.

[SIZE="4"]
**Xterm**[/SIZE]
echo $TERM
xterm

Xterm displays the full 256 colors from the script including the grayscale ramp.

vim in xterm displays the desert theme (i would prefer it default to the xoria256, no idea why the 256 color script works but vim doesn't see xterm as a 256 capable terminal).

_in xterm, Gnu Screen_
echo $TERM 
screen-256color-bce   ( I do not see in any file where this option is defined)

Xterm with Gnu Screen displays the full 256 colors from the script including the grayscale ramp.

Vim in Gnu Screen in Xterm displays 256 colors properly.


**Here is my .screenrc**

```
#terminfo and termcap for nice 256 color terminal
# allow bold colors - necessary for some reason
attrcolor b ".I"
# tell screen how to set colors. AB = background, AF=foreground
termcapinfo xterm 'Co#256:AB=\E[48;5;%dm:AF=\E[38;5;%dm'
# erase background with current bg color
defbce "on"
#term xterm-256color
term screen-256color
startup_message off


caption always "%{= KW}%-w%{= gW}%n %t%{-}%+w %-="

hardstatus alwayslastline "%{= kW} %-= %{= kC}Session:%u%{= kW} %5` | %{= kC}Host:%{= kW} %H | %1` |%{= kC} MEM:%{= kW} %2`MB /%{= kC} SW: %{= kW}%3`MB | %4` %{= kR}Unread %{= kW}| %m/%d %c"

vbell off

#Backticks to display information in status bar
backtick 1 60 60 /home/username/bin/get_uptime
backtick 2 60 60 /home/username/bin/get_freemem
backtick 3 60 60 /home/username/bin/get_freeswap
backtick 4 60 60 /home/username/bin/get_gmail
backtick 5 60 60 /home/username/bin/get_sessionname

defscrollback 5000
screen -t root 0 sudo -s
screen -t shell 1 bash
screen -t shell 2 bash
screen -t shell 3 bash
screen -t shell 4 bash
screen -t shell 5 bash
screen -t shell 6  bash
screen -t shell 7  bash
screen -t irc 8 irssi
screen -t home 9 bash
select 1

```

**here is my .Xdefaults**
```
!XTerm*font: -*-terminal-*-*-*-*-14-*-*-*-*-*-*-
XTerm*font: xft:DejaVu Sans Mono:size=8
xterm*faceName: Mono
xterm*faceSize: 8
XTerm*background: #191919
XTerm*foreground: white 
XTerm*pointerColor: white
XTerm*pointerColorBackground: black
XTerm*cursorColor: white 
!XTerm*internalBorder: 3
XTerm*loginShell: true
XTerm*scrollBar: false
XTerm*scrollKey: true
XTerm*saveLines: 1000
XTerm*multiClickTime: 250
XTerm*boldColors: false
xterm*title: xterm
xterm*geometry: 160x25
! Black
XTerm*color0:           #262626
XTerm*color8:           #252525

! Red
XTerm*color1:           #C12121
XTerm*color9:           #E50E0E

! Green
XTerm*color2:           #597b20
XTerm*color10:          #89b83f

! Yellow
XTerm*color3:           #Ded838
XTerm*color11:          #efef60

! Blue
XTerm*color4:           #265997
XTerm*color12:          #3F6FD0

! Magenta
XTerm*color5:           #706c9a
XTerm*color13:          #826ab1

! Cyan
XTerm*color6:           #69a2b0
XTerm*color14:          #a1cdcd

! White
XTerm*color7:           #BBBBBB
XTerm*color15:          #EEEEEF

URxvt*termName: xterm-256color 
URxvt*urlLauncher: /usr/bin/firefox
URxvt.matcher.pattern.1: \\bwww\\.[\\w-]\\.[\\w./?&@#-]*[\\w/-]
URxvt.matcher.button: 2
URxvt.perl-ext-common: default,matcher
URxvt*saveLines: 4000
URxvt*background: #191919 
URxvt*secondaryScroll: true
URxvt*scrollBar: false
URxvt*geometry: 150x25
URxvt.font: xft:DejaVu Sans Mono:size=8
URxvt.xftAntialias:      true
URxvt*foreground: white 
URxvt*pointerColor: white
URxvt*pointerColorBackground: black
URxvt*cursorColor: white 
!URxvt*inheritPixmap: True
!URxvt*shading: 90   
!URxvt*tintColor: #999
URxvt*keysym.Home: \033[1~
URxvt*keysym.End: \033[4~
! Black
URxvt*color0:           #262626                                                                                                                                                                                   
URxvt*color8:           #252525                                                                                                                                                                                   

! Red
URxvt*color1:           #C12121
URxvt*color9:           #E50E0E

! Green
URxvt*color2:           #597b20
URxvt*color10:          #89b83f

! Yellow
URxvt*color3:           #Ded838
URxvt*color11:          #efef60

! Blue
URxvt*color4:           #265997
URxvt*color12:          #3F6FD0

! Magenta
URxvt*color5:           #706c9a
URxvt*color13:          #826ab1

! Cyan
URxvt*color6:           #69a2b0
URxvt*color14:          #a1cdcd

! White
URxvt*color7:           #BBBBBB
URxvt*color15:          #EEEEEF

```


[SIZE="3"]To Fix In Xterm[/SIZE]
[LIST]
[*]Get Vim to display 256 colors without Gnu Screen
[/LIST]


[SIZE="3"]To Fix In Urxvt[/SIZE]
[LIST]
[*]Get vim to display any color, but preferably 256 colors in urxvt and urxvt with Gnu Screen.
[/LIST]

[SIZE="3"]To Fix In Gnu Screen[/SIZE]
[LIST]
[*]Make it stop reporting the term variable as screen-256color-bce without losing 256 color support as this screws up shells i ssh to.
[/LIST]

any help would be greatly appreciated.  I feel like a dog chasing its tail b/c when I find a fix to one problem, I end up creating 1-2 more.

---

