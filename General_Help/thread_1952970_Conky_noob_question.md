---
title: "Conky noob question"
date: 2012-04-05
forum: General Help
---

### Post by M_Mynaardt on 2012-04-05
Hi!

I'm pretty new to Conky.  I actually did a bit of copying and modifying of a Conky script I found on Crunchbang Linux that works quite well.  **Except** that its size is rather limited.  It is quite small, actually, unlike the examples of really big Conky displays a lot of Conky enthusiasts post.  I think I'm doing good for modifying as much as I did to have bar displays of the CPU, RAM, Disk use, and battery use on my laptop.

Can someone tell me why it my display would be as small as it is?  And how to make it more, well, spacious, really.  My display, as it is, seems to be limited to about 15 lines of output display.

These are the settings from my **.conky** files, which is about the same for both my PC and laptop.  I'm sure the problem is here somewhere:

```
##############################################
#  Settings
##############################################
background yes
use_xft yes
xftfont mono:size=10
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_argb_visual yes
# I need to be set to "yes" in Xubuntu
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour 233d5d
# background window colour
double_buffer yes
minimum_size 200 200
# maximum_width 240
draw_shades no
draw_outline no
draw_borders yes
draw_graph_borders no
default_color bad3e9
# font colour
alignment top_right
gap_x 10
gap_y 40
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

```

I'm sure it's an easy fix, but I just need a bit of help figuring out how to prissy up Conky for my Xubuntu PC and Lubuntu laptop.  I'd be ever so grateful if someone could give me a few practical tips on this for Conky.
:)

Thanks in advance!

---

### Post by QIII on 2012-04-05
Is it coming up on your screen initially as 200 x 200 (your minimum size)?

---

### Post by stinkeye on 2012-04-05
It's pretty hard to determine what you want it to look like without the rest 
of your config to test or a pic.
Conky will draw to your **minimum_size 200 200** unless what you have
below "TEXT" requires more.

---

### Post by M_Mynaardt on 2012-04-05
Well!  Isn't this fun?!  I tried to make my Conky display longer on my desktop, running under Xubuntu, to get screen-shots to show how it doesn't work.  So, of course, it works just fine!  Typical!
:-k

**On the other hand**, Conky does cut off lines when I try to make the display longer on my laptop, which runs with Lubuntu.  I don't know if the problem is using Conky in Lubuntu or Xubuntu.  But it definitely doesn't let me make the display as big as I'd like with Lubuntu.  This time I've got screen-shots, which I've attached.

The first one is maxed out, without trying to add anything.  The second one has just two lines added: the time and swap bar.  The last two lines end up getting cut off at the bottom of the display box.  Any suggestions as to why I seem to have a maximum number of lines in my Conky display in Lubuntu (but not in Xubuntu, apparently), would be appreciated, and cool, and stuff.

I'm sure there's probably just one, maybe two changes I need to make to my Conky file that might be obvious to someone in the know about Conky (unlike me).  Here's my Conky file from my Lubuntu laptop:
```

##############################################
#
#  LUBUNTU Conky Settings
# 
##############################################
#  Settings
##############################################
background yes
use_xft yes
xftfont mono:size=10
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_colour 101040
# if the Conky display has trouble showing on the desktop because of the colour
# of the wallpaper, set own_window_transparent to "no"
# own_window_argb_value X
# does not seem to work in Lubuntu
# own_window_type desktop
# in Lubuntu, disable this; or Conky display disappears with mouse clicks
# anywhere on the desktop
double_buffer yes
minimum_size 200 200
maximum_width 300
draw_borders yes
draw_graph_borders no
default_color 40b0ff
# original default_color 1010ff
alignment top_right
gap_x 10
# 10 pixels from the right, so the right border isn't obscured
gap_y 34
# 10 pixels below the panel (24 pixels high) so top border is visible
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
##############################################
#  Output
##############################################
TEXT
$alignc LUBUNTU - Powered
$alignc $nodename
${hr}
  Clock: ${time %H:%M:%S}
# not necessary, but it looks nice
 Uptime: $uptime
Battery: $battery_bar
    RAM: $membar
    CPU: $cpubar
   Disk: $fs_bar
   Swap: $swapbar
${hr}
F11$alignr Full Screen
Alt+F1$alignr LXDE Menu
Alt+F2$alignr Run Dialog
Ctrl+Alt+Del$alignr Task Mgr
Ctrl+Alt+L$alignr Lock Scrn
Ctrl+Alt+Lt$alignr Go Left
Ctrl+Alt+Rt$alignr Go Right
Shft+Alt+Lt$alignr Send Left
Shft+Alt+Rt$alignr Send Right

```

Thanks in advance for any help!
):P

---

### Post by QIII on 2012-04-06
Have you gotten any further on this?

If you start conky with a min size of, say, 200x400 and then add lines that exceed the height and save your conkyrc, the next time your conky is redrawn it may not "expand".  I have found this to be true even after changing the min size to make it longer.

Logging out of the session and logging back in seems to fix the issue.

BUT:  I use KDE and that might be a KDE quirk.  Might be worth a try, though.

I can't imagine that your DE has a magical conky size governor.  You should be able to make it so big it will slop over the edges of your screen.

---

### Post by stinkeye on 2012-04-06
QIII is right,
You need to kill conky and restart to change the window size.

Change your first setting in you config to
```
background **[COLOR="Red"]no[/COLOR]**
```


Then when editing use this to start conky (use just "conky" if your config is @ **~/.conkyrc**)
```
conky -c /path/to_your/conkyconfig
```

In the terminal use ctrl+c to kill conky.
Then use the up arrow to bring back the previous command to restart conky.

---

### Post by M_Mynaardt on 2012-04-06
> **QIII said:**
> Have you gotten any further on this?

If you start conky with a min size of, say, 200x400 and then add lines that exceed the height and save your conkyrc, the next time your conky is redrawn it may not "expand".  I have found this to be true even after changing the min size to make it longer.

[COLOR="Green"]**Logging out of the session and logging back in seems to fix the issue.**[/COLOR]

BUT:  I use KDE and that might be a KDE quirk.  Might be worth a try, though.

I can't imagine that your DE has a magical conky size governor.  You should be able to make it so big it will slop over the edges of your screen.

As far as making progress with Conky is concerned; **YES I DID!**
\\:D/

Reading your reply made me realize that in order to update my Conky changes, I would need to log out and back in, or else reboot the computer.  Well, I did just that and, **[COLOR="Purple"]behold![/COLOR]**  It worketh!
=D>

All that time, and it never occurred to me to just restart the session after making a change in my **.conkyrc** file.
](*,)

Seriously, though, I wouldn't have thought of restarting the session to resent Conky had I not read your reply to my post.

Thanks for that!

---

### Post by M_Mynaardt on 2012-04-06
> **stinkeye said:**
> QIII is right,
You need to kill conky and restart to change the window size.

Change your first setting in you config to
```
background **[COLOR="Red"]no[/COLOR]**
```


Then when editing use this to start conky (use just "conky" if your config is @ **~/.conkyrc**)
```
conky -c /path/to_your/conkyconfig
```

In the terminal use ctrl+c to kill conky.
Then use the up arrow to bring back the previous command to restart conky.

I changed the background option to "no", as you suggested.  Seems to work well enough.

As I indicated in my other reply to ***QIII*** it turns out I overlooked one annoyingly obvious thing.  To just restart a session after editing the **conky** file.

All is right with my Lubuntu **conky** file and display.

Thanks so much for the help.

---

### Post by M_Mynaardt on 2012-04-06
Right!  I know all I need do with my Lubuntu Laptop is reboot the computer to get my Conky display looking good and proper after making changes to my **.conkyrc** file.

Therefore, I got bold and tried to spiffy up my Conky display.  And to mess about with some output *stuff* I've not tried out before.  I think the result wasn't too bad.

Thanks for the help, **QIII** and **stinkeye**!
):P

---

### Post by stinkeye on 2012-04-06
Looks good.Nice neon blue.
Just a note. It's not necessary to restart your session.
Just need to restart conky.

---

### Post by M_Mynaardt on 2012-04-06
> **stinkeye said:**
> Looks good.Nice neon blue.
Just a note. It's not necessary to restart your session.
Just need to restart conky.

Right!  Got it!

I knew there had to be an easy fix!

Thanks!

---

### Post by QIII on 2012-04-06
The reason I suggest restarting the session is to be sure that, in the natural order of things, the system and the DE have enough time to get their business done before conky starts to draw.  With a DE like KDE, for instance, it's good to have your startup script sleep for 15 seconds or so.

Maybe not a big problem for lighter DEs, but you make sure that way.

If you make minor changes and adjustments, just the act of saving your conkyrc will redraw your conky just fine.

The real test comes when you log into a session and you want conky to be drawn after things are settled.

---

### Post by M_Mynaardt on 2012-04-07
> **QIII said:**
> The reason I suggest restarting the session is to be sure that, in the natural order of things, the system and the DE have enough time to get their business done before conky starts to draw.  With a DE like KDE, for instance, it's good to have your startup script sleep for 15 seconds or so.

Maybe not a big problem for lighter DEs, but you make sure that way.

If you make minor changes and adjustments, just the act of saving your conkyrc will redraw your conky just fine.

The real test comes when you log into a session and you want conky to be drawn after things are settled.

I think I'm doing pretty good with Conky, all things considered.  I did start by copying the stock Conky configuration from Crunchbang Linux and then tinkering from there.  Don't know if I'll get around to doing the really fancy stuff I see a lot of Conky enthusiasts posting, but I think I'm doing okay for the moment.

As I said, it was just a simple matter of overlooking something *almost* obvious to get things working.  At least now I know that Conky is working just find, and it's restarting Conky or the Lubuntu session that's all that it takes to update the display right and proper.

I guess we all learn by doing and asking, eh?

Thanks again for the help!

---

### Post by QIII on 2012-04-07
If you happen to stop by again --

Play with all of it.  It really is fun.

I started fiddling around and learning things.  I found all sorts of cool things I wanted to add.  I got to the point where I had weather forecasts and rss feeds and all sorts of things.  The conky-est conky of them all.  

But at some point I found that I really didn't need a weather forecast, because I looked at that once in the morning and I didn't need to look at it every 5 minutes all day long.  I had an rss feed going while I was sitting at the computer reading a news web site.  Why?

I had really cool gauges I made with lua, all different colors and artistic placement.

I finally realized that what I really needed was a speedometer, fuel gauge, temperature gauges and such.

My conky now has CPU loads with graphs (for watching "historical" change); load, temp and fanspeed on my graphics cards; memory use; temperature readouts for motherboard components, CPU and disks; CPU fan speed; ethernet traffic, top processes and disk activity.

In short, it monitors meaningful things about my machine in a straight forward, unadorned way.  No more dog and pony show.

---

### Post by M_Mynaardt on 2012-04-07
> **QIII said:**
> If you happen to stop by again --

Play with all of it.  It really is fun.

I started fiddling around and learning things.  I found all sorts of cool things I wanted to add.  I got to the point where I had weather forecasts and rss feeds and all sorts of things.  The conky-est conky of them all.  

But at some point I found that I really didn't need a weather forecast, because I looked at that once in the morning and I didn't need to look at it every 5 minutes all day long.  I had an rss feed going while I was sitting at the computer reading a news web site.  Why?

I had really cool gauges I made with lua, all different colors and artistic placement.

I finally realized that what I really needed was a speedometer, fuel gauge, temperature gauges and such.

My conky now has CPU loads with graphs (for watching "historical" change); load, temp and fanspeed on my graphics cards; memory use; temperature readouts for motherboard components, CPU and disks; CPU fan speed; ethernet traffic, top processes and disk activity.

In short, it monitors meaningful things about my machine in a straight forward, unadorned way.  No more dog and pony show.

Well, just having a cool display of the current status of my computer is what I'd like.  So, I think the CPU and memory gauges go well with the history graphs of each.

I'll probably get around to tinkering with some of the other 'nick-knacks' in Conky at some point too, I"m sure!

---

