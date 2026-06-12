---
title: "Controlling Terminal Window"
date: 2009-12-21
forum: General Help
---

### Post by Sailing Bud on 2009-12-21
I am new to Ubuntu 9.10 (approx. 1 1/2 weeks) and I am comfortable using a command line structure. I am attempting to write my first script and have done pretty good so far. I have three problems and all three are in the same area of controlling the terminal window. 1.) I can open a new terminal window the size and location that I want but I want to have the script continue to run in the original window and run a new command in the new window. 2.) I would like to change the title of this window to a custom name. 3.) And . . . I would like to change the size of an existing window and have the script continue to run.
 
Your tollerance will be appricated ad I don't know if this should be in the newbees corner or here.
Thank You in Advance,

---

### Post by hugmenot on 2009-12-21
If you are that comfortable then you should find all you need by reading gnome-terminal&#8217;s man page.

Just type "man gnome-terminal".

1) The "--geometry" parameter is what you need.
2) Probably "-t"
3) No idea.

---

### Post by Rhubarb on 2009-12-21
I might be able to help you out with number 3)

**devilspie** sounds like it might be able to do the job
It's an app in the repositories that's excellent for controlling windows, their sizes, positions, and even transparency.
Have a look at the man page for it for further details.

I'm not infront of a Linux box at the moment, so I can't really assist you much further at present.
But, from memory devilspie should be able to do the trick for you.

---

### Post by Sailing Bud on 2009-12-26
Thank you for the help.  There is still an ongoing problem.  I believe that you are correct with "gnome-terminal --geometery=XX and --title=XX" a couple of other options will do exactly what I want.  The problem that I an fighting now is the command "mulit-gnome-terminal" appears not to be available in Ubuntu 9.10.  There are several other options that appear to be not present and I can not find them in the respotories.  They are: title, usage, working-directory, hide-menubar and the list goes on and on.

Please remember that I am a newbee with this and am trying hard to be sucessful.

Hoping to go from :confused: to :)
 
Thank Again,
Bud

---

### Post by Rhubarb on 2010-02-11
Also consider using **xdotool** from the Ubuntu repositories.  It can do somethings that devilspie can do, but in some ways a little easier.

---

