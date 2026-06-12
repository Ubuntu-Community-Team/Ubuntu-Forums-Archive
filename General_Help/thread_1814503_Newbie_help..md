---
title: "Newbie help."
date: 2011-07-29
forum: General Help
---

### Post by emafasa on 2011-07-29
I'm fairly new to this. I've been asked to do certain jobs doing scripts in bash and perl. So this time they asked me to check which users hasn't been able to loggin. DONE with 
```
lasb
``` 
Now they asked me to show how many times all the users have input certain Bash Commands like 
```
Ls
Cd
pwd
```

I was wondering if there was a command of something that could show me how many times those commands has been used, I already know I can see all input with ```
history
```

Sorry I'm really new to this, been working with this for a couple of weeks, and its really interesting.

---

### Post by TeoBigusGeekus on 2011-07-29
```
history | grep ls | wc -l
```
You pipe the history command with grep ls, thus making only the lines that contain ls to appear and then you pipe the result with wc -l which counts the resulting lines.

---

### Post by emafasa on 2011-07-29
Thank you so much! I was working with 
```
 history | grep ls 
```
but without the 
```
wc -l
```
That's even better! Nothing bad putting in some extra work! Thanks again.

BTW nice troll face haha!

One more question when I run that in a .sh it doesn't do anything it just goes blank. Any suggestions?
Thanks in advance!

---

### Post by TeoBigusGeekus on 2011-07-30
Make your script like this
```
history | grep ls | wc -l
read -p "Press any key to continue"
```
and run it from a terminal
```
/path/scriptname.sh
```

You could even create a launcher for it that contains this command
```
gnome-terminal -e /path/scriptname.sh
```
Replace gnome-terminal with whatever shell you're using.

---

