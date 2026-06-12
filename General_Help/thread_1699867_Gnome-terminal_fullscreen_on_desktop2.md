---
title: "Gnome-terminal fullscreen on desktop2"
date: 2011-03-04
forum: General Help
---

### Post by atb-nl on 2011-03-04
Hello,

i have a question.

On my pc i have ubuntu 10.10 64bit desktop installed.
on this pc i have a server running in a terminal.
the terminal starts when i boot my pc.
the "problem" is that it starts on my primary desktop, the one i see.
i have the default amount of desktops: 4 and desktop cube enabled with compiz.
now i want that the server starts in full-screen mode on my second desktop, so i can switch to it with ctr-alt arrow if i want to.
can this be done ?

this is how i start the server:
i give this command in start-up applications:
```
sh "/home/user/Minecraft Server/run_on_startup.sh"
```
this is the script that starts the gnome terminal:
```
#!/bin/bash
cd "/home/user/Minecraft Server/"
gnome-terminal --title "Minecraft Server" --command ./run.sh
```

run.sh runs the actual server.

i know how to put in in fullscreen mode.
but i dont know how to get it on the second desktop. can you help me?

atb-nl

---

### Post by stinkeye on 2011-03-04
Using compiz you only really have one desktop.
The only way I know how to get the terminal on the second desktop
is to use something like xdotool in your script to initate your shortcut keys
to switch desktops,start your terminal then use xdotool to switch back to desktop 1.

I run a fullscreen MOC (console audio player) terminal by putting it in the widget layer with compiz.
I created a new terminal profile called **MusicConsole** and set the 
initial title as **MusicConsole** and set to keep initial title.


Then I start the MusicConsole terminal after compiz has loaded with this script.
```
#!/bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
               
               **gnome-terminal --full-screen --window-with-profile=MusicConsole -x mocp** >/dev/null 2>&1 &
  
                
                
		done="true";
	else
		echo "waiting for Compiz"
		done="false"
		sleep 5;
fi
done
exit 0
```

Then add it to the widget layer plugin in ccsm and toggle the layer with F9.

---

