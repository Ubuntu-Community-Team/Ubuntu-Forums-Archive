---
title: "How to store favorite terminal commands?"
date: 2010-01-15
forum: General Help
---

### Post by RRFarFar on 2010-01-15
I am currently using tomboy to store my favorite terminal commands. Is there a better way? Maybe some terminal programm that has this feature?
I am currently using Guake and it works great.
Thx

---

### Post by alwayshere on 2010-01-15
you could right click on desktop and choose create launcher 
and make a launcher for the coomands

---

### Post by lykwydchykyn on 2010-01-15
I reported the spam, if it happens again just click the "report abuse" link by the post and tell the mods it's spam.  Someone will come by to clean it up eventually.

Regarding your question, this is usually handled by writing scripts.  The customary approach is as follows:

1. create a directory called "bin" in your home folder.
2. edit your .bashrc file and add a line like this:
```

PATH=$PATH:$HOME/bin

```
3. Now, anything you put in ~/bin is in your path, so if you put a script called "my_favorite_command" in there and make it executable, you can run it from anywhere without specifying a path.


Once you do that, you can put your favorite terminal commands in script files with names that are more meaningful to you.  for instance you could create a script called "free_drive_space" that contained this:
```

#!/bin/bash
df -h

```

---

### Post by SuperSonic4 on 2010-01-15
Or you can set aliases in terminal by editing ~.bashrc
One of mine is

```
alias handbrake1='handbrake -i /dev/sr1 -L -e x264 -b 1024 -E ac3 -s 1 -o output.mkv'
```

You can give your user the right to use root commands (like apt) without a password (involving editing sudoers) but idk what forum policy is -- but you can still set aliases without it so dw.

---

### Post by stinkeye on 2010-01-15
You can use the ctrl + r feature in terminal.
Press ctrl + r and then type in part of the command and it will bring up a command from your history.
Press ctrl + r again and it will cycle through your history finding commands containing the phrase you entered.

---

### Post by RRFarFar on 2010-01-15
Thank you for all you replies. I will experiment with pleasure.

I never heard of script trick. That is interesting althugh I would prefer to see the actual command because I might forget it when I am in front of somebody else's linux.
Ctrl + r - this is great. I will definitely use it.

When I asked this question I thought of some terminal addon that would be like favorites in firefox))))) it is sort of fantasy)))) maybe something of that sort already exists

---

### Post by mister_playboy on 2010-01-15
Entering ```
history
``` while in the terminal will bring up a list of recently entered commands... default is last 500, IIRC.

You can then enter any of those command by entering ! and the number in the list... say ```
!344
```

I find this quite helpful.

---

