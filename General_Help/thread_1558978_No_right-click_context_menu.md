---
title: "No right-click context menu"
date: 2010-08-23
forum: General Help
---

### Post by Quackers on 2010-08-23
I've just installed 64 bit Lucid Lynx on a seperate hard drive and all seems well except when I right-click on the desktop no context menu appears. Nothing happens :confused:
It's ok when right-clicking in Firefox say, or within a file, but not on the desktop.
What have I done?

---

### Post by xangua on 2010-08-23
is nautilus runing¿

---

### Post by Quackers on 2010-08-23
Yes, xangua, Nautilus is running.

---

### Post by Quackers on 2010-08-23
Any ideas?

---

### Post by WorMzy on 2010-08-23
Is nautilus drawing your desktop? (Check gconf: /apps/nautilus/preferences/show_desktop)

Do you get a context menu in other nautilus windows?

---

### Post by Quackers on 2010-08-23
Hello WorMzy.
Sorry but I don't understand the first bit of your answer.
Yes, I do get a context menu in every type of window - just not the desktop.
I think it may be a user problem. My conky display is "over the top" of any open windows too.

---

### Post by WorMzy on 2010-08-23
Sorry, I should have elaborated on that: open gconf-editor (Alt+F2, gconf-editor, run), and browse to that key. (gconf is like the windows registry, just not as problematic or necessary)

Conky rising above the desktop level is a classic sign that your desktop isn't being drawn by nautilus.

Y'see, the desktop is, by default, just an image. Nautilus adds extra functionality to it by adding the context menu and clickable icons for "Computer" and removable drives, etc., as well as displaying the contents of ~/Desktop. So if nautilus crashes, or hasn't been told to draw the desktop, that added functionality stops working, and you're left with just your desktop image.

---

### Post by Quackers on 2010-08-23
Thanks for the explanation :-)
No, the show_desktop box is not checked.
Also, by way of confirmation I have created 2 desktop icons and although they appear in the desktop folder in Home, they don't appear on the actual desktop.
If Nautilus is not drawing the desktop, what is? Compiz, xorg?

---

### Post by WorMzy on 2010-08-23
gdm, I believe. The desktop image info is stored separately in gconf, under /desktop/gnome/background, which is why it continues to display even if nautilus isn't drawing it.

Check that box (show_desktop) in gconf to enable the nautilus functionality. :)

---

### Post by Quackers on 2010-08-23
Ok, I've ticked the show_desktop box and rebooted.
I now have the 2 shortcuts on the desktop and I have a right-click context menu.
But :-( open windows can still slide under Conky.
So thanks for your help, it did solve the question I asked. I've just got a different one now :-)

---

### Post by WorMzy on 2010-08-23
Well, one down. ;)

Is conky starting automatically? If so, it might be starting up too quickly, so it's being drawn before nautilus takes command of the desktop.

Try extending the sleep command of the start-up command, e.g.

```
sleep 10 && conky
```

If you're starting conky manually, then maybe you're missing part of the config:
```
own_window_hints undecorated,_below_,sticky,skip_taskbar,skip_pager
```

---

### Post by Quackers on 2010-08-23
My current conky works fine in 32 bit. Startup is delayed by 30 seconds. In fact I copied over the files (after changing the path to weather.template) and my conkyrc does not include the line you refer to. I'll give that a try. Thanks.

---

### Post by WorMzy on 2010-08-23
30 seconds? I'd have gotten bored and walked away by then. :P

It's strange that it works on 32-bit but not 64-bit though, the different architecture shouldn't make any difference, and indeed it doesn't with my config.

Here's all the options I have in my conkyrc, just in case you don't have any of them either (I'm not sure how relevant any of them are any more, I think I generated it at least a couple of years ago now)

```
use_xft yes
xftfont DejaVu Sans:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 185 800
maximum_width 185
default_color black
draw_shades no

color0 0033CC
color1 660000
color2 330066

alignment top_right
gap_x 25
gap_y 40

net_avg_samples 2

override_utf8_locale yes

no_buffers yes
```

---

### Post by Quackers on 2010-08-23
At the risk of speaking too soon, I hereby declare all problems to be solv-ed!
That did it, WorMzy! Many thanks :-)
I'm really not sure why that line was necessary in the 64 bit version and not in the 32 bit version. But, in fairness, in the 64 bit version there was originally a shadow drawn around the conky window (which I got rid of with Compiz) that wasn't there in 32 bit. So there does seem to be some difference between the two.
Once again, thanks for your time and expertise, old bean :-)

---

### Post by WorMzy on 2010-08-23
Ah, glad I could help. Again.

I'm not stalking your topics, honest. :P

---

### Post by Quackers on 2010-08-23
Here's my ramshackle attempt :-) BTW stalk away! I need help often :-)

```
alignment top_right
background no
border_width 0
cpu_avg_samples 2
default_color white
default_outline_color black
default_shade_color black
double_buffer yes
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades yes
use_xft yes
xftfont terminus:size=11
gap_x 10
gap_y 50
maximum_width 320
minimum_size 300 100
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no
text_buffer_size 4096

```

---

### Post by WorMzy on 2010-08-23
After looking at conky's man page, it seems that hints line wouldn't have made any difference,

```
       own_window_type
              if  own_window  is  yes,  you  may specify type normal, desktop,
              dock, panel or override (default: normal).  Desktop windows  are
              special windows that have no window decorations; are always vis&#8208;
              ible on your desktop; do not appear in your  pager  or  taskbar;
              and  are  sticky  across  all  workspaces. Panel windows reserve
              space along a desktop edge, just like panels and taskbars,  pre&#8208;
              venting  maximized  windows  from  overlapping them. The edge is
              chosen based on the alignment option. [B]Override windows  are  not
              under the control of the window manager. _Hints are ignored._ This
              type of window can be useful for certain situations.[/B]
```

So.. I'm not sure why it made any difference.

If the problem comes back, try switching own_window_type to desktop. It sounds like the right option for the job.

---

### Post by Quackers on 2010-08-23
In my many conky difficulties I have tried the desktop type window and the conky display includes a surround (like any normal window).
It does seem strange how it has worked, but I have rebooted since and all is well. I'll keep an eye on it! Just one :-)

---

