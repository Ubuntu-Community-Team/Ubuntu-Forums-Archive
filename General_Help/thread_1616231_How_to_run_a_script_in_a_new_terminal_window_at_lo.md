---
title: "How to run a script in a new terminal window at login"
date: 2010-11-08
forum: General Help
---

### Post by GenePayne on 2010-11-08
I am aware of how to run scripts on startup, but I don't know how to do the following everytime ubuntu starts up:

1. automatically open a new terminal window (I know how to do this)
2. automatically run a specific script in that terminal (I want to leave this terminal open indefinitely)

Any ideas?

---

### Post by me.translucent on 2010-11-08
i am not sure would it run in a terminal but have you tried using a start up script ? create the script that you want to run at the time of start and place it in ```
/etc/init.d 
```
then run the command.
```
update-rc.d file_name defaults
```
please note that you'd also have to update the permission of the file and make it executable for the user who is running it .

---

### Post by GenePayne on 2010-11-27
I figured this out.
I went to Preferences -> Startup Applications, and then added a startup program with command string:
```
gnome-terminal -x /path/to/script_to_run_at_startup
```

Now when I login, a new terminal window opens and runs the script automatically. This way I can see the output of the script.

---

### Post by me.translucent on 2010-11-28
hmm .. i heard that they are going to replace the gnome with unity even on desktop computeres, wondering if that would work from the next version of ubuntu i guess not :P

---

