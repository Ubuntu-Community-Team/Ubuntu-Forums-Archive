---
title: "Analog joystick not working in one direction"
date: 2010-06-28
forum: General Help
---

### Post by ardvark on 2010-06-28
I have an old Logitech Wingman analog joystick connected to a game port on a Creative sound card. At this point I've got the system to see the joystck and was able to run jscal. I was also able to run jstest. I was able to see positive & negative numbers moving the joystick in four directions. However, when I try 2 different MAME games or Open Arena there is no right direction. Pushing the joystick right only stops it from going left.. Up and down movement seems to be OK.

---

### Post by toledoimperial on 2010-08-04
> **ardvark said:**
> I have an old Logitech Wingman analog joystick connected to a game port on a Creative sound card. At this point I've got the system to see the joystck and was able to run jscal. I was also able to run jstest. I was able to see positive & negative numbers moving the joystick in four directions. However, when I try 2 different MAME games or Open Arena there is no right direction. Pushing the joystick right only stops it from going left.. Up and down movement seems to be OK.

Now games use "/dev/input/eventX" instead of "/dev/input/jsX" therefore jscal calibration has no effect on them.

You must force games to use "/dev/input/jsX".

Workaround 1 (only for SDL based games):

[FONT=courier new][COLOR=#0000ff][FONT=courier new][COLOR=#000000][FONT=courier new]  export SDL_JOYSTICK_DEVICE="/dev/input/jsX"[/FONT][/COLOR][/FONT][/COLOR][/FONT]

Workaround 2 (generic):

Look for the joystick event input device (lshal | less) and remove it by hand (sudo rm /dev/input/eventX). Don't worry about event input device removing because it is created again after reboot.

Another automatic and equivalente way is:

[FONT=courier new][COLOR=#0000ff][FONT=courier new][COLOR=#000000][FONT=courier new]  for n in [COLOR=#000000][FONT=courier new]/dev/input/by-path/*event-joystick[/FONT][/COLOR]; do sudo rm $(readlink -f $n); done
[/FONT][/COLOR][/FONT][/COLOR][/FONT]
Best regards.

---

### Post by ardvark on 2010-08-15
Some time after I entered this problem, and before the last reply, I tried the following. I unplugged the analog joystick and plugged in a USB joystick, and restarted my PC. It did not recognize the USB joystck but that may be because it was one of the Xbox/PC types. So I put back everything the way it was. The analog joystick was now working much better, although in the MAME games it's a not very responsive. I did not rerun JSCAL, so perhaps running it messes things up.

---

