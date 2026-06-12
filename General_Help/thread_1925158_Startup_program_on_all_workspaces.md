---
title: "Startup program on all workspaces"
date: 2012-02-14
forum: General Help
---

### Post by seastick on 2012-02-14
I have set xclock to startup on login through System - Preferences - startup applications.  Can I set it so that it starts up visible on all workspaces?  Also, how can I manage where it is positioned on startup, rather than having to move it each time I log in (I know it's not a big deal to move it, but it would be more elegant to have it start in the right place)
Any help gratefully received.

---

### Post by HiImTye on 2012-02-14
```
xclock
sleep 10 #increase if not enough time given to make the window sticky
wmctrl -r xclock -b add,sticky
```if you want it all on one line instead of a script then:
```
xclock && sleep 10 && wmctrl -r xclock -b add,sticky
```

---

### Post by seastick on 2012-02-15
That's great, thanks.  However it doesn't do anything when put in the Preferences - Startup Applications "command" field - in fact it doesn't even start xclock.  I can put the code in a script but where does the script go in Ubuntu?  Is it in /etc/init.d or a subdirectory, or somewhere else entirely.?
Also wmctrl doesn't seem to handle dual screens too well.  Using the -e option to position xclock on the external screen connected to my laptop it doesn't quite make it.  Having got the coordinates using -lG options I tried using -e with the same xy coordinates but it only made it to the edge of the laptop screen, rather than the external corner.  (It did resize itself nicely though).  Is there anyway to get wmctrl recognising dual screens?
I appreciate your help

---

### Post by HiImTye on 2012-02-29
sorry, I don't check this often

to add it to your startup apps, you would just copy the second example I gave
```
xclock && sleep 10 && wmctrl -r xclock -b add,sticky
```
into the 'command' line in 'startup applications. you might want to add a delay to the beginning to make sure other stuff loads first like:
```
sleep 45 && xclock && sleep 10 && wmctrl -r xclock -b add,sticky
```if it is not working at all then paste the first one (the one without the delay *before* the program launches) into the terminal to see why, as the terminal will give you information about any errors, etc..

hope this helps

---

