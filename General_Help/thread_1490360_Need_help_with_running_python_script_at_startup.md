---
title: "Need help with running python script at startup"
date: 2010-05-22
forum: General Help
---

### Post by inameiname on 2010-05-22
I decided to give randomizing my desktop background a shot every time I login, and after finding a python script that works, I wanted it to start automatically on login. 

I added it in System > Preferences > Startup Applications and it works just fine. 

However, I notice that there is still a "Python" running process. I have to 'killall /usr/bin/python' or end the process through the System Monitor. And for some reason at times the 'Python' running process takes up a lot of resources.

Now my question is how can I run my script so that it runs only once (which in my case is to change the background at system startup just once) and then exits both it and 'Python'? 

My current command that is implemented at startup is:    	 	 	 	 	 	  /usr/bin/python /home/me/.gnome2/nautilus-scripts/Multimedia/Random-Wallpaper.py


So can I just add something at the end of this, or perhaps tweak the end of the python script itself to achieve what I want?

---

### Post by inameiname on 2010-05-22
So I seemed to have found a backwards way of resolving my issue.

I added 'Random-Wallpaper' to the Startup Applications:

Name: Random Wallpaper
Command: /home/me/.gnome2/nautilus-scripts/My_Scripts/Random-Wallpaper/Random-Wallpaper
Comment: Changes desktop background at startup

...and created a 'Random-Wallpaper' folder in nautilus-scripts (because this is where I always put scripts), which includes the python script, a 'delay.sh' script (which delays the running of a script until after a user-defined time (in this case, "killall /usr/bin/python")), and then the 'Random-Wallpaper' script that basically combines the following two things:

/home/me/.gnome2/nautilus-scripts/My_Scripts/Random-Wallpaper/delay.sh 5 "killall /usr/bin/python" & 
/usr/bin/python /home/me/.gnome2/nautilus-scripts/My_Scripts/Random-Wallpaper/Random-Wallpaper.py

It works, but I'm sure there's a simpler way.

---

### Post by cgroza on 2010-09-14
You can kill the process at the end of your script. 
import os
os.system('killall [process]')

---

### Post by inameiname on 2010-09-16
Thanks for the tip. I've changed the Random Wallpaper script since this posting and it doesn't have this issue so it's not necessary now, but thanks for the suggestion.

---

