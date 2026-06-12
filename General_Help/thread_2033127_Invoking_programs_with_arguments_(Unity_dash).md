---
title: "Invoking programs with arguments (Unity dash)"
date: 2012-07-25
forum: General Help
---

### Post by ArlieS on 2012-07-25
Many unix programs take large numbers of arguments. This includes some that it would be convenient to launch from the GUI, rather than launching from an xterm window. One example is xterm itself ;-) 

Unfortunately there's no obvious way to provide arguments to programs started from the dash - or for that matter, from the vertical bar below the dash, and there's no discussion of it in the only good (newbie) guide to Unity I've so far found. ( [http://www.youtube.com/watch?v=xA9EHaNc2VI](http://www.youtube.com/watch?v=xA9EHaNc2VI))

Is this possible, or is the "familiar windows environment" too important to allow convenient argument passing?

---

### Post by cariboo on 2012-07-25
You can create or modify a launcher with the parameters needed, and locate it in ~/.local/share/applications, for example I have an icon in my launcher that uses a quicklist to remotely access a couple of servers eg:

```
[Desktop Entry]
Version=1.0
Name=Remote Servers
Comment=Login to my servers
Exec=gnome-terminal --disable-factory --sm-client-disable --class=remoteserver -x ssh -t willy 
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=utilities-terminal
StartupNotify=true
StartupWMClass=RemoteServers
X-Ayatana-Desktop-Shortcuts=Server1;
X-Ayatana-Desktop-Shortcuts=Server2;

[Server1 Shortcut Group]
Name=SSH into willy
Exec=gnome-terminal --disable-factory --sm-client-disable  --class=remoteserver -x ssh -t willy
TargetEnvironment=Unity

[Server2 Shortcut Group]
Name=SSH into Likely
Exec=gnome-terminal --disable-factory --sm-client-disable --class=remoteserver -x ssh -t likely
TargetEnvironment=Unity
```

Note the Exec line in the above output.

---

### Post by HiImTye on 2012-07-27
you can just alt+f2 and type in the command you want

---

### Post by O2Blevel on 2012-07-27
You could also modify the properties section of the 'Main Menu' gui.

---

### Post by ArlieS on 2012-07-27
> **HiImTye said:**
> you can just alt+f2 and type in the command you want

Great - I didn't know about alt-f2. That solves a lot of problems.

---

### Post by ArlieS on 2012-07-27
> **O2Blevel said:**
> You could also modify the properties section of the 'Main Menu' gui.

Where do I start? I haven't even found a main menu, just the things in the left bar. And now (with your hint) a kind of desktop menu, which lacks an item to change desktop properties, though at least you can change the desktop background. 

Unity's obviously got a lot of useful abilities, but they've hidden them a little too well. (It took me at least a day to figure out how to get access to the menus associated with whatever application I was running, as an example, and if I hadn't used a mac recently, it would have taken longer.)

---

### Post by O2Blevel on 2012-07-27
> **ArlieS said:**
> Where do I start? I haven't even found a main menu, just the things in the left bar. And now (with your hint) a kind of desktop menu, which lacks an item to change desktop properties, though at least you can change the desktop background. 

Unity's obviously got a lot of useful abilities, but they've hidden them a little too well. (It took me at least a day to figure out how to get access to the menus associated with whatever application I was running, as an example, and if I hadn't used a mac recently, it would have taken longer.)

You can launch Main Menu from the dash. Find the program you want to modify, open properties and change Command to whatever. I'm not sure if it will have all your programs but it does have quite a few.

---

