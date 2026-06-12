---
title: "Wish Script. I wish it would work"
date: 2011-07-16
forum: General Help
---

### Post by conradin on 2011-07-16
Hi Everyone,
I have a script in wish (simple windowing shell) 
```

#!/usr/bin/wish
button .hello -text Hello -command {puts "Hello, World!"}
pack .hello -padx 10 -pady 10

```
I checked the path using the bash command: ```
which wish
```
so I know that path is right. 
when I try to run the script, I get "Permision Denied", and ```
# ./2_2.tcl 
-bash: ./2_2.tcl: Permission denied
```
from root.

But, When I type ```
wish
``````
button .hello -text Hello -command {puts "Hello, World!"}
pack .hello -padx 10 -pady 10
```
The thing works. A window with a button appears, and if I click it, it prints "hellow world". SO I have no idea whats going on. This is my first day with wish, so Im a newb.

---

### Post by tredegar on 2011-07-16
Did you make your script executable?

**chmod +x *name-of-script***

Then try again.

---

### Post by conradin on 2011-07-16
Yep. its executatble.

---

### Post by tredegar on 2011-07-17
Well, I copied and pasted your code from post #1, and it works for me (10.04).
Edit: What editor did you use to create your script?

---

### Post by conradin on 2011-07-18
I used gedit originaly. But since you brought it up, I decided to try using 
Cream (a graphical Vim editor) And that works! 

But whats going on here?? All I did was copy and paste from gedit to the cream editior!

---

### Post by Wim Sturkenboom on 2011-07-18
It's just one of those things that can't be explained afterwards. The script might not have been executable for the root user, e.g. because you created it as a normal user and used *chmod 744* to make it executable.

Is there, by the way, a reason why you're developing under root? One mistake can result in disaster.

And welcome to the wonderful world of Tcl/Tk. You will have fun with it and you will curse it ;)

---

### Post by conradin on 2011-07-18
I'm not developing under root, I was just at a loss as to why this script was failing...

---

