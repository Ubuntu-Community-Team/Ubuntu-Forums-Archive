---
title: "Invert Ctrl c/v and Ctrl Shift c/v in Terminal"
date: 2011-03-16
forum: General Help
---

### Post by ursubaloo on 2011-03-16
Hi all,

I want to invert the keyboard shortcuts "Ctrl c" and "Ctrl Shift c" in the terminal. That means I want "Ctrl c" to COPY and "Ctrl Shift c" to BREAK. Similarly for Ctrl v <--> Ctrl Shift v. 

I know you can assign copy and paste to ctrl+c and ctrl+v in the Edit->Keyboard Shortcuts menu of the terminal, but I can't find a way to assign BREAK to ctrl+shift+c if I override what ctrl+c does.

Any ideas?

---

### Post by ursubaloo on 2011-04-24
Bump. Any ideas guys? It seems like a fairly common thing for anyone migrating from Windows to Ubuntu would be interested in. 
Thanks

---

### Post by bitwisespecificity on 2011-09-09
After reading this request i thought it sounded really handy so i tried to figure it out. No luck, but i think i will be setting my COPY command to Ctrl-C. Then i'll use the following workaround for sending a "BREAK":

[LIST=1]
[*]Press Ctrl-Z to send the current process to the background
[*]You are back at the prompt. Enter the command: [FONT=Courier New]kill %1[/FONT]
[/LIST]
Not quite as fast as Ctrl-Shift-C, but it works. Also, it's not quite the same thing, since the kill command sends a SIGTERM by default, whereas Ctrl-C sends a SIGINT. When i really need the exact same thing as the traditional Ctrl-C i'll use a more exact translation:


[LIST=1]
[*]Ctrl-Z
[*][FONT=Courier New]kill -SIGINT %1[/FONT]
[*][FONT=Courier New]fg[/FONT]
[/LIST]
Here are some examples, killing the "cat" command both ways. I also run [FONT=Courier New]jobs[/FONT] a few times so that you can see that with the SIGINT you have to run [FONT=Courier New]fg[/FONT] in order for the job to go away.

```
bitwisespecificity@boxy ~ $ cat
abc^Z
[1]+  Stopped                 cat
bitwisespecificity@boxy ~ $ jobs
[1]+  Stopped                 cat
bitwisespecificity@boxy ~ $ kill %1

[1]+  Stopped                 cat
bitwisespecificity@boxy ~ $ jobs
[1]+  Terminated              cat
bitwisespecificity@boxy ~ $ jobs
bitwisespecificity@boxy ~ $ 
bitwisespecificity@boxy ~ $ 
bitwisespecificity@boxy ~ $ 
bitwisespecificity@boxy ~ $ 
bitwisespecificity@boxy ~ $ cat
abc^Z
[1]+  Stopped                 cat
bitwisespecificity@boxy ~ $ jobs
[1]+  Stopped                 cat
bitwisespecificity@boxy ~ $ kill -SIGINT %1

[1]+  Stopped                 cat
bitwisespecificity@boxy ~ $ jobs
[1]+  Stopped                 cat
bitwisespecificity@boxy ~ $ jobs
[1]+  Stopped                 cat
bitwisespecificity@boxy ~ $ fg
cat

bitwisespecificity@boxy ~ $ jobs
bitwisespecificity@boxy ~ $
```

---

### Post by ursubaloo on 2011-09-09
Thanks for the tip bitwisespecificity.

If there is a way to assign a hotkey in linux to do these 3 commands automatically when you press Ctrl Shift C then that would work for inverting them.

In the meantime I'll use your system as well.

Thanks!

---

### Post by ursubaloo on 2011-11-15
I came across a convenient solution here: 

[http://superuser.com/questions/160388/change-bash-shortcut-keys-such-as-ctrl-c](http://superuser.com/questions/160388/change-bash-shortcut-keys-such-as-ctrl-c)

Basically set a new hotkey (like ctrl+k) to SIGINT via stty:

[FONT=Courier New][SIZE=3]stty intr \^K[/SIZE][/FONT]

Then just set ctrl+c to copy in the terminal keyboard shortcuts and problem solved. Not quite sure how to map to "ctrl+shift" combination, but I'm still  :)

---

### Post by carranty on 2011-11-15
I'm genuinely surprised there isn't a simple way of remapping the break command to Ctrl-Shift-C.  When I first read your post I thought it would be simple, but 20 minutes of searching later and I still can't do it!

---

