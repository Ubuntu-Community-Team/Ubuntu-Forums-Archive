---
title: "zombie program using huge resources"
date: 2012-10-06
forum: General Help
---

### Post by Ol'manScratch on 2012-10-06
I've been seeing a lot of resources being sucked up and continual net activity, but I can't figure out what is causing it.
The system monitor show a process name "SH" status "zombie" %cpu "0" nice "0"
ID "1926" memory "N/A do_exit"
Everything else is listed as sleeping except the system monitor.
But there is constant modem activity and it slows down my system.
I've tried killing it, but it's still sucking resources.
What is this problem and what can I do to fix it?
Thanks

---

### Post by Habitual on 2012-10-06
```
lsof -p 1926
``` will show you what files are open by that process.
```
sudo kill 1926
``` will kill it.

Post output of lsof command please.
Don't forget code tags please. :)
[noparse]```

```[/noparse] around output.

Thank you.

---

### Post by Ol'manScratch on 2012-10-06
Habitual

Here is what comes up in terminal. I don't know how to interpret all this, so more help will be appreciated. Should I go ahead and kill it, or will you need this data?
 

jess@jess-desktop:~$ lsof -p 1926
COMMAND    PID USER   FD   TYPE             DEVICE SIZE/OFF    NODE NAME
gnome-scr 1926 jess  cwd    DIR                8,1     4096       2 /
gnome-scr 1926 jess  rtd    DIR                8,1     4096       2 /
gnome-scr 1926 jess  txt    REG                8,1   132096   10219 /usr/bin/gnome-screensaver
gnome-scr 1926 jess  mem    REG                8,1    35528 2228593 /usr/lib/gio/modules/libdconfsettings.so
gnome-scr 1926 jess  mem    REG                8,1    23088 1052142 /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
gnome-scr 1926 jess  mem    REG                8,1    60112 1053577 /usr/lib/gtk-3.0/3.0.0/theming-engines/libunico.so
gnome-scr 1926 jess  mem    REG                8,1    55176 2228277 /lib/x86_64-linux-gnu/libudev.so.0.12.0
gnome-scr 1926 jess  mem    REG                8,1    94552 3019225 /usr/lib/gvfs/libgvfscommon.so
gnome-scr 1926 jess  mem    REG                8,1   177128 2233972 /usr/lib/gio/modules/libgvfsdbus.so
gnome-scr 1926 jess  mem    REG                8,1    26776  393552 /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
gnome-scr 1926 jess  mem    REG                8,1   178424  393555 /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
gnome-scr 1926 jess  mem    REG                8,1    39184   16239 /usr/lib/libltdl.so.7.3.0
gnome-scr 1926 jess  mem    REG                8,1    67984  393898 /usr/lib/x86_64-linux-gnu/libtdb.so.1.2.9
gnome-scr 1926 jess  mem    REG                8,1    31016  393468 /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3.3.4
gnome-scr 1926 jess  mem    REG                8,1    64288   12489 /usr/lib/libcanberra.so.0.2.5
gnome-scr 1926 jess  mem    REG                8,1    18784    7025 /usr/lib/libcanberra-gtk3.so.0.1.8
gnome-scr 1926 jess  mem    REG                8,1    23072 1054787 /usr/lib/gtk-3.0/modules/libcanberra-gtk3-module.so
gnome-scr 1926 jess  mem    REG                8,1    51736 2229734 /lib/x86_64-linux-gnu/libnss_files-2.13.so
gnome-scr 1926 jess  mem    REG                8,1    47696 2229740 /lib/x86_64-linux-gnu/libnss_nis-2.13.so
gnome-scr 1926 jess  mem    REG                8,1    97256 2229481 /lib/x86_64-linux-gnu/libnsl-2.13.so
gnome-scr 1926 jess  mem    REG                8,1    35712 2229495 /lib/x86_64-linux-gnu/libnss_compat-2.13.so
gnome-scr 1926 jess  mem    REG                8,1    60720   10569 /usr/lib/liboverlay-scrollbar3-0.2.so.0.0.11
gnome-scr 1926 jess  mem    REG                8,1  5780288 3145742 /usr/lib/locale/locale-archive
gnome-scr 1926 jess  mem    REG                8,1    22496  394360 /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
gnome-scr 1926 jess  mem    REG                8,1    10328  394333 /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
gnome-scr 1926 jess  mem    REG                8,1   170024 2229158 /lib/x86_64-linux-gnu/libexpat.so.1.5.2
gnome-scr 1926 jess  mem    REG                8,1    14768 2229606 /lib/x86_64-linux-gnu/libdl-2.13.so
gnome-scr 1926 jess  mem    REG                8,1   243800 2234241 /lib/x86_64-linux-gnu/libpcre.so.3.12.1
gnome-scr 1926 jess  mem    REG                8,1    30896  394158 /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
gnome-scr 1926 jess  mem    REG                8,1    18824  397067 /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.3000.0
gnome-scr 1926 jess  mem    REG                8,1    43432  393822 /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
gnome-scr 1926 jess  mem    REG                8,1   112992  394463 /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
gnome-scr 1926 jess  mem    REG                8,1    34824  393810 /usr/lib/x86_64-linux-gnu/libxcb-render.so.0.0.0
gnome-scr 1926 jess  mem    REG                8,1    10248  393816 /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0.0.0
gnome-scr 1926 jess  mem    REG                8,1   162776 2231870 /lib/x86_64-linux-gnu/libpng12.so.0.46.0
gnome-scr 1926 jess  mem    REG                8,1   620776  393481 /usr/lib/x86_64-linux-gnu/libfreetype.so.6.6.2
gnome-scr 1926 jess  mem    REG                8,1   473344  393803 /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.22.2
gnome-scr 1926 jess  mem    REG                8,1   101192 2229484 /lib/x86_64-linux-gnu/libresolv-2.13.so
gnome-scr 1926 jess  mem    REG                8,1   117720 2233675 /lib/x86_64-linux-gnu/libselinux.so.1
gnome-scr 1926 jess  mem    REG                8,1    96816 2228656 /lib/x86_64-linux-gnu/libz.so.1.2.3.4
gnome-scr 1926 jess  mem    REG                8,1    10208  393868 /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
gnome-scr 1926 jess  mem    REG                8,1    10192  393856 /usr/lib/x86_64-linux-gnu/libXcomposite.so.1.0.0
gnome-scr 1926 jess  mem    REG                8,1    39184  393864 /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
gnome-scr 1926 jess  mem    REG                8,1    63800  393877 /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
gnome-scr 1926 jess  mem    REG                8,1    10360  393876 /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
gnome-scr 1926 jess  mem    REG                8,1    14472  397068 /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3000.0
gnome-scr 1926 jess  mem    REG                8,1   220896  393799 /usr/lib/x86_64-linux-gnu/libfontconfig.so.1.4.4
gnome-scr 1926 jess  mem    REG                8,1   302456  394179 /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0.2903.0
gnome-scr 1926 jess  mem    REG                8,1   176080  394180 /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0.2903.0
gnome-scr 1926 jess  mem    REG                8,1    34832  393920 /usr/lib/x86_64-linux-gnu/libcairo-gobject.so.2.11000.2
gnome-scr 1926 jess  mem    REG                8,1   137944  397072 /usr/lib/x86_64-linux-gnu/libatk-1.0.so.0.20209.1
gnome-scr 1926 jess  mem    REG                8,1    22504  393860 /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
gnome-scr 1926 jess  mem    REG                8,1    52416  394182 /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0.2903.0
gnome-scr 1926 jess  mem    REG                8,1    34920  393880 /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
gnome-scr 1926 jess  mem    REG                8,1   125992  393491 /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
gnome-scr 1926 jess  mem    REG                8,1   538928 2229703 /lib/x86_64-linux-gnu/libm-2.13.so
gnome-scr 1926 jess  mem    REG                8,1    31752 2228994 /lib/x86_64-linux-gnu/librt-2.13.so
gnome-scr 1926 jess  mem    REG                8,1  1694008 2229746 /lib/x86_64-linux-gnu/libc-2.13.so
gnome-scr 1926 jess  mem    REG                8,1    22672  393963 /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
gnome-scr 1926 jess  mem    REG                8,1  1277312  393443 /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
gnome-scr 1926 jess  mem    REG                8,1    77696  394522 /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
gnome-scr 1926 jess  mem    REG                8,1  1003848 2233677 /lib/x86_64-linux-gnu/libglib-2.0.so.0.3000.0
gnome-scr 1926 jess  mem    REG                8,1   326984  397066 /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3000.0
gnome-scr 1926 jess  mem    REG                8,1   766024  393830 /usr/lib/x86_64-linux-gnu/libcairo.so.2.11000.2
gnome-scr 1926 jess  mem    REG                8,1  1311808  394810 /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.3000.0
gnome-scr 1926 jess  mem    REG                8,1   506536   10961 /usr/lib/libgdk-3.so.0.200.0
gnome-scr 1926 jess  mem    REG                8,1  4506592   10962 /usr/lib/libgtk-3.so.0.200.0
gnome-scr 1926 jess  mem    REG                8,1   164816   16136 /usr/lib/libgnome-desktop-3.so.2.0.2
gnome-scr 1926 jess  mem    REG                8,1   135500 2229595 /lib/x86_64-linux-gnu/libpthread-2.13.so
gnome-scr 1926 jess  mem    REG                8,1   276392 2229156 /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
gnome-scr 1926 jess  mem    REG                8,1   156272  393972 /usr/lib/x86_64-linux-gnu/libdbus-glib-1.so.2.2.0
gnome-scr 1926 jess  mem    REG                8,1   141088 2229735 /lib/x86_64-linux-gnu/ld-2.13.so
gnome-scr 1926 jess  DEL    REG                8,1           527300 /home/jess/.config/dconf/user
gnome-scr 1926 jess  mem    REG                8,1   160101 1707222 /usr/share/glib-2.0/schemas/gschemas.compiled
gnome-scr 1926 jess  mem    REG                8,1   117272 1835759 /usr/share/mime/mime.cache
gnome-scr 1926 jess  mem    REG                8,1      176 2504346 /home/jess/.local/share/mime/mime.cache
gnome-scr 1926 jess  DEL    REG                8,1           525003 /home/jess/.cache/dconf/user
gnome-scr 1926 jess  mem    REG                8,1     3443 2230929 /usr/share/locale-langpack/en/LC_MESSAGES/gtk30.mo
gnome-scr 1926 jess    0u   CHR                1,3      0t0    5176 /dev/null
gnome-scr 1926 jess    1u   CHR                1,3      0t0    5176 /dev/null
gnome-scr 1926 jess    2u   CHR                1,3      0t0    5176 /dev/null
gnome-scr 1926 jess    3u  unix 0x0000000000000000      0t0   31458 socket
gnome-scr 1926 jess    4u   CHR                1,3      0t0    5176 /dev/null
gnome-scr 1926 jess    5u  0000                0,9        0    5167 anon_inode
gnome-scr 1926 jess    6u  unix 0x0000000000000000      0t0   31459 socket
gnome-scr 1926 jess    7u  0000                0,9        0    5167 anon_inode
gnome-scr 1926 jess    8u  unix 0x0000000000000000      0t0   31863 socket
gnome-scr 1926 jess    9u  unix 0x0000000000000000      0t0   31864 socket
gnome-scr 1926 jess   10u  unix 0x0000000000000000      0t0   31867 socket
gnome-scr 1926 jess   11u  0000                0,9        0    5167 anon_inode
gnome-scr 1926 jess   12u  0000                0,9        0    5167 anon_inode
gnome-scr 1926 jess   13r  0000                0,9        0    5167 anon_inode

---

### Post by Ol'manScratch on 2012-10-06
> **Habitual said:**
> ```
lsof -p 1926
``` will show you what files are open by that process.
```
sudo kill 1926
``` will kill it.

Post output of lsof command please.
Don't forget code tags please. :)
[noparse]```

```[/noparse] around output.

Thank you.
Also,
why are there processes running when the system monitor shows 0 resources being used?
This is what's showing in monitor.

---

### Post by mittwit on 2012-10-06
gnome-scr would be the screen saver process so you could check your screen saver settings.

---

### Post by Habitual on 2012-10-06
Jess:
gnome-screensaver seems to be doing "something" with some Video function(s) ...(libogg).
```
gnome-scr 1926 jess  mem    REG                8,1    26776  393552 /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
gnome-scr 1926 jess  mem    REG                8,1   178424  393555 /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
```Custom slideshow is the only thing that comes to mind. Maybe it's scanning your ~/Pictures directory? 
I don't use gnome, and when I did, I never used gnome-screensaver or custom screensaver 'material', so it is an uneducated guess.

JJ

Please let us know...

P.S. You forgot the code tags, you can always edit that one post and add them. :)
[noparse]```

```[/noparse] around output.

---

### Post by Ol'manScratch on 2012-10-06
[B]P.S. You forgot the code tags, you can always edit that one post and add them. :smile:
```

``` around output.[/B]

Sorry, I don't know what you mean by code tags.

The screen saver thing might have been from me staying in Firefox with pages displayed while copying the log file you wanted. I'm out of all of it now.

When I used the command "lsof -p 1926" in the terminal, it worked the first time it Now doesn't work now.
And the command "sudo kill 1926" shows command not found.

I know this should be easy, but I'm still seeing continuous high traffic through my DSL connection. This is what I want to fix.

One final thing: I wanted to copy the info shown in my system monitor to send, but all I get is the top part of what is shown.
How do I copy the entire output to send to you?

As always when I try to do a task in Ubuntu I get lost in the weeds, eat up hours and hours and still don't get what I need to fix. Can someone find me a solution to that?

Thanks

---

### Post by Habitual on 2012-10-06
> **Ol'manScratch said:**
> [B]P.S. You forgot the code tags, you can always edit that one post and add them. :smile:
 around output.[/B]

Sorry, I don't know what you mean by code tags....

No code tags ...
gnome-scr 1926 jess   10u  unix 0x0000000000000000      0t0   31867 socket
gnome-scr 1926 jess   11u  0000                0,9        0    5167 anon_inode
gnome-scr 1926 jess   12u  0000                0,9        0    5167 anon_inode
gnome-scr 1926 jess   13r  0000                0,9        0    5167 anon_inode

with code tags:...
```
gnome-scr 1926 jess   10u  unix 0x0000000000000000      0t0   31867 socket
gnome-scr 1926 jess   11u  0000                0,9        0    5167 anon_inode
gnome-scr 1926 jess   12u  0000                0,9        0    5167 anon_inode
gnome-scr 1926 jess   13r  0000                0,9        0    5167 anon_inode
```You can either add the [noparse]```

```[/noparse] yourself, or highlight the entire text that IS code and use the "#" button in the editor. **If you go back to edit a previous post, you may have to select "Go Advanced" to "see" the "#" button in the editor.**

It's not firefox. Try to stay with me, It's your gnome-screensaver :)
"lsof -p 1926" will come up blank if you killed it.

---

### Post by wheeze on 2012-10-06
Sorry if this is a dumb idea, but can you just log out of your session and log back in again?

It could be something that just got hung up and logging out/in might just stop it and restore normalcy.

---

### Post by Ol'manScratch on 2012-10-07
Well, what's interesting is that when I shut down FIREFOX and went to Chrome the high traffic pretty much stopped.
I guess the problem is temporarily fixed - Of course I still don't know how or why.
I really want to learn Ubuntu better, but the time factor kills me. So it goes.

Thank you all for your help on this. Sometimes stuff just makes me crazy. Doh!

---

### Post by vasa1 on 2012-10-07
I'm wondering about whether "zombie" programs use huge resources (by definition).

---

### Post by Habitual on 2012-10-07
> **wheeze said:**
> Sorry if this is a dumb idea, but can you just log out of your session and log back in again?

It could be something that just got hung up and logging out/in might just stop it and restore normalcy.

Wheeze:
Ah, the low-tech approach. It's a Grand Idea and it's probably what I'd do first and foremost for myself. It sounds like Jess has it nailed down to Firefox (I've heard that across various forums...), I went with the info he gave me... 
Sometimes it's hard to really know the situation when you or I may know a lot and a screen full of pidof output is 'normal' to us, to a new user it must seem like overload. Every detail must be important!

I remember compiling my first kernel manually in my first days as a Linux user, all that text flying by, I asked my telephone-call-away Linux guru "Is that filling up my hard drive?" to which replied "No, just text on the screen".

I thought it was important to *know* what was flying across my screen, important or not.

Jess:

If you see or suspect another zombie process, you could logout and back in, if it still persists, open a terminal and paste this in
```
ps aux | awk '{ print $8 " " $2 }' | grep -w Z | awk '{print $2}'
``` This will show you the Process ID (always numeric) or PIDs of any truly zombied processes on the system.
Then do a```
top p <PID>
``` You will see the name of the zombied process.

If that is too much for you to take on, then I'd have to ask...
how much system RAM you have in your computer and 
Does a logout and login alleviate the symptoms? 
How about a reboot and login? Any sign of issue? 
Does closing Firefox help at all? 
Did you check your gnome-screensaver settings?

"[On Unix operating systems, a zombie process or defunct process is a  process that has completed execution but still has an entry in the  process table, allowing the process that started it to read its exit  status.]("http://wiki.answers.com/Q/What_is_Zombie_Process_and_Orphan_Process")"

Please don't take multi-vector approaches or replies as contrary, as in Linux there is definitely more than one way to get things done. 

Please let us know.

Have a Great Day!

---

