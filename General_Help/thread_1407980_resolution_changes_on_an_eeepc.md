---
title: "resolution changes on an eeepc"
date: 2010-02-15
forum: General Help
---

### Post by jeff.sadowski on 2010-02-15
Here is a script I wrote to change resolutions on my eeepc

> #!/bin/bash
#
# res.sh
#
change_to()
{
xrandr --fb $1 --fbmm $1 --output LVDS1 -s $1 --scale $2 --panning $1+0+0 --pos 0x0 2>/dev/null >/dev/null
notify-send -u critical $1 -t 1
}
current=`xrandr |head -n 1|cut -d, -f 2| awk '{print $2$3$4}'`
case $current in
1920x1080)
change_to 640x480 0.625x0.8
;;
640x480)
change_to 800x600 0.79x1.0
;;
800x600)
change_to 1024x768 1x1.28
;;
1024x600)
change_to 1920x1080 1.88x1.8
;;
*)
change_to 1024x600 1.0x1.0
;;
esac


---

