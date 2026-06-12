---
title: "Ubuntu 10.04 goes to terminal after login"
date: 2010-06-03
forum: General Help
---

### Post by thisisnew on 2010-06-03
After logging in, it goes straight to a terminal.
 
Please help me get on to my desktop

---

### Post by daamaya1982 on 2010-06-03
Are you in runlevel 5 or runlevel 3? You probably just need to change your runlevel to 5... Are you getting a gdm or kdm splash screen for logging in?

---

### Post by thisisnew on 2010-06-03
Sorry, but I'm new to ubuntu.. and don't really know what im doing. I just installed ubuntu last night.
 
Today I ran updates and shut off my computer only to turn it on a few hours later and have this happen

---

### Post by daamaya1982 on 2010-06-03
Alright, at the command line type in /sbin/runlevel and tell me if the number is 3 or 5...

If it is 3, then vi /etc/inittab and find this line:

```

id:3:initdefault:

```

and change it to:

```

id:5:initdefault:

```

---

### Post by thisisnew on 2010-06-03
i got "N 2"

---

### Post by T-rock007 on 2010-06-03
After you log in just type startx and your x server will start.

---

### Post by thisisnew on 2010-06-03
ive tried that and i got "X: user not authorized to run the X server, aborting."

---

### Post by daamaya1982 on 2010-06-03
> **thisisnew said:**
> i got "N 2"

Alright, I am not 100% sure how Ubuntu deals with this. As a CentOS user I am used to RL 3 being text and RL 5 being GUI...

Try this and let me know what happens: sudo service gdm start

---

### Post by thisisnew on 2010-06-03
i got "start: Job is already running: gdm"

---

### Post by daamaya1982 on 2010-06-03
Edit this file /etc/X11/Xwrapper.config and make sure this line exists:

```

allowed_users=anybody

```

Then reboot your machine.

---

### Post by thisisnew on 2010-06-03
my permission was denied

---

### Post by daamaya1982 on 2010-06-03
> **thisisnew said:**
> my permission was denied

Use sudo to edit the file. Ubuntu protects itself from the user...

```

sudo vi /etc/X11/Xwrapper.config

```

If you're not comfortable with vi, then use nano or pico.

---

### Post by dcstar on 2010-06-03
> **thisisnew said:**
> Sorry, but I'm new to ubuntu.. and don't really know what im doing. I just installed ubuntu last night.
 
Today I ran updates and shut off my computer only to turn it on a few hours later and have this happen

Since you have a brand new system and it looks like an update may have gone wrong, it may be better to do a complete reinstall rather than spend time trying to fix a system with a difficult problem.

You may end up wasting a lot of time and getting very frustrated if you are not familiar with diagnosing and fixing these things, so if you aren't going to lose any data then I would advise you to just do another install.

---

### Post by daamaya1982 on 2010-06-03
> **dcstar said:**
> Since you have a brand new system and it looks like an update may have gone wrong, it may be better to do a complete reinstall rather than spend time trying to fix a system with a difficult problem.

You may end up wasting a lot of time and getting very frustrated if you are not familiar with diagnosing and fixing these things, so if you aren't going to lose any data then I would advise you to just do another install.

Uh, why would he need to do that? I think the purpose of troubleshooting is to learn. If every time someone ran into an issue they just did a reinstall, we'd have something similar to the Ubuntu community :P

---

### Post by thisisnew on 2010-06-03
do i need to save or something after i change it to "anybody" ?

---

### Post by dcstar on 2010-06-03
> **daamaya1982 said:**
> Uh, why would he need to do that? I think the purpose of troubleshooting is to learn. If every time someone ran into an issue they just did a reinstall, we'd have something similar to the Ubuntu community :P

This is not a simplistic "every time" recommendation that only a moron would make - it is based on the obvious facts that the OP stated:

[I]Sorry, but I'm new to ubuntu.. and don't really know what im doing. I just installed ubuntu last night.

Today I ran updates and shut off my computer only to turn it on a few hours later and have this happen[/I]

If you want to indulge yourself and waste the OPs time in trying to find out why a brand new system is broken by trying to get an obviously inexperienced user to do all sorts of things then go ahead, chances are that it will waste a lot more time than simply following my advice in this particular situation.

You decide, do you want the OP to have a usable Ubuntu system in the shortest time or do you want to indulge in something that **you** want?

---

### Post by daamaya1982 on 2010-06-03
> **thisisnew said:**
> do i need to save or something after i change it to "anybody" ?

If you did not save, why would you do it in the first place? Seriously, of course you need to save.

---

### Post by thisisnew on 2010-06-03
How do i save?

---

### Post by daamaya1982 on 2010-06-03
If you are using vi, hit esc and then ":wq"...

---

### Post by RedRat on 2010-06-03
I must agree with dcstar. This is a newbie who is completely unfamiliar with the command line, yet alone vi. Vi is for pros and those who are comfortable editing with it. I used it years ago and do not like it at all. 

The best thing to do here is just re-install Ubuntu and go from there. Don't be asking a newbie to do all these things. It is clear that he/she is lost, nothing wrong with that, we are all at that stage.

---

### Post by T-rock007 on 2010-06-03
You can try ctrl+alt+F7 and that might take you to gnome.

---

### Post by TheCoffeeKid on 2010-06-30
I had this same problem and I tried all of the steps mentioned with no success. I'm a newbie as well, but I continued to look for solution and found this command: sudo apt-get install ubuntu-desktop

After I rebooted, everything popped up with all of my settings, preferences and more importantly, all of my files intact. I think I accidently removed a gnome component when I was deleting some of the default software I didn't want.

I feel that I must comment on some of the attitudes displayed on this thread. First, newbies need to realize that if someone is doing them a favor by helping them, they need to help themselves. When I was running through some of these fixes, I did some research on my own to figure out how to implement them. For instance, I had no clue on how to use vi, but a quick google search gave me a list of commands and a run down of the program. So I was able to try the fix without hectoring the advanced users with rudimentary questions. So, seriously noobs (myself included) try not to be handholders.

As for the helpers, don't be too quick to dismiss someone. If I had followed your advice I'd be spending the rest of my day downloading apps and trying to recover data.

Anyway, thanks for the help!

---

### Post by Lord Lance on 2010-07-27
> **daamaya1982 said:**
> Edit this file /etc/X11/Xwrapper.config and make sure this line exists:

```

allowed_users=anybody

```Then reboot your machine.

Hallo people.
I'm another "noob" with a little brain but lot of desire to improve.  Men, I had the same problem, and I follow yuor instructions until I  arrived to edit the file.
VM is very unfriendly, but "nano" command is really simple, like the old DOS edit.  Simply follow the key combinations you see on the bottom (CTRL+O to  save, CTRL+X to exit) and you done!!!
So, after the file modify, I rebooted and all was OK! :popcorn:

No idea what caused the error, but now my system start X right, and I can re enter using my vncviewer, 'cause I have no monitor and I use remote viewing to pilot my ubuntu "mule" PC.

Finally, a friendly "f**k you" to the helpers that wanted we give up and format the PC... It was really simple to fix the damage, and this time I avoided the universal Windows solution... "To format everything".

---

### Post by deedsofhaphazzard on 2010-08-27
Hi,
I seem to be experiencing the same problem as well. I've tried all the solutions mention, but in vain. I also tried to re-install ubuntu to see if that fixes the issue. Unfortunately, it boots up alright a few times after the installation but ends up at the terminal after 4-5 boots.

I am using a HP G62 144DX laptop. Is this a generic issue seen on many machines or is this device specific ?

---

