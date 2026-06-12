---
title: "Some shell scripting advice please to start an application."
date: 2011-09-01
forum: General Help
---

### Post by bwallum on 2011-09-01
Hello

I'm running QCAD beta 3 on a 64 bit Ubuntu 11.04 system. QCAD is 32 bit and can't run using normal gnome themes. The work-around is to start it in a compatible theme. The programme runs fine when I start it by navigating to the appropriate directory and issuing the command.

The command with the appropriate instruction to start up in a compatible theme mode is:```
./qcad -style plastique
```I have tried to put this into a shell script (my first such venture) which I call qcad3. This is the content:> #!/bin/sh

# Start 32bit QCAD3 with a style compatible with 64bit Ubuntu
./qcad -style plastiqueThe script sits in the folder /home/bob/qcad-3.0.0-beta-prof-linux

If I navigate to that folder, right click on the qcad3 file and run, the programme fires up and runs fine.

If I try and create a launcher with the command > /home/bob/qcad-3.0.0-beta-prof-linux/qcad3 then the icon glows and dims a couple of times (is there a technical term for that?) but nothing further happens.

How can I modify the script or launcher command to make it work by clicking on the launcher icon?

---

### Post by sanderd17 on 2011-09-01
Why don't you delete the script and put everything in the launcher? So that the launcher command is

```

/home/bob/qcad-3.0.0-beta-prof-linux/qcad -style plastique

```

---

### Post by sisco311 on 2011-09-01
If you need to change the working directory, then try:
```
sh -c 'cd /home/bob/whatever && ./qcad -style plastique'
```

Or use the Path key in the .desktop file, ~/.local/share/applications/name.desktop:
```

[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=<name here>
Path=/home/bob/whatever
Exec=./qcad -style plastique
StartupNotify=false
Terminal=false
Hidden=false

```

---

### Post by bwallum on 2011-09-01
> **sanderd17 said:**
> Why don't you delete the script and put everything in the launcher? So that the launcher command is

```

/home/bob/qcad-3.0.0-beta-prof-linux/qcad -style plastique

```
I tried that and nothing happens. qcad is a shell script file with the following content:```
#!/bin/sh

LD_LIBRARY_PATH=. ./qcad-bin $@
```I tried to modify the qcad script with this:```
#!/bin/sh

STYLE=plastique
LD_LIBRARY_PATH=. ./qcad-bin $@
```The startup ran and was visible but as soon as the work screen appeared... it disappeared. That's the same behaviour as the default qcad file script, i.e. the STYLE statement was ineffective.

---

### Post by bwallum on 2011-09-01
> **sisco311 said:**
> If you need to change the working directory, then try:
```
sh -c 'cd /home/bob/whatever && ./qcad -style plastique'
```Or use the Path key in the .desktop file, ~/.local/share/applications/name.desktop:
```

[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=<name here>
Path=/home/bob/whatever
Exec=./qcad -style plastique
StartupNotify=false
Terminal=false
Hidden=false

```
Ok, I've set up a qcad3.desktop file in ~/.local/share/applications, what's the next step?

---

### Post by bwallum on 2011-09-02
> **sisco311 said:**
> If you need to change the working directory, then try:
```
sh -c 'cd /home/bob/whatever && ./qcad -style plastique'
```Or use the Path key in the .desktop file, ~/.local/share/applications/name.desktop:
```

[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=<name here>
Path=/home/bob/whatever
Exec=./qcad -style plastique
StartupNotify=false
Terminal=false
Hidden=false

```

I put ```
sh -c 'cd /home/bob/qcad-3.0.0-beta-prof-linux && ./qcad -style plastique'
```as the command in Create Launcher (right click on Desktop), then dragged it to the launcher side panel and it worked!

Thanks sisco311!

Could you possibly explain what the command is doing, is it something to do with passing the cd command to the shell and then running the qcad command, much as you would using a terminal consol? When normally using the terminal is one running commands directly on the shell?

---

