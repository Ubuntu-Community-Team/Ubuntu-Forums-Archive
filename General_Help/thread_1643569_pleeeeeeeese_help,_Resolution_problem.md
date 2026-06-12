---
title: "pleeeeeeeese help, Resolution problem"
date: 2010-12-12
forum: General Help
---

### Post by Pralay on 2010-12-12
Hi guys,
I am using ubuntu 10.10.
My monitor is old Samtron 56v and I have INTEL *82845G*/[I]GL Controller.
Ubuntu does not recognise my monitor as it says Unknown monitor and my resolution is stuck at 800*600.

I surfed the web for a way out and tried different options, but to no avail. My default xorg.conf was empty. I tried to edit it  with some available codes on web, but none of them really worked. 
I also tried xrandr for adding new mode.
But it says, "xrandr: Failed to get size of gamma for output default  ".

Anyone out there who can help me out? Please. [-o<
[/I]

---

### Post by fungiblename on 2010-12-12
Do you know the native resolution of the monitor, e.g., 1280x1024?

First step: 

Connect the external monitor, and type "xrandr" in the terminal. Note what xrandr calls the monitor. If you are connecting it to a laptop, you may see something like this: 

```

Screen 0: minimum 320 x 200, current 2166 x 900, maximum 8192 x 8192
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3     56.2  
   640x480        59.9     59.9  
LVDS1 connected 1366x768+1440+132 (normal left inverted right x axis y axis) 293mm x 164mm
   1366x768       60.0*+

```


If so, do the following in the terminal: 

```

cvt modeline 1280x1024

```

(or whatever your monitor's native resolution is)

Copy the output of that command starting after Modeline, e.g., 

```

"1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```

This is your "modeline string". Paste the "modeline string" as follows into the following xrandr commands: 

```

xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024_60.00

```

Be careful with this, however: Depending on the type and age of the monitor, you may permanently damage it with the wrong resolution or refresh rate. 60 Hz is usually pretty good, though....

The part inside the quotes is the name of your mode - you can call it whatever you like, so long as the part inside quotes in the --newmode line matches the part after VGA1 in the --addmode line.

You should now see the correct resolution in the GNOME Monitors panel.

If you like the results, paste the two xrandr commands above into your ~/.bashrc file or some other script that runs when you login.

Also, you may notice that one display is darker than the other. You can correct this in the terminal, but I'm not aware of a GUI for it yet. 

To aid those who are trying to find this via search, below is a method for adjusting gamma for an external monitor independently from a laptop to which it is attached, allowing one gamma setting for the laptop screen, and a different gamma for the external monitor: 

First, run xrandr, and note the output. Your laptop is likely called LVDS1, and your external screen something else, likely VGA1 or HDMI1

To correct gamma on your laptop, run: 
```

xrandr --output LVDS1 --gamma 1.8:1.8:1.8

```

On my Asus UL30A, this makes the screen look somewhat better than default (by default, it's pretty bad--almost unusable) - your numbers may vary. Read the xrandr manual page to see what the above actually does. 

You can do something similar for your external monitor, and even give it different settings: 

```

xrandr --output VGA1 --gamma 2.0:2.0:2.0

```

I hope this helps the original poster and anyone else out there who may be frustrated. This drove me crazy initially, but it works on my installation of Lucid/10.04 (I imagine it will also work on Maverick).

All of the above could easily be pasted into various scripts (or perhaps even programs that run at a lower level) that run automatically at certain events. That's well beyond my capabilities, though. 

However, none of this fixes the issue with mouse pointers disappearing off the top of a monitor that has a lower vertical resolution than another monitor on the same logical display.....

---

### Post by Pralay on 2010-12-13
Thanks fungiblename for your detailed post.
Now this is what happened when I followed your instructions.

When I type "xrandr" in terminal, it says,

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600         0.0* 
```


When I try "xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync",
it says,

```
xrandr: Failed to get size of gamma for output default
```

There must be something wrong. But I can't figure it out.
Can you please help me out of this? Please. 8-[

---

### Post by Pralay on 2010-12-14
hi guys,
I am really expecting a guidance from you to resolve this issue.
I am yet to get rid of this of this trouble. 
Please someone help! [-o<

---

### Post by eeshan.mulye4 on 2010-12-14
did you check that your graphics driver was installed properly.If not do it see the ubuntu hardware support list and find the driver solution.Then if thats not a problem check your monitor driver on the net for linux.

---

### Post by eeshan.mulye4 on 2010-12-14
I think this might help a little


The intel drivers are all built right into the Linux kernel.

It sounds like you're going to need to edit xorg.conf:
sudo gedit /etc/X11/xorg.conf

Find the "Screen" section and add:
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection

Of course replace the resolutions I listed with your own. 

If that doesn't work, you can also try adding some modelines:
[http://xtiming.sourceforge.net/cgi-bin/x…]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")

---

### Post by Pralay on 2010-12-14
Hi eeshan.mulye4,
Thanks for your post.
My default xorg.conf seems empty because when I tried to edit it , it opened a empty file.
Can you guide exactly what to write in that file?

Then I can try it out.

Thanks again.

---

