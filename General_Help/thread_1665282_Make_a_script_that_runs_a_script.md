---
title: "Make a script that runs a script?"
date: 2011-01-12
forum: General Help
---

### Post by neokyle on 2011-01-12
Is it possible to have a script execute another script after performing some simple actions?

I need a script that goes into my screen session, types and enters the word "stop" then runs another script. I want to crontab it so it runs every 6 hours.

---

### Post by TeoBigusGeekus on 2011-01-12
```
#!/bin/bash
....
/path/to/script/scriptname
....
```

---

### Post by matt_symes on 2011-01-12
Hi

As Teo said but to run in same shell (not child shell)  

```
. /path/to/script/scriptname
```

or

```
source /path/to/script/scriptname
```

Kind regards

---

### Post by neokyle on 2011-01-12
so it would be

#!/bin/bash
screen -r stop
/home/meokyle/script.sh

That would go into my screen session, type stop, then run the script that i specify?

I dont want to try it out if thats not how the script should be setup, just paranoid that something will break. Gonna wait for confirmation that i have this right.

---

### Post by Vaphell on 2011-01-12
any sequence of commands/scripts that you execute in terminal can be transformed into a script so what you got there is correct

---

### Post by neokyle on 2011-01-12
Oh, ok. 

Would about detaching from the screen? the terminal wouldnt be open so would i need it to detach? I would i have the script do ctr A + D.

---

### Post by neokyle on 2011-01-12
I tried executing the script and it did not work, now when i type screen -r and go into my screen session i cant type any commands, it doesnt even say neokyle@server.

---

### Post by Vaphell on 2011-01-13
sorry about that, i shouldn't really confirm without reading much into what screen does >_<

---

### Post by Vaphell on 2011-01-13
sorry about that, i really shouldn't confirm without reading deep into what screen actually does >_<

---

### Post by neokyle on 2011-01-13
Its alright, even though i couldn't do anything in screen i was able to terminate it via my control panel.

---

### Post by neokyle on 2011-01-13
I cant get the script to work, th only thing it does is,attaches to my screen and makes it so i cant execute commands.

Perhaps a better approach would be a script that terminates a process and then runs a script in screen.

---

