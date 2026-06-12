---
title: "AWN-Manager does not start"
date: 2009-10-29
forum: General Help
---

### Post by razorboy5 on 2009-10-29
Hi

I've had some installation problems with awn yesterday but now i got it working

however i cannot open the AWN-manager

tried System>Pref>Awn Manager 
right click awn - dock properties

when i run awn-manager in terminal

```

daniel@daniel-gateway:~$ awn-manager
/usr/bin/awn-manager:72: GtkWarning: Theme directory 8x8/stock/generic of theme GlassDark has no size field

  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=defs.I18N_DOMAIN)
/usr/bin/awn-manager:72: GtkWarning: Theme directory 12x12/stock/generic of theme GlassDark has no size field

  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=defs.I18N_DOMAIN)
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 220, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 136, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 109, in __init__
    self.setup_look(defs.BAR, defs.BAR_ANGLE, self.wTree.get_widget("look"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 363, in setup_look
    self.changed_look(dropdown)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 377, in changed_look
    self.reload_look(0, dropdown)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 368, in reload_look
    if self.client.get_int(defs.BAR, defs.BAR_ANGLE) == 0:
glib.GError: Type mismatch: Expected `int' got `float' for key /apps/avant-window-navigator/bar/bar_angle

```tried a few methods i found on google with no success

i installed using the terminal

sudo apt-get remove --purge
sudo apt-get autoremove
sudo apt-get install avant-window-navigator

---

### Post by razorboy5 on 2009-10-30
i remember the first time i installed it the manager did pop up however the dock did not

so i did a reinstall now dock shows up but not the manager

also i tried cairo dock again that does not seem to work for me either... installed through software centre

---

### Post by lvqier on 2009-10-31
I've got the same bug since I upgraded my ubuntu form 9.04 to 9.10.
Now I solved it temporarily by editing the file /usr/share/avant-window-navigator/awn-manager/awnPreferences.py
at line 368:
change 

```

if self.client.get_int(defs.BAR, defs.BAR_ANGLE) == 0:

```
to
```

if self.client.get_float(defs.BAR, defs.BAR_ANGLE) == 0:

```

but i got another problem quickly:
when i changing the look of the bar appearance to 3Dlook
the bar angle cat not work correctly......

May u good luck!

---

### Post by razorboy5 on 2009-10-31
thx alot :P
works great now

---

### Post by oktapod on 2009-11-01
That's for me too. 
awn-manager worked when I installed it from Ubuntu Software Center, but when I installed avant-window-navigator from Synaptic, awn-manager didn't run and awn itself worked.

By modifying the line 368 it's working fine.
Thank you guys.

---

### Post by fabounet on 2009-11-02
if you install Cairo-Dock, please use the official repository, as it is always more recent and stable than the version in Ubuntu.
see wiki.cairo-dock.org for the easy installation way.

---

### Post by koleoptera on 2009-11-02
I've got the same bug since I upgraded my ubuntu form 9.04 to 9.10.
Now I solved it temporarily by editing the file /usr/share/avant-window-navigator/awn-manager/awnPreferences.py
at line 368:
change

Code:

if self.client.get_int(defs.BAR, defs.BAR_ANGLE) == 0:

to
Code:

if self.client.get_float(defs.BAR, defs.BAR_ANGLE) == 0:

Tried to do the above, but this file belongs to the root directory, which is beyond the reach of any user. How do we change permissions in order to change files in system directory?
Any help guys I am a newbie............:(

---

### Post by tom.swartz07 on 2009-11-02
> **koleoptera said:**
> 

Tried to do the above, but this file belongs to the root directory, which is beyond the reach of any user. How do we change permissions in order to change files in system directory?
Any help guys I am a newbie............:(

open a terminal and use 

```
sudo gedit /usr/share/avant-window-navigator/awn-manager/awnPreferences.py
```

then type your changes.

that will open the text editor (gedit) with the root user permissions.

---

### Post by koleoptera on 2009-11-03
Great it worked for me too.. thanks alot...

---

### Post by juan-sx on 2009-11-08
same problem after upgrade ubuntu from 9.04 to 9.10
and works great :p

---

### Post by Ahmedfarid on 2009-12-08
The same problem.
I fixed it with the above steps but still dose not work properly. You can fix the 3D look from the  bar appearance
Bar angel (60)
then it will work fine but still it will not be stable.

---

