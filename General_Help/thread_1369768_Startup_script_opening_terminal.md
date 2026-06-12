---
title: "Startup script opening terminal?"
date: 2010-01-01
forum: General Help
---

### Post by Max_Mackie on 2010-01-01
Hi,
Ive got a simple bash script that basically just displays a couple lines of text and a random quote. In startup applications, I made "gnome-terminal --full-screen" open up and in the profile preferences of gnome-terminal I made it run my startup script. There are two problems though.

(1) At startup, 2 terminals are opened (one fullscreen, one not fullscreen)
(2) By bash script runs and keeps on running (how do I get it to display another input line?)

Thanks for the help
I think my second issue belongs in the programming section but they kinda come in a pair.

---

### Post by northrup on 2010-01-01
I don't know how to apply my recommendations, since I'm not very skilled with any kind of scripting beyond DOS batch files.  But the concept should still apply.

For the first issue, it could help if, instead of running the terminal itself as a startup program, which is configured to run your script on startup, you just run the terminal so it points to your script in the command.  I'd try something like this (let me know if this works...):

```
gnome-terminal --full-screen -e [your script]
```

where [your script] is the path to the script you're trying to run.

For the second problem, you need to make sure your script knows to stop and return to the shell instead of go on and on.  Perhaps invoke bash at the end of the script?  I'm not sure how to do that, though.

---

### Post by Max_Mackie on 2010-01-01
Okay, so I tried doing that and I didn't work. So I went back to my startup applications and it turns out that it wasn't even saved! The command was changed from what you gave me to the default "gnome-terminal".

---

### Post by northrup on 2010-01-01
I'd try it again, taking care to make sure you clicked on "Save" instead of "Cancel".  I make that mistake a lot :)

---

### Post by Max_Mackie on 2010-01-01
Ahhh now this is awkward.
Well, you were right :)
Sorry about all that. Thanks again!

---

### Post by northrup on 2010-01-01
No problem :)

---

