---
title: "Remapping Broken F2 Key / xmodmap"
date: 2011-02-07
forum: General Help
---

### Post by DarkSideKlyde on 2011-02-07
Hi, and thanks in advance for the help. This is my first forum post (here or elsewhere) and I have searched for an answer but cannot find exactly what I am looking for. I apologize in if I have broken some kind of forum rule. Anyway, as stated in the subject line...my F2 key does not work and I do a lot of file renaming. As this is also the hotkey to run applications (with Alt) I would like to remap it to the 'squiggly line' key (to the left of the 1 key and above the Tab key). Using the command 'xev' I have determined that this is "keycode 49". I have been using the the following command in the terminal after booting up my PC...

xmodmap -e 'keycode 49 = F2'

This seems to work most of the time, however, I would prefer to have this done every time automatically upon startup. Through my research I have read that I need to modify or create a file in /etc/X11/   but I am unsure of what EXACTLY to do and don't want to screw anything up. Could I please get some help in finding out which file I need to add/modify to make my 'squiggly line' key act as the 'F2' key every time I log in/boot up?

As a side note, I know how to add applications to Startup (i have added the Guake Terminal to run at Startup) but I am unsure of what exactly I am supposed to do in this situation. 

Thanks in Advance,

Darkside Klyde

EDIT: I just booted up my computer and remapped F2 to the 'squiggly' key in the terminal with xmodmap. I tested it on a file and it successfully renamed it. However, when I press Alt + 'squiggly' it does not open the "Run Application" window. I checked in the Keyboard Shortcuts and "Run" is set to Alt + F2. :(

---

### Post by DarkSideKlyde on 2011-02-17
After doing some command line work/terminal entries, I have determined that I need the "squiggly line" key and would like to map my F2 key to the "right control" key....Keycode 105... I can do this ever time i boot by typing..."xmodmap -e 'keycode 105 = F2" into the terminal. Please help me. I know I need to modify a file and add it to  the start up ???? Which file? If it is not there, how do i create it? I just want my 'right ctrl' to  be 'F2' every time i start the computer. Thanks in advance.....

Klyde

---

### Post by DarkSideKlyde on 2011-03-10
I bought a replacement keyboard for my machine on Amazon.com for about 10 bucks. MY problem here is solved.

---

### Post by Krytarik on 2011-03-10
Although it comes a little late, it may help in future cases:

You can simply add the command to "/etc/rc.local", before "exit 0", like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

xmodmap -e 'keycode 105 = F2 F2 F2'

exit 0
```Where you able to use gnome-panels Alt+F2 feature with your modification?

I just yet figured that you need to restart Compiz to get it recognize the new xmodmap, it handles some of the most common keyboard shortcuts with its "Gnome Compatibility" plugin.

So, if you would add the xmodmap command to rc.local, the specified key would be recognized right from startup. (Of course, you could also simply modify the keyboard shortcut.)

---

### Post by DarkSideKlyde on 2011-03-29
Thanks [Krytarik]("http://ubuntuforums.org/member.php?u=1187548") for the reply, late or not. Your explanation was perfect. I have had some recent experience editing rc files recently while test driving #!. It seems that your answer would have worked perfectly for me. As for the run command (Alt+F2), if i remember correctly it worked sometimes and others not, although I couldn't tell you why or what made it work/not work sometimes. Anyway, thanks again [Krytarik]("http://ubuntuforums.org/member.php?u=1187548") for the reply, hope this helps someone else.

---

