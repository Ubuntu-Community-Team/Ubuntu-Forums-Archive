---
title: "Turning Numlock on and off Without a Keyboard"
date: 2010-04-19
forum: General Help
---

### Post by -nat- on 2010-04-19
I'm using a laptop that doesn't have a numlock key and would like to be able to switch numlock on and off without having to plug in an external keyboard.
Is there a command or app that will let me do this?

Thanks.

---

### Post by colorlessprism on 2010-04-19
on my msi wind i have to push (Fn+Ins) for my numlock. post what kind of laptop you use and maybe we can find out what key combo would work for you

---

### Post by -nat- on 2010-04-20
I don't have an Insert key, but my keyboard is the same as this: [IMG]http://images.apple.com/keyboard/images/gallery/wireless_1_20070807.jpg[/IMG] (MacBook)
I would however prefer a command or app rather than a key combo.

---

### Post by colorlessprism on 2010-04-20
i forget not everyone is/wants to be a keyboard ninja, try this:
sudo apt-get install numlockx

numlockx has three options:
on - turns numlock on in x ( default )
off - turns numlock off in x
toggle - toggles the numlock on and off in x

you can run this in the command line like this:
numlockx off

but maybe you are a mouse ninja and dont want to be bothered opening shells to do this. so lets write a very simple script.

#/bin/bash
numlockx toggle

save this as numlock.sh and set as executable (chmod +x). now create a desktop shortcut, and you have a simple mousable way to turn the numlock on and off

---

### Post by -nat- on 2010-04-20
Cool, thanks for that, I'll try it out now.

---

### Post by bororeh on 2011-04-11
Hi!

I've also a small tiny doubt!

I use a separate keyboard on my laptop and I usually do not turn numlock off when I remove it. So, the next time I restart the computer using the laptop's own keyboard, the numlock still on and I type numbers instead of letters.

So I've installed the NumLockX (already tested and it is working properly) and added to the startup applications the command "numlockx off".

This way I thought numlock would always be off when I started my laptop. But it's not working and I have no idea of what may be going on.

Did I do something wrong? Is something missing? Thanks!

---

### Post by TeoBigusGeekus on 2011-04-11
Create a script
```
#!/bin/bash
sleep 5
numlockx off
```
Save it as numlockoff in your home folder, make it executable
```
chmod +x ~/numlockoff
```
and add this command at your startup applications
```
bash ~/numlockoff
```
Play with the sleep command parameter (5) to see if you need more or less delay for the command to work.
Reboot and post back with the result.

---

### Post by bororeh on 2011-04-11
Hey, first of all thanks for the assist.

This procedure also did't work. Another thing to try out?:popcorn:

---

### Post by TeoBigusGeekus on 2011-04-11
Have you tried increasing the value in the sleep command, to 10 for example?

---

### Post by bororeh on 2011-04-11
Yes, I tried 5 and 10 but no sucess.

EDIT: 1 also didn't work.

---

### Post by TeoBigusGeekus on 2011-04-11
One last thing from me to try:
```
#!/bin/bash
sleep 10
numlockx off &
```

---

### Post by bororeh on 2011-04-15
> **TeoBigusGeekus said:**
> One last thing from me to try:
```
#!/bin/bash
sleep 10
numlockx off &
```

Still nothing!

Look at this (also didn't work for me):
[http://www.spotht.com/2010/12/how-to-turn-on-automatically-numlock-at.html](http://www.spotht.com/2010/12/how-to-turn-on-automatically-numlock-at.html)

(Hey, sorry for the huge delay to answer!!) ):P

EDIT: I don't know... but I might forget this issue and just turn it on/off when I need it to. Also... a better script would turn numlock ON if the external keyboard is plugged and, otherwise, off.

---

### Post by TeoBigusGeekus on 2011-04-15
Ok, open a terminal. Do the following commands work for you?
```
numlockx off
numlockx on
```

---

### Post by bororeh on 2011-04-15
Yes, I've checked that. These work perfectly!
Something I think it's wierd is:

If numlock is OFF and I type "numlockx" (without the on/off part), it turns numlock ON.
But if numlock is ON and I type "numlockx" (without the on/off part), it does nothing. Shouldn't it toggle on/off?

("numlock toggle" works normally)

---

