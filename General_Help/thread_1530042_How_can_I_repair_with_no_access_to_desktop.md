---
title: "How can I repair with no access to desktop?"
date: 2010-07-13
forum: General Help
---

### Post by sofasurfer on 2010-07-13
Jaunty.
Don't know if I have a glitch or if I deleted something while dinkin' around. Anyway, I boot to the desktop and I have desktop icons but no panels at all. Alt+F2 does not work. I think CTRL+ALT+F2 gave me "run" window. "Sudo gnome-panel &" did nothing. "Init 1" gave me a "init 1" screen but I couldn't accomplish anything there for lack of know-how.
Reinstalling is no big deal at all for me but I wish I could accomplish something geeky like a repair.
I'm not sure of the process for using a live cd.
Any thoughts?

---

### Post by lordskid on 2010-07-13
open a terminal... (ctrl-alt-t) //works only if running 10.04
then type this command.
```

gnome-panel --replace

```

does this bring up the panel?
also try to right-click on the desktop and select create launcher

you can fill in the details and put the gnome-panel --replace command there too.
double click and see if panel comes up.

---

### Post by lordskid on 2010-07-13
this should not be a sudo command.

---

### Post by dino99 on 2010-07-13
have you tried right click somewhere on the desktop and select the second choice line ?

or

sudo dpkg-reconfigure gnome-panel

---

### Post by sofasurfer on 2010-07-13
Wow am I a screwup.
CTRL+ALT+T does nothing.
CTRL+ALT+F2 opened "run" window so I typed sudo dpkg-reconfigure gnome-panel. Nothing!
I right clicked on the desktop. How often I forget about the precious "right-click". I created a launcher by using the command "gnome-panel". Got me some panels!!
Opened a terminal. Typed "gnome-panel --replace". Nothing!! Typed "sudo apt-get install gnome-panel". Rebooted. Nothing!!

Well, I can work with this for tonight. I just need to watch a little on line tv before bed. I'll just reinstall tomorrow. Its just a half hour job.

Thanks. I learned a little.

---

### Post by pmlxuser on 2010-07-13
re installing though sound easy is not the best, the best way to learn is fixing. till nothing can be fixed then re installing is the way to go. 
Just Saying ;)

---

### Post by lordskid on 2010-07-13
I agree with that pmlxusr

---

