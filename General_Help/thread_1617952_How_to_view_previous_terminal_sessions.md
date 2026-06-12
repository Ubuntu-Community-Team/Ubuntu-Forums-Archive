---
title: "How to view previous terminal sessions?"
date: 2010-11-10
forum: General Help
---

### Post by stevepetmonkey on 2010-11-10
I often use the terminal to shut down my system whilst watching TV in bed, I use SUDO AT TIME and HALT.
This works a treat most of the time, but a couple of time this week I have woken in the night and the PC/TV is still running? Maybe I mis typed somthing? 
Is there any way I can view previous terminal sessions to check ???

---

### Post by mick222 on 2010-11-10
you can use the up arrow to see previous commands in terminal

---

### Post by stevepetmonkey on 2010-11-10
Thank you, thats will be very useful. 
Not quite what I wanted, I could do with seeing the whole history job numbers etc.

---

### Post by nothingspecial on 2010-11-10
In the future you could use the script command to record your terminal sessions.

There is the history command (same as up arrow)

There is also /var/*[I]l*[/I][I]og/auth.log

[I]Every sudo command you run is logged there.

[/I][/I]```
less /var/log/auth.log
```

press the / key and type "sudo" without the quotes then use the N key to search through them

---

### Post by mister_playboy on 2010-11-10
Your terminal entries are stored in a hidden file ~/.bash_history.  You can modify the length of the history kept by editing ~/.bashrc.  I keep the last 3000 commands. :popcorn:

You can display hidden files in Nautilus with CRTL+H

---

