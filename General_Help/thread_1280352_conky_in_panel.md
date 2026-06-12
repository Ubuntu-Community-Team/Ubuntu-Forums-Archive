---
title: "conky in panel?"
date: 2009-10-01
forum: General Help
---

### Post by sopadeajo on 2009-10-01
I downloaded conky which is situated in /usr/bin, but i had to go there and double click on the conky file to get it working. Is there a way to keep it somewhere in the panel?

Is there a way to view its results with larger characters ? (jaunty)

---

### Post by yabbadabbadont on 2009-10-02
No, conky can not be displayed in the panel.  It draws either on the root window pixmap or its own window (which is usually transparent and without borders).

There are several conky tutorial threads in the forums and one gigantic thread in the Cafe that is loaded with tips and tricks for using conky.

---

### Post by ninjapirate89 on 2009-10-02
You can't display conky in the panel, but you can create a launcher to start it. Just right click on the panel, Add to Panel, Custom Application Launcher, put in Conky for the name and conky for the command and a description if you want. Click ok and you will have an icon to click to start conky.

---

### Post by MaxIBoy on 2009-10-02
I prefer to have it start up automatically at boot. 


Just go to system>preferences>Startup Applications (It may have a different name, but the icon is a white arrow on a blue background.)

Click "Add," then type Conky for the name and "conky" for the command. Click "add" again and now Conky is run automatically when you boot up.


(By the way, since /usr/bin is in your PATH, you can also just pull up a terminal or hit alt+f2 and type "conky", you don't need to browse to /usr/bin. PATH is a system setting which is a list of folders, where the system will automatically look for programs to run. If you type conky, it will look in a number of folders, including /usr/bin, for a file named conky which it will then run when it finds it. You can add new folders to your PATH as well if you want custom locations for programs. Learn more about the PATH setting here: [http://www.cs.purdue.edu/homes/cs541/unix_path.html](http://www.cs.purdue.edu/homes/cs541/unix_path.html))


EDIT: you can make characters larger using the font setting. Edit the file .conkyrc in your home folder, this contains settings for conky. All files which have names starting with a dot "." are hidden, so you need to show hidden files with "view>show hidden files" in your file browser. You should see some text like this:
```
# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8
```
You can change the size, for example if you want font size 12:
```
# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=12
```

---

### Post by sopadeajo on 2009-10-02
> **MaxIBoy said:**
> I prefer to have it start up automatically at boot. 


Just go to system>preferences>Startup Applications (It may have a different name, but the icon is a white arrow on a blue background.)

Click "Add," then type Conky for the name and "conky" for the command. Click "add" again and now Conky is run automatically when you boot up.


(By the way, since /usr/bin is in your PATH, you can also just pull up a terminal or hit alt+f2 and type "conky", you don't need to browse to /usr/bin. PATH is a system setting which is a list of folders, where the system will automatically look for programs to run. If you type conky, it will look in a number of folders, including /usr/bin, for a file named conky which it will then run when it finds it. You can add new folders to your PATH as well if you want custom locations for programs. Learn more about the PATH setting here: [http://www.cs.purdue.edu/homes/cs541/unix_path.html](http://www.cs.purdue.edu/homes/cs541/unix_path.html))


EDIT: you can make characters larger using the font setting. Edit the file .conkyrc in your home folder, this contains settings for conky. All files which have names starting with a dot "." are hidden, so you need to show hidden files with "view>show hidden files" in your file browser. You should see some text like this:
```
# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8
```You can change the size, for example if you want font size 12:
```
# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=12
```

Thanks to all for your good informations.


Nevertheless there is not a .conkyrc among the hidden files of my home folder nor in usr/bin and i guess that without this file no conky configuration is possible.

---

### Post by sopadeajo on 2009-10-03
Do this in terminal:
sudo gedit /etc/conky/conky.conf

This will allow you to edit the conky configuration file which is situated in etc/conky (in Jaunty)

You"ll see this:

alignment bottom_left
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_class Conky
own_window_type normal
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer no
show_graph_scale no
show_graph_range no


Replace font 6x10 by font 7x13 or 8x13 or 9x15 and save. (do not know if there are other possible values, did not try) and you'll get conky automatically resized to fit to the new size of the characters. A well written program, indeed!

---

### Post by sopadeajo on 2009-10-04
> **sopadeajo said:**
> I downloaded conky which is situated in /usr/bin, but i had to go there and double click on the conky file to get it working. Is there a way to keep it somewhere in the panel?

Is there a way to view its results with larger characters ? (jaunty)

Well, there is in fact a way not to keep directly it in the panel, but to get it started by clicking on a Custom Application Launcher Added to Panel in which we write conky as name and conky as command.

See also:
[http://ubuntuforums.org/showthread.php?t=1281795](http://ubuntuforums.org/showthread.php?t=1281795)

---

