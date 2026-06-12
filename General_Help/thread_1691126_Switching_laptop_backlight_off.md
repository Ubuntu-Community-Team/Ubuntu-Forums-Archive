---
title: "Switching laptop backlight off"
date: 2011-02-19
forum: General Help
---

### Post by mathiaho on 2011-02-19
Hi

I want to make two hotkeys on my laptop:

1. Blank the screen and turn off the backlight
2. Lock the screen and turn off the backlight

I'm running Lucid. The laptop is a Tosshiba satellite, see here for specs:
[http://uk.computers.toshiba-europe.com/innovation/product/Satellite-L650D-15G/1094634/toshibaShop/true/#0](http://uk.computers.toshiba-europe.com/innovation/product/Satellite-L650D-15G/1094634/toshibaShop/true/#0)

1. I have tried "xset dpms force off", which works for half a minute or so, before the backlight comes back on.

2. I've tried "gnome-screensaver-command --lock && xset dpms force off", which works, but has the same problem as 1..


Strangely, when gnome-power-manager turns the screen off after a set amount of time, it works perfectly. Is there any way of replicating what gnome-power-manager does in a command?

Thanks

---

### Post by Naggobot on 2011-02-19
I have been wanting the same thing so you are not alone.

I have not gotten as far as you. I tried your commands and the behavior was the same as you describe. My hard ware is [HP550]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-89315-3764998.html") so a quick assumption might be that this is not hardware related issue.

---

### Post by mathiaho on 2011-02-19
I think I've read somewhere that gnome-screensaver is to blame (I'm not sure, though). It forces the backlight on if it haven't marked the computer as idle. Maybe there's a way to tell gnome-screensaver manually that the computer is idle. uninstalling gnome-screensaver is not an option for me (as it handles the screen-locking mechanism that I want)

---

### Post by Naggobot on 2011-02-19
Based on your post I googled a bit and tried following

1. Opened a terminal and ran command

```
gnome-screensaver-command -i
```Terminal was frozen by this command i.e. process stays active I think. 

2. Opened a second terminal and ran command

```
. /usr/share/acpi-support/screenblank
```Screen stayed blanked (at least for few minutes)

Now this is clearly not the solution I need / want but counts probably as progress. Do you have any ideas on how to iterate from this?

---

### Post by Naggobot on 2011-02-19
Possible solution

I made a script with

```

#!/bin/bash
gnome-screensaver-command -a
. /usr/share/acpi-support/screenblank

```which worked at least for 120 sec.

I need to reboot and retest to see if it actually works and is just not a quirk mess up by me.

---

### Post by Naggobot on 2011-02-19
Nope

It was the latter. 

So the script did not work after reboot. So obviously I had inhibited the screen saver somehow and was not aware of it.

---

### Post by mathiaho on 2011-02-19
Ok, this is strange.

I tried your codes, and my results are exactly the same.

meanwhile I tried killing processes, and found that if you kill gnome-power-manager,

```

sudo killall gnome-power-manager
```

then the backlight stays off.

I have a couple of ideas. I'll post back in a couple of minutes

---

### Post by mathiaho on 2011-02-19
that should be "-i" in line 2 of your script. Try again

---

### Post by Naggobot on 2011-02-19
The -i stops the execution of the script (at least I think it happened so on my first try.) Thats why I switched to -a.

Anyhow this script seems to work when the script is run in terminal

```

#!/bin/bash
. /usr/share/acpi-support/screenblank
gnome-screensaver-command -i

```I have not tried / tested but I suspect that if the script is not run in terminal then the screen saver will stay inhibited. If the script is run in terminal then closing the terminal should kill the inhibiting process? At least this is my guess (no knowledge involved)

Anyhow this solution seems to work for me. 

Detailed instructions

Open gedit and paste the above code portion to file
Save file to desktop as blankScreen.sh
Right Click to file, select properties, select permissions, check the "allow executing file as program" check box. 
Close dialog box.
Double click the file and select "run in terminal" option
Screen blanks and back light stays turned off. 

To turn on back light  move mouse and close the terminal.

Thanks for your help!

---

### Post by mathiaho on 2011-02-19
Yes. The -i makes bash busy, so it won't run the rest of the script. -i -a are two completely different flags, and makes gnome-screensaver do two completely different things. The reason why your last script works is because "gnome-screensaver-command -i" is the last process run.

And you're right; Closing the terminal stops the "gnome-screensaver-command -i"-process. I don't really know how to stop the process if its run elsewhere (via alt+F2 for example). As long as "gnome-screensaver-command -i" is running, the screensaver will not be activated by timeout.

It is possible, though, to activate the screensaver manually.

---

### Post by mathiaho on 2011-02-19
killall gnome-screensaver-command -i

you don't even need sudo.

But you have to do it in terminal, I think.

Edit: actually just 
```
killall gnome-screensaver-command
```

will work, and you can run it in any way you like; by terminal or alt F2

---

### Post by Naggobot on 2011-02-19
OK

And it seems that closing the terminal also closes the gnome-screen-saver-command process. 

I do not know if you noted my edit so I re-iterate here.

Thanks for your help. If you had not pointed me to the screen saver 

>  gnome-screensaver is to blame

I would still be in where I was a year ago with this when I first took a look in to this. (and I mean no where)

---

### Post by mathiaho on 2011-02-19
Hehe, me neither I guess. gnome-screensaver-command -i is what really solved it for my part, so thanks for the help! :)

I guess I'll make gnome-screensaver-command -i run on startup, since I really don't like having a screensaver at timeout anyway, then I'll set my hotkeys to

```
xset dpms force off
```and

```
gnome-screensaver-command -l && xset dpms force off
```I'll mark the tread as solved, although we shouldn't need to run through these loopholes to make such a simple thing work.

---

### Post by sputnikeee on 2011-05-12
Thank you mathiaho & naggobot for your interesting collaboration.  Elegant it isn't, but work it does.  I have also been trying to solve this for quite some time.
Too bad gnome-power-manager did away with the dbus interface, as that would have made it easy, since it does switch the light off.  I'm sure they had their reasons.  But this will do!  I don't care about screensaver function either, just give my backlight a break.
\\:D/

---

### Post by mathiaho on 2011-05-12
:) 
And thank you for taking the time to tell us! It's nice to know that we've helped someone else than ourselves. You've gotta love this community!

---

### Post by sputnikeee on 2011-05-16
Actually I'm a spy from the eeebunt, er, I mean Aurora community.  But with Ubuntu's huge user base, I find many answers here, as we all have much in common.
Anyhow, my reason for this post is for others that may stumble on this.  Although your hotkey idea is just fine, I cannot enter multiple commands (i.e. &&) for my hotkeys for some reason.  So I simply created a bash file called by the hotkey and perhaps it might be even better because the first command is: killall gnome-screensaver-command, so there isn't a backlog of dead running processes, although probably not a big thing.  Here it is:

```
killall gnome-screensaver-command
xset dpms force off
gnome-screensaver-command -i
```

So there is never more than one of these limbo instances running.  This works very nicely.  I find now when I close Linux the "a program is still running" dialog appears for 1/2 a second (it says unknown for program name), but no big, quits immediately after that with no effort on my part, it's worth it.  If it really bugs you even that could be fixed, but I'm not bothering.
I also tried running the -i command on startup, but it didn't seem to stick, although I could have jumped to conclusion, too antsy to see this finally solved.  This works, so it's the winner.
Another nice thing about your idea is that power manager screen blanking still functions on time, so it's the best of everything.

---

### Post by mathiaho on 2011-05-16
I can't have && and such in hotkeys either, so I made a script, I just forgot to mention that I did. Oops :P
Another thing that might be of interest: I'm using the "windows button"+F2 as the hotkey. The keyup signal from the "windows-button" makes the backlight come back on.
Solved with "sleep 0.2" at the start of the script

About the "gnome-screensaver-command -i" at startup: it works for me. I don't need to "killall gnome-screensaver-command", nor do I have to start "gnome-screensaver-command -i" more than once.

I don't think there will be a pile of dead processes since "gnome-screensaver-command -i" is just run once.

---

