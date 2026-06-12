---
title: "Running Shell Script from Terminal"
date: 2011-02-14
forum: General Help
---

### Post by EMABrad on 2011-02-14
So I have a shell script that I want to be able to run from the terminal just by typing "topcat", regardless of where I am or what user I'm under.  How would I go about changing the bash configuration files (if I have to) in order for that to work, for me and for the other users on the computer (I have root access)?  As it stands right now, I have to type "/bin/topcat/./topcat" in order for it to execute.  How could I make it shorter?

---

### Post by hawkmage on 2011-02-14
Try adding the "/bin/topcat" directory to your path.

Then all you should have to do is run "topcat"

---

### Post by Habitual on 2011-02-14
Or...

type  in terminal... type
```
echo $PATH
```

and then mv topcat to any one in the result.

Or...
Stick this in your .bashrc
```
alias topcat="/path/to/current/topcat"
```
and then type
```
source ~/.bashrc
```
then
topcat from anywhere will work.

---

### Post by EMABrad on 2011-02-15
Awesome, thanks a lot!

---

