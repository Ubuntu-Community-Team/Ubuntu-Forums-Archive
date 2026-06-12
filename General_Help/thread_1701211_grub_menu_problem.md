---
title: "grub menu problem"
date: 2011-03-06
forum: General Help
---

### Post by decrepit on 2011-03-06
Sorry guys this falls into the silly old fart category.

I didn't like the white on black grub menu, found it hard to read.

so modified the /etc/grub.d/05_debian_theme


```

set menu_color_normal=white/black
set menu_color_highlight=black/light-grey

```

(This is where the silly old fart comes in, I didn't comment out the original lines, I just deleted the black/white, black /light-grey and reversed them.)

then I updated grub, rebooted, and got this message from grub.

> 
error Invalid mode 1280X1024
error unknown command "terminal"
warning Invalid background color "light-grey"


Maybe a while ago I did play with the resolution for some reason or other. But I did a 
```
vbeinfo
``` 
and 1280X1024 came up as OK.

No idea about the "terminal" thing.

Maybe "light-grey" should be "light_grey"

Could somebody please look at their /etc/grub.d/05_debian_theme and post the below lines

```

  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/light-grey
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
    if is_path_readable_by_grub $i ; then

```

As this mention of "terminal is close to where I was mucking about, maybe I've done something inadvertently here

---

### Post by turtle153 on 2011-03-06
```

  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
EOF
}

# check for usable backgrounds
use_bg=false
for output in ${GRUB_TERMINAL_OUTPUT}; do
  if [ "$output" = "gfxterm" ] ; then
    for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
      if is_path_readable_by_grub $i ; then 

```
GRUB uses the American spelling, **gray** and we use the British spelling, **grey**.

---

### Post by drs305 on 2011-03-06
Also the resolution should have a lowercase X (x). I don't know about the terminal message either. 

Fix the two items mentioned, run "sudo update-grub" and see if you still have the problem.

---

### Post by decrepit on 2011-03-06
OK thanks guys, that's fixed it, such silly little things. 
The "terminal" problem has also vanished.

I'll change the resolution to something a bit less, the writing with 1280x1040 is too small, and have another go at reversing the colours.
Fingers crossed.

---

### Post by decrepit on 2011-03-06
Yep, changed resolution to 800x600, reversed the colours and it's all go.
much easier to read and select OS.
Now, all I have to do is remember how to mark this thread "solved".


OK I got it.

---

