---
title: "Simple Script to open terminal"
date: 2011-05-11
forum: General Help
---

### Post by Kin2InuYasha on 2011-05-11
I'm trying to create a script where all I have to do is double click the script file, and it opens and runs 2 commands. That's it. Or run a command from a certain directory.

I'm looking for something similar to Batch files in windows. I've looked and found the shell scripts and I created one, and it works and runs the script, but it doesn't open the terminal for me.

In short, a way to make a script, where all I have to do is double click the file, and it runs,

cd /home/sds/srcds_1/orangebox
[FONT=verdana]./srcds_run -console -game cstrike +map de_dust -maxplayers 16 -autoupdate[/FONT]

Or, from that directory so I don't have to cd.

Thank you.

---

### Post by m_duck on 2011-05-11
Is it necessary that it runs in a foreground terminal? For that to be so, something like this would probably work:
```
#!/bin/bash
xterm -e "/home/sds/srcds_1/orangebox/srcds_run -console -game cstrike +map de_dust -maxplayers 16 -autoupdate"
```
Shove the above in a file some, say ***/home/sds/scripts/cslaunch*** or something, then make it executable with:```
chmod +x /home/sds/scripts/cslaunch
```Remember to change the path in that command to the one you used.

Finally, make a launcher on your desktop or panel or wherever, with the command field referring to the path of that script. That ***should*** work :p

---

### Post by Kin2InuYasha on 2011-05-11
> **m_duck said:**
> Is it necessary that it runs in a foreground terminal? For that to be so, something like this would probably work:
```
#!/bin/bash
xterm -e "/home/sds/srcds_1/orangebox/srcds_run -console -game cstrike +map de_dust -maxplayers 16 -autoupdate"
```Shove the above in a file some, say ***/home/sds/scripts/cslaunch*** or something, then make it executable with:```
chmod +x /home/sds/scripts/cslaunch
```Remember to change the path in that command to the one you used.

Finally, make a launcher on your desktop or panel or wherever, with the command field referring to the path of that script. That ***should*** work :p
This guy.....I LOVE THIS DOCTOR! er, Ubuntu Expert.

It doesn't look like the type of terminal I'm used to, but this DOES satisfy my needs. Thank you good sir.

---

### Post by r-senior on 2011-05-11
> **Kin2InuYasha said:**
> This guy.....I LOVE THIS DOCTOR! er, Ubuntu Expert.

It doesn't look like the type of terminal I'm used to, but this DOES satisfy my needs. Thank you good sir.
You could try 'xfce4-terminal' instead of 'xterm'?

---

### Post by m_duck on 2011-05-11
Yeah, you can switch ***xterm*** for whatever terminal you want to use, be it gnome-terminal, xfce4-terminal, urxvt, konsole, eter... Well, you get the idea.

---

### Post by Kin2InuYasha on 2011-05-11
> **r-senior said:**
> You could try 'xfce4-terminal' instead of 'xterm'?
> Yeah, you can switch ***xterm*** for whatever terminal you want to use, be it gnome-terminal, xfce4-terminal, urxvt, konsole, eter... Well, you get the idea. 	

This is now EXACTLY what I was looking for now. Everyone in this thread is awesome. This is now the VIP section of ubuntuforums.

Thanks guys.

---

