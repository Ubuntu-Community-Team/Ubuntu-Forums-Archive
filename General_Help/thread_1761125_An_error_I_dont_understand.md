---
title: "An error I dont understand"
date: 2011-05-17
forum: General Help
---

### Post by Atsuisofu on 2011-05-17
I was just trying to have a launcher button that runs a command in terminal and opens up the terminal. I have the code down for the most part but when I press the button and run the command it gives me an odd error type message on the terminal window.
It says 
"The child process exited normally with status 0." and it gives me a button to Re-Launch.

My code for .desktop file is below.
```

[Desktop Entry]
Name=Sensors
Comment=
Exec=sensors
Terminal=true
Type=Application
StartupNotify=false
Icon=/usr/share/icons/Humanity/actions/48/thermo.svg

```

Thanks for your time I am not sure as to why this would occur.

---

### Post by TeoBigusGeekus on 2011-05-17
Try changing the line
```
Exec=sensors
```
to
```
Exec=gnome-terminal -e sensors
```

---

### Post by Atsuisofu on 2011-05-17
Thanks for the quick reply. When I try and replace the line of code as you stated above it instead causes two gnome terminals to open one with the sensors output and the other completely blank. They both still have the same error like message "The child process exited normally with status 0."  I am running natty with all recent updates.

---

