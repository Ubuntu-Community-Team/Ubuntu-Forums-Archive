---
title: "256 ls support?"
date: 2009-12-27
forum: General Help
---

### Post by ooobooontooo on 2009-12-27
Hi,

Is there a way to change dircolors or LS_COLORS to have support for 256 colors? I'm using urxvt right now and kind of frustrated by the lack of colors available.

Thanks in advance.

---

### Post by falconindy on 2009-12-27
It's possibly an issue of the terminal not supporting 256 colors. Not sure what rendition of rxvt Ubuntu packages. What do you get when you do:
```
echo $TERM
```
Also, have you made an .Xdefaults file to set the palette?

---

### Post by ooobooontooo on 2009-12-27
> **falconindy said:**
> It's possibly an issue of the terminal not supporting 256 colors. Not sure what rendition of rxvt Ubuntu packages. What do you get when you do:
```
echo $TERM
```
Also, have you made an .Xdefaults file to set the palette?

I compiled my urxvt with 256 color support so that shouldn't be a problem.

$TERM gives rxvt-unicode

My .Xdefaults:
```
URxvt*depth: 32
URxvt*foreground: green
URxvt*background: rgba:0000/0000/0000/bbbb
URxvt*font: xft:Terminus:pixelsize=12
URxvt*fading: 12%
URxvt*shading: 75
URxvt*scrollBar: false
```

I'm pretty sure I have the support for it. I just don't know where to look to expand the colors offered for ls coloring.

EDIT: more info

---

### Post by falconindy on 2009-12-27
This is my .Xdefaults, with 2 color themes: gnome-terminal, and the ever popular Tango.

[http://dpaste.com/138405/](http://dpaste.com/138405/)

---

### Post by ooobooontooo on 2009-12-28
> **falconindy said:**
> This is my .Xdefaults, with 2 color themes: gnome-terminal, and the ever popular Tango.

[http://dpaste.com/138405/](http://dpaste.com/138405/)

I think you may be misunderstanding me. My qualm isn't that urxvt doesn't support 256 colors. My qualm is that when I use ls --color, there are only a limited number of colors provided to highlight the directories, executables and such, even on my 256-color terminal. I was wondering if there were any available programs to expand the number of colors that can be highlighted by ls.

Let me know if I misunderstood you, and you're actually telling how to do the above. Thanks for responding.

---

### Post by mali2297 on 2009-12-28
You can change the definitions of the 16 standard colors by using .Xdefaults, see the sample code below. However, I do not know any way to expand the palette to more than 16 colors. I doubt that it is possible.

```

!COLOR DEFINITIONS

!BLACK
URxvt*color0:           #000000
URxvt*color8:           #666666

!RED
URxvt*color1:           #9e1828
URxvt*color9:           #cf6171

!GREEN
URxvt*color2:           #81996C
URxvt*color10:          #84A651

!YELLOW
URxvt*color3:           #968a38
URxvt*color11:          #CCC678

!BLUE
URxvt*color4:           #414171
URxvt*color12:          #4186be

!MAGENTA
URxvt*color5:           #963c59
URxvt*color13:          #B288A4

!CYAN
URxvt*color6:           #418179
URxvt*color14:          #63A6A6

!WHITE
URxvt*color7:           #bebebe
URxvt*color15:          #ffffff

!WINDOW COLORS
URxvt*background:       #eeeeef
URxvt*foreground:       #303030
URxvt*borderColor:      #eeeeef
URxvt*fading:           0

!TRANSPARENCY
URxvt*transparent:      false
URxvt*shading:          80
URxvt*tintColor:        #e0e0e0

```

---

### Post by ooobooontooo on 2010-01-06
Hi,

I know it's a bit late, but thank you for your post. It wasn't exactly what I was looking for, but it really helped me out a lot.

---

