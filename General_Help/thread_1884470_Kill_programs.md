---
title: "Kill programs?"
date: 2011-11-21
forum: General Help
---

### Post by Agent26 on 2011-11-21
Hi there all,
Today i'm attempting to learn how to kill programs usuing terminal.
 
I understand I need to get the program identity and the command to type kill it, but what do I type, please could someone send me in the right direction.
 
P.s I just bought more ram for my machine bringing me up to a massive 1g now(from 256kmb) so in the future probobly wont need this but just incase...
 
(pressing cntl alt delete wont work for me)

---

### Post by mikegior on 2011-11-21
What I usually do is run 'top' which displays all the currently running processes. I look through the list and determine which process ID (or PID) I want to end.

Example: lets say I wanted to kill Firefox via the CLI. I would run top and see that Firefoxs' PID is 3011, I would then run kill 3011 which would end that particular process.

---

### Post by betterhands on 2011-11-21
ps for the process name...for instance, if i want to kill a gedit process, i do this:

ps -ef | grep gedit

and the output will show me any processes with that name that are running.  then you can kill <process id>.

***didn't see the post above mine before submitting my reply...top is nice in that, as mentioned it will show you all running processes, not just the one(s) you grep for with ps.  but ps'ing without grep will show you more info as well.

---

### Post by mikegior on 2011-11-21
> **betterhands said:**
> ps for the process name...for instance, if i want to kill a gedit process, i do this:

ps -ef | grep gedit

and the output will show me any processes with that name that are running.  then you can kill <process id>.

***didn't see the post above mine before submitting my reply...top is nice in that, as mentioned it will show you all running processes, not just the one(s) you grep for with ps.  but ps'ing without grep will show you more info as well.

I like the idea of utilizing grep, which makes more sense than siphoning through a long list of processes. Regardless, both work. I think I'm going to try betterhands' method though :)

---

### Post by Agent26 on 2011-11-21
Thanks guys for the fast responces, i'm just about to test both methods and see which I prefer, thanks again.
 
I shall leave the thread open for a bit though as I have another realted question but I will try these first.

---

### Post by Elfy on 2011-11-21
you can also just use xkill - type it in the terminal and click on whatever you want to kill

Edit - you can create a launcher to do this as well.

---

### Post by Chris Musampa on 2011-11-21
'killall *appname*' is my weapon of choice.

---

### Post by Agent26 on 2011-11-21
Wow, i,m getting somewhere now, thats 3 techniques, this problem is seriously solved.
Mike I prefer your tecnique. (it seems abit techy) but still happy with all.(forest yours is the quickest):D
 
My next problem is in the unlikley event of a full crash(untill my extra ram arrives of ebay) I would usually go for cntrl alt delete to just restart.
 
Is there a technique or that.
 
but remember, i'm talking a full lockdown where all I could do is move a mouse with the clenched hand but not press anything.

---

### Post by Agent26 on 2011-11-21
Thanks chris.

---

### Post by Lars Noodén on 2011-11-21
There is also [pkill](http://manpages.ubuntu.com/manpages/precise/en/man1/pkill.1.html), which will kill a process by name or regex.

```

pkill -x firefox

```

---

### Post by Agent26 on 2011-11-21
Thanks Lars, plenty of choices now- rouge programs beware!!

---

### Post by Agent26 on 2011-11-21
So I shall head out now but will be back tommorow to see if there are any suggestions on how to get out of a full freeze. (my system has low ram at the mo)
Thanks again

---

### Post by |{urse on 2011-11-21
To kill an indefinitely postponed process from the terminal I usually kill it with

sudo killall -9 whatever

Is that an unsafe practice? Idk (someone can hopefully expand on that)  but it usually works.

You can also hit ctrl + alt + esc, your cursor turns into a skull and crossbones, if the program that is hanging is visible on your desktop, click on it with the skull and crossbones and it will (hopefully) die.

If you are unable to kill the process and are faced with reboot..

Try restarting your x-server instead, right alt + PrintScr (SysRq) + k *be sure youve saved whatever is open that you dont want lost as you will basically be resetting your desktop session.

---

### Post by Agent26 on 2011-11-23
Thank you urse, thats handy to know to.
Love your signiture by the way.
 
Thanks to all for helping me learn new techniques.
I shall close the thread  now.

---

### Post by Ms. Daisy on 2011-11-23
> **|{urse said:**
> You can also hit ctrl + alt + esc, your cursor turns into a skull and crossbones, if the program that is hanging is visible on your desktop, click on it with the skull and crossbones and it will (hopefully) die.
Does  ctrl + alt + esc work on all versions of Ubuntu?  It's not working on my 11.04 :(

---

### Post by |{urse on 2011-11-27
I'm using kubuntu, It works on mine. 

you can always run xkill, it does the same thing.

---

