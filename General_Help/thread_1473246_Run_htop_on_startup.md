---
title: "Run htop on startup"
date: 2010-05-05
forum: General Help
---

### Post by bolenjx1 on 2010-05-05
Is it possible to have htop run automatically after I login? If it's too much to ask, it would be great if that specific htop window is locked on the upper right corner of my screen and is a bit transparent (more opacity). 

I'm looking for something similar to this one: [http://ubuntuforums.org/attachment.php?attachmentid=106256&d=1236934676](http://ubuntuforums.org/attachment.php?attachmentid=106256&d=1236934676)

Thanks

---

### Post by wilee-nilee on 2010-05-05
Go to preferences-startup applications, click add then put htop in the command. This will just have one version of htop shown, I suspect you need a bash script to reproduce the screen shot. Which I have no idea how to write, but others do.

---

### Post by NearlyALaugh on 2010-05-05
If you wanted to open an ordinary terminal window with htop on startup, you would have to add```
gnome-terminal -x htop
```to your startup script.

However, take a look at this page from the Arch Linux wiki which describes how to do what you want:

[http://wiki.archlinux.org/index.php/Terminal_as_a_Transparent_Wallpaper](http://wiki.archlinux.org/index.php/Terminal_as_a_Transparent_Wallpaper)

---

### Post by wilee-nilee on 2010-05-05
> **NearlyALaugh said:**
> If you wanted to open an ordinary terminal window with htop on startup, you would have to add```
gnome-terminal -x htop
```to your startup script.

However, take a look at this page from the Arch Linux wiki which describes how to do what you want:

[http://wiki.archlinux.org/index.php/Terminal_as_a_Transparent_Wallpaper](http://wiki.archlinux.org/index.php/Terminal_as_a_Transparent_Wallpaper)

Thanks for the info. ;)

---

### Post by NearlyALaugh on 2010-05-05
You might have to do some fiddling with the instructions to make it work with Compiz.

Alternatively, you could use the "Window Rules" plugin in the CompizConfig Settings Manager to try to do the same thing without the use of "devilspie".


Edit:

I was curious so I did it myself (following method #2 in the tutorial).

1. Install **devilspie** and **compizconfig-settings-manager**.

2. Configure devilspie:```
cd ~
mkdir .devilspie
gedit .devilspie/DesktopConsole.ds
```into that file, paste```
(if
	(matches (window_name) "DesktopConsole")
		(begin
			(undecorate)
			(geometry "640x1000+640+0")
		)
)
```and save, modifying if necessary.

2½. Configure compiz:

Open compizconfig-settings-manager under preferences, enable the "Window Rules" plugin, and paste "title=DesktopConsole" into these fields:[list][*]Skip taskbar
[*]Skip pager
[*]Below
[*]Sticky
[*]Non movable windows
[*]Non resizable windows
[*]Non minimizable windows
[*]Non maximizable windows
[*]Non closable windows[/list]

(Using only the devilspie method made the new window misbehave. If you don't have compiz, maybe you won't have a problem.)

3. Create a custom gnome-terminal profile as per the [instructions](http://wiki.archlinux.org/index.php/Terminal_as_a_Transparent_Wallpaper#Step_3).

4. Try the following commands:```
devilspie &
gnome-terminal --window-with-profile=DesktopConsole --title=DesktopConsole -x htop
```If they give you what you want, then add them into your startup session. If not, do some tweaking.

See the attached screenshot for the effect I got. I don't think I'll use it myself since it seems rather messy; **conky** (visible top left) is good enough for me. But thanks for the interesting question!

---

