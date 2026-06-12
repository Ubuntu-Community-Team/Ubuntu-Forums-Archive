---
title: "no cursor after apt-get upgrade and ati drivers installation"
date: 2010-02-23
forum: General Help
---

### Post by arcanewulf on 2010-02-23
So, my computer has a radeon hd 5770 graphics card. I wanted to have the most compatible drivers so I downloaded the proprietary ones from ATI's site. Found the ones for my card and x64 bit windows and chmod'd it into an executable. 

Ran it with --buildpkg ubuntu/karmic the first time and the command aticonfig --initial -f threw back errors.

(just remembered, the first time I ran it without --buildpkg and it failed, after adding --buildpkg ubuntu/karmic it downloaded some extra files and installed fine. That's when aticonfig --initial -f threw the xorg "Screen" error.)

I saw that installing it without specifying which linux distro you had would bring up a GUI and it would sort everything out itself. So I did this, and it's the best display so far, but ever since I installed from the original driver package from ubuntu my mouse cursor has been missing completely.

It isn't on the login screen, it doesn't come up at all. If I click and drag on the desktop it highlights blue where the cursor should be. I can still use the mouse, I just can't see where it is.

I had the drivers ubuntu installed by itself after I allowed the use of proprietary software, but after an apt-get upgrade I got a watermark that said "ati unsupported hardware" which is a known bug for a range of the ati drivers and the suggestion is to get the newest version from their site or to roll back to an older working one.

There are also people with a similar problem but not the same problem. The most common occurrence is no cursor after waking from sleep. It seems to be an error in the xorg.conf, but I can't find the file where it should be and recreating it with a dpkg console command didn't do anything.

Everything else is running amazing. Awesome speed, everything works as I click, almost no wait time, but I need to have a cursor... Thanks in advance, sorry for the essay, but I wanted to cover my procedure thus far and all the little details so nothing gets skipped over.

---

### Post by arcanewulf on 2010-02-23
well, I found this 
[Forums.amd.com ATI 10.2 No Cursor]("http://forums.amd.com/forum/messageview.cfm?catid=203&threadid=128217&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+AmdDeveloperForums-GeneralDiscussions+%28AMD+Developer+Forums+-+General+Discussions%29")
which tells me to enter a line into the xorg file, but /etc/x11/xorg.conf doesn't exist...

---

### Post by arcanewulf on 2010-02-23
So, now I found xorg.conf, I accidentally created x11, and realized that there was an X11 folder that was also there (I'm mostly a windows user, non-case sensitive).

Now, I appended the lines as stated in the link I posted, but I get an error that the xorg.conf file could not be parsed that there were no screens found and that the error was on line 39 (the last line) of the file.

---

### Post by arcanewulf on 2010-02-23
Basic Problem guys, thanks so much for the help, sometimes I just have to do something like this to walk myself through the logical steps.

There were two sections labeled "device" so that obviously is why it threw the errors.

Catalyst 10.2 has an error in its xorg.conf file where the mouse cursor does not display.

To fix it you must
[INDENT]1. open your xorg.conf file as a root user and edit the section "Section "Device"" to include the line 
Option "SWCursor" "true"" on its own line within the section and end section segments saving changes and paying attention to syntax, otherwise you'll have to fix your xorg.conf in the VI editor like me.[/INDENT]
[INDENT]2. stop xorg by running sudo /etc/init.d/gdm stop[/INDENT]
[INDENT]3. sign back in inside of the no-gui mode[/INDENT]
[INDENT]4. run the command startx to restart the xorg server[/INDENT]
[INDENT]5. you can skip 2-4 if you know an easier way to restart the xorg server (such as rebooting), but this is the method I've found in a quick google search.[/INDENT]

P.S. -> Case closed, I solved this guy myself.

---

### Post by Sivik on 2010-04-21
I added the Options with the "SWCursor" "true" and it is still not working correctly.  Is there something else which needs to be done after the reboot to make this work?

---

