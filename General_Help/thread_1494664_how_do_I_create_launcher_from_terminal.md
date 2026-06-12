---
title: "how do I create launcher from terminal?"
date: 2010-05-27
forum: General Help
---

### Post by d3v1150m471c on 2010-05-27
You know when you right click the screen and you can make a launcher with a custom command? Okay...how would I do that from the terminal?

---

### Post by jerrrys on 2010-05-27
this any help?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=create+launcher+in+terminal&as_qdr=all&sa=Google+Search&lang=en#909](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=create+launcher+in+terminal&as_qdr=all&sa=Google+Search&lang=en#909)

---

### Post by d3v1150m471c on 2010-05-28
not quite, unless i missed something. i'm looking for a command or series of commands that i could implement from a terminal or in a bash script that would create a launcher for specific command **on the desktop. **nonetheless, thanks for the help.

---

### Post by patchwork on 2010-05-28
If you are trying to execute a script or a GUI application, create a softlink using the ln -s command:

```
ln -Ts target_script_or_command ~/Desktop/launch_foo
```

If you want to run a command in a terminal from the launcher, create a script first, and then link the script to the Desktop.

More info:

```
man ln
```

---

### Post by d3v1150m471c on 2010-05-28
I actually like that better than the typical launcher and it works perfect. I have an off topic question if you don't mind. Say I created the new launcher with the command you just showed me. Do you know a command that would alter the picture or icon of the shortcut (launcher) that is created?

---

### Post by patchwork on 2010-05-28
Sorry, not sure about that.  I'm sure there is someone around who does, though.

---

### Post by sisco311 on 2010-05-28
A launcher is a .desktop file. For the full specification see: [http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

It's a plain text file, you can use your favorite text editor to create it.

Here is an example of a desktop entry file:
```

[Desktop Entry]
Type=Application
Version=1.0
Encoding=UTF-8
Exec=**command**
Icon=**icon**
Name=**name**
GenericName=**description**
```

In a script you can use something like:
```
cat << **EOF** >> filename.desktop
[Desktop Entry]
Type=Application
Version=1.0
Encoding=UTF-8
Exec=**command**
Icon=**icon**
Name=**name**
GenericName=**description**
**EOF**
```

---

