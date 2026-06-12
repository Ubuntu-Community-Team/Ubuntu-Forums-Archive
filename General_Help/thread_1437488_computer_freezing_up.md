---
title: "computer freezing up"
date: 2010-03-23
forum: General Help
---

### Post by Chuck_N on 2010-03-23
oh man, I thought Ubuntu was supposed to be solid.
well, so far, it's not for me; my computer keeps freezing, leaving me no option but to hold down the power button. 
At least I think there's no other option.  mouse will move but can't select anything. Hmmmm, could it be the problem is with the mouse?

   I've reactivated a used Compaq Presario with only 256 meg Ram.
I do plan to kick up to a gig or so of ram, but I doubt that's the problem.
I'm using 9.10 KarmicKoala for about two weeks now, my first non-windows OS.

It happens at totally random times, sometimes right after bootup, usually within 30 minutes of bootup.
   Any ideas on what to check out?  
              thanks, Chuck

---

### Post by Serpher on 2010-03-23
Ubuntu isn't as solid as other distros, but I think you're problem is hardware related. Laptops are tricky to get working under the Linux Kernel as they're made to run Windows, and nothing else, and don't release the blueprints to their chipsets. Had this happen on another HP computer, froze up and got weird lines everywhere.

If you're curious and have the time, go into terminal and run the command 'lspci' and google all the chipsets eg: Ubuntu 82801G

---

### Post by Rasa1111 on 2010-03-23
Hi Chuck, 

can you try to turn off compiz/special visual effects?

Go into the System menu at the top~ System>Preferences,>Appearance>  in the visual effects tab,  see if "none" is selected, if not, select 'none',  and see if that helps. 

 hopefully it does. let us know.

---

### Post by Chuck_N on 2010-03-24
this is a SR1503WM, a desktop not a laptop.

---

### Post by Chuck_N on 2010-03-24
okay, I'll do that later.  Right now I'm running with WOT disabled and so far no troubles.  If/when  it freezes again, I'll put WOT back in and follow your instructions. 
(maybe tomorrow, I'm fallin' asleep at the keyboard again.....)

---

### Post by |{urse on 2010-03-24
out of curiousity, what model presario and what cpu? How old is the hard drive also? You might want to run memtest on the ubuntu livecd also to eliminate ram from the equation.

---

### Post by Serpher on 2010-03-24
I remember now. The computer I was working on was a parsario. Tried to open up OpenOffice and I got a bunch of weird lines on my screen and it just froze up just the way you described. If you get it working I'd love to know how.

---

### Post by Chuck_N on 2010-03-24
SR1503WM Presario,   I'm a novice with Ubuntu, how do I find out CPU data?
I don't think I have liveCD; can I run memtest under 9.10?

---

### Post by |{urse on 2010-03-24
The disk that was used to install ubuntu is also referred to as the livecd. If you boot to that disk there will be an entry on the main menu for memtest.

---

### Post by |{urse on 2010-03-24
It's not really relevant, i was just curious.. you may however want to open ur case up and make sure the processor fan is actually spinning.

in the ubuntu desktop menu under accessories is the terminal, open it and run this command

```
cat /proc/cpuinfo
```

There should be several lines of info on your cpu there. I only asked because I've seen this behavior on 2 presarios with celerons. Coppermine to be exact.

---

### Post by Chuck_N on 2010-03-24
ran memtest for 8 hours.  no errors.
booted.  selected firefox to run
cursor turned round, spun for a while, and froze. FF did not run
cursor arrow remains active but nothing happens

rebooted and I am here now.....

---

### Post by Chuck_N on 2010-03-24
> **Rasa1111 said:**
> Hi Chuck, 

can you try to turn off compiz/special visual effects?

Go into the System menu at the top~ System>Preferences,>Appearance>  in the visual effects tab,  see if "none" is selected, if not, select 'none',  and see if that helps. 

 hopefully it does. let us know.

that was a good guess. but sorry, NONE was already selected.
I have tried to change that setting before, but got an error message and was required to leave it set to NONE.

---

### Post by Chuck_N on 2010-03-24
just tried it again.  it said  Searching For Drivers
then said  Desktop Effects Could Not be Enabled 
and reset to NONE

---

### Post by Chuck_N on 2010-03-24
I put web of trust back in, since freezing is still occuring

---

### Post by Fxy on 2010-03-24
Your problem could be that your computer is over heating, due to a fan related problem...

One thing you could try is booting into your livecd to see if you still have any problems, if you don't then your problem is located within your current ubuntu installation...  I had problems similar to yours before and fixed them by reinstalling ubuntu ;)

---

### Post by Chuck_N on 2010-03-24
case is open; 2 fans running fine.

Is there a system backup,  such as Microsoft's System Restore?

---

### Post by Fxy on 2010-03-25
If you do a google your sure to find opensource software that will back up your current ubuntu installation, thought if your having problems its far better to backup only the files you need & not the whole os...

---

