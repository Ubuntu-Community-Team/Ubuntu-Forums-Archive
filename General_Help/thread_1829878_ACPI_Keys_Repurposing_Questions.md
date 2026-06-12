---
title: "ACPI Keys Repurposing Questions"
date: 2011-08-20
forum: General Help
---

### Post by abeowitz on 2011-08-20
I'd like to repurpose 6 ACPI keys on my laptop to keyboard functions while in MyPaint.

Specifically the Volume up/down/mute and CD Play/Next/Prev buttons on my Asus U43JC.  (These are conveniently on the left while I can draw on the tablet with my right hand.)

I've successfully modified /etc/acpi/events, and the scripts are called as expected.

But, I have two problems:

1)  I'm using xdotool to ID the current application.  i.e. if MyPaint, then send 'd' or 'f' to change cursor size.  If other app, exit.

Problem is the ACPI script does not have access to the Xorg display, even with 'xhost +'.


2)  Even when I successfully capture an ACPI event, the volume still goes up and down.  How can I halt an ACPI event after I've processed it?


-OR- perhaps there's a better way to:

1)  Catch the ACPI key event
2)  Determine which app is focused
3)  Issue appropriate new key event

Thanks in advance!  :)

Oh, here's some test code:

```
#!/bin/bash

# Determine active window/app:
A1=`ps -p \`xdotool getactivewindow getwindowpid\` | grep -c mypaint`

# Debug
A1=`xdotool getactivewindow 2>&1`

if [ 1"$A1" = "1"]; then
  echo "mypaint" > /tmp/test.txt
  xdotool key d
else
  # print error message
  echo "$A1" > /tmp/test.txt
fi

exit 0

```

---

