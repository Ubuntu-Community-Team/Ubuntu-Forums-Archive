---
title: "command to bring up multiple terminal windows in gnome"
date: 2010-08-06
forum: General Help
---

### Post by alesserfate on 2010-08-06
hey folks

im working a BASH script and at one part of it i need it to:

-bring up 3 terminal windows with x-by-x size aligned in a specific part of the screen (x, y coordinates)
-terminal windows must be addressed with a command line so when they are opened, they are running seperate scripts.

im lost and i've searched and have no idea how to write something like this

---

### Post by v1ad on 2010-08-06
use screen. but that will have them running in the background.

if you want to tell us more specifics we might even find better ways to do it.

---

### Post by slooksterpsv on 2010-08-06
Look into using XTERM - I'm not sure how to fully do what your asking, but you can set geometry of the window and also tell it to execute a script/command/etc. via
```

xterm -e /bin/bash -l -c "*command_to_run*"

```

Only problem is I can't figure out how to keep the window open, it closes after running the command, may have to look into that.

EDIT:
If you need window dimensions I'll find out how to do that and post back.

Found it it'd be:
```

xterm -hold -e /bin/bash -l -c "*command_to_run*"

EXAMPLE:
xterm -hold -e /bin/bash -l -c "ls -R ~"

```

Post regarding it is here:
[http://ubuntuforums.org/archive/index.php/t-296628.html](http://ubuntuforums.org/archive/index.php/t-296628.html)

---

### Post by alesserfate on 2010-08-06
thanks for the super replies, i've made some progress but still kind of stuck, this is what im doing:

i have a looping menu, with choice 1, 2, 3, 4,5 etc

when a user enters the choice, it runs a command thats listed under that option

i've used the
 ```
xterm -hold -e /bin/bash -c "command"
```

and it works, HOWEVER, the main script will NOT continue until the child script thats called in that menu option is done executing

this is where im stuck, i need the main script to keep looping even while the child scripts are still executing. aka - the user must be able to run multiple options simultaneously

so if the user presses 1., it executes script under option 1 in a new window which the user leaves open, then they go back to the main script and press 2, and it executes script number 2. now we have scripts 1 and 2 running, and main menu still open

also, i was wondering if it's possible to bring up the terminal that comes with ubuntu, rather then xterm, so that the visual appearance of that terminal window is the same as of the parent.

thanks for the help so far guys!

EDIT:

so i am currently trying to use "gnome-terminal" instead of xterm command.

---

### Post by worksofcraft on 2010-08-06
See if this gives you any ideas:

```


gnome-terminal -e "gnome-terminal --help-all"


```

;)

---

### Post by alesserfate on 2010-08-06
> **worksofcraft said:**
> See if this gives you any ideas:

```


gnome-terminal -e "gnome-terminal --help-all"


```

;)

haha yeah,
i used that and im at

gnome-terminal --geometry=100x10 --hide-menubar --window-with-profile=Default --execute /home/domo/cr_si_1_0.bash

but for some reason it wont load the standard profile

the profiles are in

/home/usernamdsklfsdf/.gconf/apps/gnome-terminal/Profiles

there is a folder Default with file %gconf.xml, i tried parsing it in the string all the different ways but the terminal still comes up with the default colours (not the ones that are set when  you normally click on the icon)

---

### Post by worksofcraft on 2010-08-06
I think it may be problem with permissions on files that belong to other users. Perhaps try with all the files in your own folders first... IDK I never had to do anything like that myself.

---

### Post by alesserfate on 2010-08-06
> **worksofcraft said:**
> I think it may be problem with permissions on files that belong to other users. Perhaps try with all the files in your own folders first... IDK I never had to do anything like that myself.

true.. thanks for the input anyways, i got it to do the size i want and the right terminal i want so im happy with that

the last and most important thing is I want to make the parent script not wait for child script to finish and continue executing (or rather looping in my case), thats my last challenge if anyone knows how.

---

### Post by worksofcraft on 2010-08-06
if you end your command line with & then it runs in the back-ground.... i.e you don't have to wait for it to finish.

---

### Post by alesserfate on 2010-08-06
> **worksofcraft said:**
> if you end your command line with & then it runs in the back-ground.... i.e you don't have to wait for it to finish.

Thanks so much! Now it works!

---

### Post by alesserfate on 2010-08-06
hmmm on another note

i want to make a script start NOT at bootup NOR at runlevel 5 login, but when a user logs into their session in runlevel 5

i've tried adding it through startup applications but it wouldn't work

any ideas ?

---

### Post by worksofcraft on 2010-08-06
You can make a file called .profile in your home folder and the commands in there get run when you log in. Make sure you give it execute permission though ;)

---

### Post by alesserfate on 2010-08-06
amazing, thanks very much once again! at first it only loaded the script and wouldnt load the panels, but then i added a & at the end, and it worked out great, thanks againn!

---

