---
title: "Problem with starting program on specific monitor"
date: 2011-10-07
forum: General Help
---

### Post by mariodab on 2011-10-07
I have a dual monitor setup with a crt monitor as one output and a TV from s-video as the second output. 

I am trying to have xbmc autostart full screen on the TV only. I tried adding the "Primary" option in xorg.conf but that didn't work. Then I decided to try doing:

export DISPLAY=:0.x && xbmc

But couldn't get an output from:

echo "$Display"

It was just a blank line.  Disconnecting the TV and trying it again output:

0.1

So I figured TV was 0.2, so I reconnected the TV and did:

export DISPLAY=:0.2 && xbmc

This opened up xbmc on the monitor not the TV. So I have no idea what to do now.  Any suggestions?

---

### Post by papibe on 2011-10-07
Are you sure you are running separate X screens instead of Twinview?

I'm also running a 2 head system (monitor and TV), and that syntax works for me. To make sure what is the exact name of the TV screen, open a terminal on the TV and run:
```
$ echo $DISPLAY
```
If your are running 2 separate screens, the result should be different from a terminal on the monitor.

Regards.

---

### Post by mariodab on 2011-10-07
It is definitely seperate x screens. Have to use nvidia configuration software to set it up. I have three options for the screen: off, Separate x display, and twinview.  Separate X display is selected for both outputs.

I already tired using echo "$Display" as outlined in my first post.  The output of this command was a blank line on both displays when they were both enabled (I ran the command on each display). Disabling the TV and having only a single display gives me the output:

0.1

In summation, I cannot get echo "$Display" to report my outputs correctly when both displays are connected.  I believe this is my major problem. If I could find out why it is not reporting it correctly, I could make my setup work the way I want it to.

I have been researching this for the past couple of days and the closest thing I can find was someone having issues with ssh login.  Not what I am trying to do, but they got the same output I get when issuing:

echo "$Display"

Which is a blank line.  There is no output. Below is what I get with the command:

media-pc@media-pc:~$ echo "$Display"

media-pc@media-pc:~$

Thanks for responding.  You have any others ideas I could try?

---

### Post by papibe on 2011-10-07
Just make sure, bash variables are case sensitive so $Display is another variable, you need to use $DISPLAY. For example:
```
$ echo $DISPLAY
:0.0
$ echo $Display

$
```
Could you test that again using the all caps variable?

Regards.

---

### Post by BicyclerBoy on 2011-10-07
The primary X screen is :0.0, second is :0.1..

A working example (in 10.04)
from terminal:
DISPLAY=":0.1" mythfrontend
launches myth onto 2nd display

launcher script eg:
```

#!/bin/sh
# Run MythTV front end on display 1
export DISPLAY=:0.1
mythfrontend

```

---

### Post by mariodab on 2011-10-07
Man. I hate it when I do that. Syntax, my old enemy.  Yeah, putting display in all caps got me my output.  Thank you so much.  Problem solved. Thank you papibe for pointing out the syntax, I swear that is the source of half my problems. Now xbmc starts up in fullscreen on the TV and my keyboard and mouse aren't locked the tv.  I love it when things come together.

---

### Post by papibe on 2011-10-07
:D Glad we could help.

By the way, I think BicyclerBoy's script is good idea. Not only will simplify things for you, but also will be a reference and source for ideas for future challenges.

If you create a ~/bin directory an move the script there, you wouldn't have to modify anything else to make it work in the terminal (as it were an installed application). For example, you could run something like
```
$ myXBMC
```
and have XBMC running on the TV screen.

Regards.

---

