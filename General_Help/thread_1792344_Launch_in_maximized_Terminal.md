---
title: "Launch in maximized Terminal?"
date: 2011-06-28
forum: General Help
---

### Post by miststlkr on 2011-06-28
I have a launcher set up to run the command in a terminal window and it would be lovely to have the window automatically maximize. Is there a way to do this?

---

### Post by nothingspecial on 2011-06-28
Lots of ways.

Are you using gnome-terminal?

On my netbook, the command would be ```
gnome-terminal --geometry 135x30
```

The numbers are the number of characters across, by the number of characters down.

---

### Post by miststlkr on 2011-06-28
Thanks for the quick reply!   This particular one is a launcher [made using "System>Prefrences>Main Menu>New Item"] opening an ssh connection in a terminal.  the command is just "ssh [user]@[ip]" and I picked "Application in Terminal" from the pulldown.  I had thought about trying to make a bash script to open a terminal, maximize it then open the ssh connection but surely there must be an easier way?

---

### Post by Habitual on 2011-06-28
"Maximized" is subjective to your screen's resolution.
but for now... this will work. (Adjust your gnome-terminal's "--geometry 135x30" to your personal preference.)

**Menu Item for ssh@IP using terminal:**
```
gnome-terminal -e "ssh root@IP" --geometry 135x30
```

or make a shell script and then call the shell script from the menu item....
Open a terminal:
```
vi myscript.sh
```
Hit the I key (for Insert) and add 

```
#!/bin/bash
gnome-terminal -e "ssh root@IP" --geometry 135x30
```

Press ZZ to save and exit.
chmod 700 myscript.sh

Open the menu editor thingie and add Menu Item as 
/home/$username/myscript

"Application in Terminal" not necessary.

---

### Post by miststlkr on 2011-06-28
Hey, thanks a ton.  Obvious answer was obvious in hindsight.  I noticed that if I put a geometry larger than the screen would handle it automagicaly just goes to a maximized window.  Is there any reason not to do it this way?

---

### Post by Habitual on 2011-06-28
> **miststlkr said:**
> I noticed that if I put a geometry larger than the screen would handle it automagicaly just goes to a maximized window.  Is there any reason not to do it this way?

No. And good for you for testing the limits. Seriously, +1

---

### Post by miststlkr on 2011-06-29
What is the point of switching to linux if I didn't want to tinker and play with things?   Sometimes I just get lost and have to stop and ask directions. ;-)    Cheers!  I had completely forgotten about the "gnome-terminal -e" route and was trying to think of a way to do it directly through the ssh command or a shell script.  I've been tinkering with linux for a year or so now, learning as I go, and it seems that the best and worst thing about it seems to be that there are enough ways to skin a cat that you are likely to cut yourself a few times in the process of learning.

---

### Post by Habitual on 2011-06-29
Tinker on then! :) I wrote this a few months ago, it may "help" you tinker further


I work on Servers all day long. Sometime spending HOURS on just a couple of servers.

I wanted a quick and dirty method to get there "faster", if that's possible. And it is...

Launch gnome-terminal and then type screen and connect to Server1. Detach from Server1 (Ctrl+A+D)
Type screen -ls and note the screen session ***identifier***.
example: ***13018***.pts-1.My-Kungfu	(Detached)

type screen again and connect to Server2. Detach from Server2 (Ctrl+A+D)
Type screen -ls and note the screen session identifier.
Screen for Server1 in this example is 13018
Screen for Server2 in this example could be 5150

Make an myscreens.sh file in your $PATH somewhere and add these 2 commands:
I called this one myscreens.sh because it's easy to type. YMMV

```
#!/bin/bash
gnome-terminal --tab-with-profile=default --title=Server1 -e "screen -x 13018" --tab-with-profile=default --title=Server2 -e "screen -x 5150"
```

chmod 700 /path/to/myscreens.sh

Now you can type myscreens.sh in terminal or Alt+F2 and run myscreens.sh and you are instantly (re)connected to Server1 in one tab and Server2 in another tab.

NOTE: if you close the "new" gnome-terminal window with these 2 tabs, just re-run myscreens.sh and you're back in business.

Enjoy.

You go, Boy-eeeeeeeeeeeee :P

---

### Post by miststlkr on 2011-06-29
outSTANDING trick.   I absolutely LOVE this stuff :-D  Cheers!  don't know that I have an immediate use for it, but that is a beautiful thing

---

