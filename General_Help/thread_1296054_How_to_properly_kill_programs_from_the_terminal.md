---
title: "How to properly kill programs from the terminal?"
date: 2009-10-20
forum: General Help
---

### Post by dillandriskell on 2009-10-20
Hi,

I'm a terminal junkie and I've begun opening and closing all my applications from the gnome-terminal.  This is the command I'm using to close programs;

```
kill -1 <ps id number>
```-1 being SIGHUP, which I was under the impression sends the appropriate signal to the program to shut it down normally, as opposed to SIGKILL.  However, when I kill a program it seems to be just closing it rather than shutting it down properly.  Like if I close Firefox I get the "Firefox did not shut down properly, restore previous session?" alert, and with OpenOffice I get the "Recover document?" alert.

So here's my question, how can I kill or close a program appropriately without a "dirty shutdown"?  Is it another form of SIG or a command seperate from "kill" entirely?

---

### Post by dvlchd3 on 2009-10-20
I thought not specifying a -# would send the normal kill signal.  If something doesn't want to end normally, that when I specify a number. (usually 9 just so I know it will kill the process)

However, I am by no means a ps kill or killall expert.

---

### Post by sdowney717 on 2009-10-20
[http://www.linfo.org/killall.html](http://www.linfo.org/killall.html)

i find killall to be easier to use. but these commands are terminating malfunctioning programs, so you would expect this behavior when restarting them.

---

### Post by dillandriskell on 2009-10-20
That's a good point dvlch3, so I went ahead and tried it but unfortunately got the the same results :(

> **sdowney717 said:**
> 
i find killall to be easier to use. but these commands are terminating malfunctioning programs, so you would expect this behavior when restarting them.

Yeah, now that I think about it you're right about them being intended for terminating malfunctioning programs.  Therefore I doubt I'll be able to do a proper shutdown with any form of a kill command.

Does anyone know what I could use an alternative?  Something that would close the program as if I manually closed it?

---

### Post by P4man on 2009-10-20
Think this might be what you're looking for:

```

sudo apt-get install wmctrl
```

```
wmctrl -c "name of window"
```

more info:
```
man wmctrl
```

---

### Post by dillandriskell on 2009-10-20
Thank you P4man!

I've installed it and it works perfectly!  Exactly what I was looking for!  And it has many other functions that could be very useful as well.

Again, thank you.

---

### Post by P4man on 2009-10-20
Great :)
 Now can you explain to me wny on earth you'd want to close windows that way and not by just clicking the close button (or pressing alt F4 if you got some medical situation making a using a mouse difficult) ?

---

### Post by donato roque on 2009-10-20
Hello p4man,
actually thank you for giving the answer here on this thread,
been trying to find how to close windows using the terminal too.
sometimes you just don't want to lift your hands from the keyboard to the mouse, and lift it back to its proper place in the keyboard.  
when you're touch typing, it's distracting.

---

### Post by gdonwallace on 2009-10-20
I always use the Kill -9.  That way I know that the program is going to terminate.

If the program is using a lot of memory you can run "top" (without the quotes) from your terminal.  Top shows all running processes on your computer.  Do a "shift + P" to re-order the display to show my memory usage.  Type "K" and it will send a kill command to the PID that is associated with that program.

I generally have a terminal running just top so I can always see what is happening and catch any run away processes before they eat up to much memory.

---

### Post by dillandriskell on 2009-11-16
> **P4man said:**
> Great :)
 Now can you explain to me wny on earth you'd want to close windows that way and not by just clicking the close button (or pressing alt F4 if you got some medical situation making a using a mouse difficult) ?

Oof, I just saw this :P

Haha, I have no excuse I'm just a terminal junkie and I was curious.  Honestly I probably just use the close button/alt F4 more often since you've given me this program.  I'm also going to try the "CLI only" challenge, where I try to go a month without using a desktop environment at all for a month, just a console.  Again, no particular reason other than maybe learning a thing or two.  So I've been doing a lot of heavy research on how to basically do everything straight from bash.

EDIT: Of course this would be irrelevant without a desktop environment, I guess I was more curious if it was possible :P

---

