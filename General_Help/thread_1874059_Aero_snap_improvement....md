---
title: "Aero snap improvement..."
date: 2011-11-02
forum: General Help
---

### Post by se4n_1 on 2011-11-02
Hello,

I was tinkering today and I enabled the Aero snap feature using the commands in compiz, that's all well and good but I have two monitors and each has a different screen resolution. After some more tinkering I realized using xrandr command on each screen produces results only for the screen the command was initiated on so i could in theory substitute it into the commands that define how the windows snap: The commands look something like this:

xrandr -q | grep -w Screen | awk '{print $8/2}'

which gives half the screens width and I can do something similar for the height. When I try and substitute that expression into my command for instance to snap the screen to the right:

wmctrl -r :ACTIVE: -e 0, `xrandr -q | grep -w Screen | awk '{print $8/2}'`,0, `xrandr -q | grep -w Screen | awk '{print $8/2}'`,1000

nothing happens and in terminal the error message:

The -e option expects a list of comma separated integers: "gravity,X,Y,width,height"

is displayed. I've looked online for how to correctly substitute arbitrary expressions into active commands with awk but I've got nothing. Maybe someone who's a wizz in terminal can tell me how to do that, whichll make me a better person and enable a gaudy visual effect simultaneously!

Cheers!

---

