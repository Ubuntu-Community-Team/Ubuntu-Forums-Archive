---
title: "Compiz/XGL installed (i think) how do i make it look pretty?"
date: 2006-05-13
forum: General Help
---

### Post by eggmanpete on 2006-05-13
Hi there, im just getting to know linux and i though i might try this compiz/xgl everyone is talking about. I looked at many howto's but the best one i found was here: [click]("http://compiz.net/viewtopic.php?id=42")
it is done using a script. i followed all instructions and i can choose "Compiz" in the log in screen under "sessions"

i loads and looks exactly like the usual gui :<
is there something i need to enable to get all the shadows/transparancy or whatnot.

Thanks for your help, eggman :)

---

### Post by louis_nichols on 2006-05-13
well... for ubuntu, you might wanna start [here]("http://ubuntuforums.org/showthread.php?t=148351"). It's for dapper.

If you're using Breezy... I don't know if you can actually use xgl/compiz. I saw a thread on this, but didn't see if they found a solution.

---

### Post by eggmanpete on 2006-05-13
thats strange, it seems to have installed though. it wouldnt be in the sessions section of the log-in screen otherwise :S

---

### Post by louis_nichols on 2006-05-13
that doesn't mean it's installed. it appears in that menu because of this section of the howto:
```

echo "[Desktop Entry]
Encoding=UTF-8
Name=Compiz
Comment=Candy store
Exec=/usr/local/bin/compiz.sh
Icon=
Type=Application" > /usr/share/xsessions/compiz.desktop
```

You could just run the command to add an entry there. To really test wether it works, try this command (but be advised that it might leave you with a not completely functional desktop environment -i.e. the window decorator will dissappear and also the ability to control windows):

```
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
```

If this doesn't work and the window decorations aren't there, then, before closing the terminal, run this:

```
metacity --replace &
```

---

### Post by eggmanpete on 2006-05-13
```
eggman@eggman:~$ gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
bash: gnome-window-decorator: command not found
[4] 27942
bash: compiz: command not found
[5] 27943
[4]   Exit 127                gnome-window-decorator
[5]   Exit 127                compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher

```
hmmm, doesn't look good

---

### Post by eggmanpete on 2006-05-13
Ok i give up :< is there any way to get rid of any changes i have made?

---

### Post by louis_nichols on 2006-05-13
Sure! Run this command to uninstall packages:

```
sudo apt-get remove compiz-gnome xserver-xgl
```

Run this command to remove the entry of compiz session from the login menu:

```
sudo rm -f /usr/share/xsessions/compiz.desktop
```

The rest isn't very important.

Also, I suggest you run a search on the Breezy support forum for possible ways to get this working on Breezy. You may wanna do that before un-doing the changes, just in case they can still be used.

---

### Post by eggmanpete on 2006-05-14
Thanks for the reply, im thinking of moving to dapper, is this a good idea? Thanks.

---

### Post by louis_nichols on 2006-05-14
why not? I've been using it for the past 2 weeks without major issues. of course, there is no guarantee that it won't over-burn your food or throw your monitor out the window :) but I guess you never get that in the software world, even when software is out of the beta testing mode

---

### Post by eggmanpete on 2006-05-14
Got dapper :)
I went thorugh the breezy nVidia driver installation : 
```
sudo apt-get install nvidia-glx
``` 
(which is probably not right)
and installed again with the script described in the first post.
My problem now is that everytime i try to run: 
```
sudo /etc/init.d/gdm restart
``` 
it tells me xserver cannot start, but i use startx to make it work.

Is it an nvidia driver problem?

---

### Post by louis_nichols on 2006-05-14
Try using [this thread]("http://www.ubuntuforums.org/showthread.php?t=131267") to make it work. Then refer to [this thread]("http://ubuntuforums.org/showthread.php?t=148351") for further info, workarounds etc. It's what I used to get it up and running. Gdm not starting might be an nvidia driver thing, but it can be something else.

---

### Post by eggmanpete on 2006-05-14
Went through the [first thread]("http://www.ubuntuforums.org/showthread.php?t=131267") instructions fine, and if i boot or type ```
thefuture
``` the screen changes resolution about 4 or 5 times and then tells me X cannot start.

im certain this is something to do with the nvida drivers.
I looked into xorg.conf and in the Device section, the driver says "nv" instead of nvidia :S
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nv"
	BusID		"PCI:2:0:0"
	Option 		"RenderAccel" 		"true"
EndSection
```

Any ideas?

---

### Post by louis_nichols on 2006-05-14
strange. after I installed dapper and then the nvidia drivers, my xorg.conf was fully configured... well, start by editing xorg.conf

```
sudo gedit /etc/X11/xorg.conf
``` and enter nvidia instead of nv. if it doesn't do the trick, then run

nvidia-xconfig

and go back to editing xorg.conf, because you'll have to add the line 

```
Option 		"RenderAccel" 		"true"
``` as it is not added by default. Then restart X and try again.

---

### Post by eggmanpete on 2006-05-14
nvidia-xconfig seems to have made it work. now the sad bit:
my 6800GT artifacts straight after the nVidia startup logo. It does not do this in windows so there must be something that compiz/xgl accesses that screws my card :(

---

