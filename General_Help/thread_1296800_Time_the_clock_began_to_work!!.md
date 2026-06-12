---
title: "Time the clock began to work!!"
date: 2009-10-21
forum: General Help
---

### Post by shankar13 on 2009-10-21
I have a dual boot XP/Ubuntu 9.04 running on a laptop. Post the Ubuntu install, the system clock is off by half a day or so. And on XP too. I happen to have an MS in CS, have worked with Unix a lot, and have no shame admitting that I can't fix this problem by myself.  
 

 These are workarounds I have tried _unsuccessfully_, after browsing through several sites:


 
[LIST=1]
[*]Make sure the time zone setting is     correct – it is (Asia/Kolkata).
[*]Change UTC=yes to UTC=no in the     rcS file. It was set to NO when installed!
[*]Create /etc/cron.daily/ntpdate and     look up ntpdate from ntp.ubuntu.com, and restart. Did that.
[*]Sync with Internet servers through     Time & Date manager. Done that. Nothing happens.
[/LIST]
 On a completely _connected_ note, the time's ripe on the evolution clock for this "feature" to be fully laid to rest. It's been 9 versions down and an OS still has problems with clock time?  How would you explain this to an audience of high school principals that I wish to lecture this weekend on the virtues of FOSS? 

For the developer out there who downplays such issues after 9 versions (witness the hundreds of responses online), here is what a fix would mean:  
 

 
[LIST=1]
[*]When you     send a mail, it goes out timestamped now, not yesterday, not     tomorrow. It will not land at the bottom of your friend's mailbox,     unopened and unread.
[*]You don't have to type incoherent     stuff into a terminal window.
[*]You don't need to know what UTC or     GMT means: you're not on that 5th grader show.
[*]There's more to a computer than     the OS. Like the world outside that I'd like to connect with.

    
     I appreciate the attempts made by the     Linux developer community to address and remedy issues via such     forums. However, repeatedly suggesting that users fix their clocks     after installing the OS (“if it bothers them”) is like asking     new car owners to make sure all cylinders are kicking before     starting the car.
[/LIST]
 

 Dual boots are a necessary evil in this period of transition. In the history of software conversions, one trend stands prominent. Visicalc users considered switching to Excel, since Excel knew how to load Visicalc _and_ it offered much more. I pray for a similar seamless migration to Linux. It would if  development priorities are kept straight – may the focus be on the “unsophisticated” end-user and not a sys admin.  
 

 Apple did a fantastic job of hiding the Terminal window. Next stop, Ubuntu?  
 
Shankar
 

 PS: Sorry if my rant is oft-expressed or ill-placed. It's hightime we called an OS an _operating_ system.

---

### Post by dmizer on 2009-10-21
Have you checked the bios to make sure the bios clock is accurate? While I realize that both Windows and Ubuntu should be able to adjust the bios clock, it's still worth checking.

---

### Post by DeMus on 2009-10-21
Replace the battery on your motherboard. A clock not running on time is the first sign the battery's life has come to an end.

---

### Post by egalvan on 2009-10-21
+1 for checking the battery.

(if the time is changing between boots, sure sign of low battery)



On a completely connected note, (and with much rambling)

This has nothing to do with FOSS.

This is a difference in philosophies between Microsoft and everyone else.

Microsoft assumed that there was one user, running one OS, on one computer, connected to no-one else.

*nix and others assumed that there was one or more users, running one or more OS's, on one or more computers, connected to one or more machines, in one or more time zones, in one or more countries.

On computers, there is a hardware clock and a software clock.
The hardware clock is always running, and has a battery back-up.
The software clock is only running when the OS is running.

Having all OS's and hardware on the exact same clock vastly simplifies housekeeping and logging.
It also simplifies the software needed to set and read the time.
(another *nix philosophy... "a program/utility should do one thing, do it simply, and do it well".)

Having the hardware clock synchronized to GMT/UTC makes for a MUCH simpler approach.
GMT/UTC is a world-wide standard.
No need to account for differences in zones.


In fact, the only time you really need to know the "local" time is when displaying the local time.
Then all that is needed is the time zone you want to display.
Which is one function of the OS. Not the hardware.


If your laptop uses this method of time-keeping, you would still have accurate times even if you traveled to Timbuktu.
No need to reset to the "local" time zone, unless you need to know the local time.
Your emails would always have the correct time on the receiving end.
No matter where in the world you sent them from, or to.
Because the time is based on a world-wide standard.
If you sent me an email at 0435UTC, no matter from what part of the world,
I would receive it with the proper time when it was DISPLAYED on *my* system, on *my* time zone.

Contrast this with Microsoft's approach.
Every machine is set to it's own time.
Software needs to account for this, so it's more complicated, and bloated.
What time zone what it sent from? What time zone is it sent to?
What if a zone is off?
what if you traveled half-way around the world?
Unless you kept up with the different time zones, your emails would hav the wrong time.

Yes, it's exactly the fact that FOSS knows, admits and accepts "the world outside the OS exists" that makes the FOSS approach superior.

And FOSS even gives you the choice...
Use a local hardware clock (Microsoft Standard)
Use a GMT/UTC clock (everyone else)

Microsoft does only gives you their choice. It's their way, or their way.


Sorry about the rambling, but it gets me a bit upset when folks claim to have "MS in CS, and worked with Unix a a lot"
and yet have no clue to setting times, or why GMT/UTC has advantages.
And then blame everyone else but Microsoft.
Even when the problem is "And on XP too"

---

### Post by raprap30 on 2009-10-21
Is youre a Wubi installation? I had the same problems when I had Wubi. I had found out that if your spend a certain amt of  time in the certain OS, the time in the ither OS will stop, while the OS that you are currently using will continue to move. ARgh im confused too.

---

### Post by dar25 on 2009-11-03
Ive had this problem in the past. It's because Unix and Windows count (and adjust) for time zone differently.

Check out the following post:

[http://ubuntuforums.org/showpost.php?p=7184210&postcount=6](http://ubuntuforums.org/showpost.php?p=7184210&postcount=6)

Good luck!

---

