---
title: "How do you un-crash an application?"
date: 2010-01-02
forum: General Help
---

### Post by the lemming on 2010-01-02
Picture the scene, you're playing a game like Supertuxcart or Open Arena and the screen freezes which hints at something that has crashed.

Well this happened this weekend when my mate's kids were playing those games on my laptop running Ubuntu 9.10.

All I could think of to resolve the issue was to hit the Power Button and restart my laptop.  I am assuming that this is not exactly a good thing to do but at the time I could not think of anything else to do seeing as the screen froze and I could not use the mouse or pressing any buttons.

Anybody got any ideas on how to un crash an application with out hitting the power button and forcing a re-boot?

Cheers

---

### Post by louieb on 2010-01-02
Couple of ways to softer landing.


[LIST]
[*]ctrl+alt+f1
[*]log in
[*]```
sudo reboot
```
[/LIST]

or remember "Raising skinny elephants is utterly boring"

alt+SysRequest+r 
alt+SysRequest+s 
alt+SysRequest+e 
alt+SysRequest+1 
alt+SysRequest+u
alt+SysRequest+b

:lolflag: Google the phrase if you want to know more.

---

### Post by impact on 2010-01-02
There's even cooler way, but it only works if the computer is not totally frozen. Try pressing the ctrl+alt+f1 and see if you can get to a terminal.

After the ctrl+alt+f1 and successful login, type 

ps -e 

to list all running processes. The list will be kinda long, so if you know the name of the crashed application (ie. tuxracer), you can instead type

ps -e |grep tuxracer 

to filter the results and only display processes that contain the word tuxracer. (grep tux or grep racer would also work, since grep understands partial matches). The command should display something like this:

 5564 ?        00:00:00 tuxracer

The first number (PID) is an identifier, you have to remember it or just write it down. 

Now that you know the PID, you can use the knowledge to terminate the crashed process. Use the kill command with a "-9" switch and the PID afterwards like this:

kill -9 5564 

After this is done, check with ps again. The crashed process should be gone. You can now logout from the terminal by pressing ctrl+D and then return to X by pressing ctrl+alt+f7. 

Note that there are multiple terminals available under the keys ctrl+alt+f1-6. It doesn't really matter which one you use.

---

