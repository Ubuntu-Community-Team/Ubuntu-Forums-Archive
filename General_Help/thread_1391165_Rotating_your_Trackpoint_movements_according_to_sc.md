---
title: "Rotating your Trackpoint movements according to screen orientation"
date: 2010-01-26
forum: General Help
---

### Post by Raniss on 2010-01-26
Hey,

I've searched for and found a solution to rotate the movements of the pointer device according the screen orientation. Tested only on a Thinkpad X60 running 9.10 so far, but it should work on other models if you change TPDEV accordingly (xinput list).

Put it somewhere, like ~/bin/rotate, chmod +x it and call it with the arguments [normal|inverted|left|right].

Improvements are welcome. 

```
#!/bin/sh

# grab first pointer device
TPDEV=`xinput list|grep XExtensionPointer|sed 's/.*id=\([0-9]*\).*/\1/'|head -n 1`

# force a specified device
#TPDEV="TPPS/2 IBM TrackPoint"

# might need adjustments
AXISSWAP=236
AXISINV=234

case $1 in 
	normal)
		if xrandr -o normal; then
			xinput set-int-prop "$TPDEV" $AXISSWAP 8 0
			xinput set-int-prop "$TPDEV" $AXISINV 8 0 0
		fi
		;;
	inverted)
		if xrandr -o inverted; then
			xinput set-int-prop "$TPDEV" $AXISSWAP 8 0
			xinput set-int-prop "$TPDEV" $AXISINV 8 1 1
		fi
		;;
	left)
		if xrandr -o left; then
			xinput set-int-prop "$TPDEV" $AXISSWAP 8 1
			xinput set-int-prop "$TPDEV" $AXISINV 8 1 0
		fi
		;;
	right)
		if xrandr -o right; then
			xinput set-int-prop "$TPDEV" $AXISSWAP 8 1
			xinput set-int-prop "$TPDEV" $AXISINV 8 0 1
		fi
		;;
	*) 
		echo "options are: normal, inverted, left or right"
		;;
esac


```

---

