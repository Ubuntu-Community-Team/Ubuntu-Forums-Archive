---
title: "ACPI thermal zone configuration"
date: 2010-08-31
forum: General Help
---

### Post by sighthnd on 2010-08-31
I originally installed Kubuntu 7.10 on an ACER laptop (exact model escapes me at the moment) and subsequently upgraded to 9.10 and then to 10.04.

Starting with 9.10, I had problems with the computer suddenly turning off in the middle of doing work.  Eventually, I figured out that when this happened, the bottom panel had gotten quite warm so it probably a thermal control measure.  Further, I discovered that I could prevent this by setting the power regulator to powersave, which effectively kept frequency scaling at 50% and under which I never had the computer suddenly turn, the only exceptions being when unplugged the computer and replugged it in and it would switch to dynamic power policy thus running at full power.

However, after "upgrading" to 10.04, I can't do anything to restrict frequency scaling.  Whether I set the regulator to powersave, ondemand or anything, CPU frequency can go to full capacity until it heats the CPU to the critical trip point, invoking poweroff.  Sometimes, this would happen just a few minutes after "[FONT=Fixedsys]acpi -t[/FONT]" reported 40C (is there some way to test the output from acpi, I've seen it report obviously wrong figures such as 0C when the room was considerably above freezing?).   While trying to figure out what to do, I discovered the /proc/acpi/thermal directory and subsequently the /sys/dev/... directory.

I would like to know which directory I should focus on and what files in order to establish trip points and direct actions that will force the system to reduce heating so it won't reach critical.  It's not like it's particularly compute intensive tasks triggering this.  I have had it happen while running nothing more than the windowing system, system monitor, terminal and paging through a file with [FONT=Fixedsys]less[/FONT].  I have looked for documentation online but have not found anything that clearly explains what I need to do.  The only parts I understand from what I've found are "[FONT=Fixedsys][critical]: S5[/FONT]", "[FONT=Fixedsys][active][/FONT]", and "[FONT=Fixedsys][passive][/FONT]".  The "[FONT=Fixedsys][passive][/FONT]" line included items like "[FONT=Fixedsys]tc=[/FONT]..." and "[FONT=Fixedsys]device=0x[/FONT]...", but I have no idea whatsoever what any of those settings do and the documents do absolutely nothing to explain them.

Could some please point to some documentation that would explain: 1) what file I need to edit, 2) what options I can set in the file, 3) what values those options can take and 4) what effects those values have on ACPI's behavior.

Lastly, the default setting HAVE GOT TO BE CHANGED.  Having poweroff as the first line of defense against overheating is simply UNACCEPTABLE.  What would happen if this occurs during the middle of a system upgrade?  I know at least enough to figure what needs to be done, even if I can't figure out how to do it.  Many users can't even do that and I don't think they should have to.  The installation process should automatically detect what methods of reducing thermal output available (reducing frequency scaling, throttling, fans) and set trip points that invoke them before reaching critical.

---

### Post by inso_741 on 2010-08-31
thermal shutdown is hardcoded in the processor so you cant change that...however you can keep it from reaching the thermal threshold by using apps like laptop-mode, powertop etc....check [this]("http://www.lesswatts.org/") out
and [this]("http://samwel.tk/laptop_mode/")

also make sure there no resistance to air-flow through the laptop
by cleaning the radiator...helps lower the temps...;-)

---

### Post by sighthnd on 2010-09-01
Allow me to specify what I am trying to do.  I'm not trying to eliminate the response to overheating.  The one thing worse than the computer shutting down is the motherboard/CPU getting fried.  What I'm trying to do is to get the computer to take other steps to prevent reaching the temperature at which it triggers thermal shutdown.

It has only become difficult since I upgraded to 10.04.  Under 7.10, I never had a problem, though I can't say for certain that this was not because it ignored overheating.  Under 9.10, setting the power regulator to powersave kept frequency scaling at 50% which effectively prevented overheating.  Furthermore, under Windoze, it does not get that hot--I can feel the difference, with the same orientation of the laptop in terms of airflow which causes critical heating in Linux.  Under 10.04 I cannot find a straight explanation of what I can do to restrict power usage.

I read the document from lesswattage.com on the ondemand power governor and it somewhat pointed me towards what I need to find out.  I had previously found out about P-states and T-states.  I would like to set trippoint that would raise the P-state and/or T-state if the temperature gets too high.  For instance:

40C: [passive] P1
60C: [passive] P4
80C: [passive] T3

The closest to documentation I've seen if to type "echo" and a string of colon separated numbers redirected to one of the files under /sys.  I know that it's broken into groups of numbers where the first is the trippoint, but there is no explanation of how many numbers are in a group and how the subsequent numbers affect the action taken at the trippoint.  It's sort of like saying to press Ctrl-Alt-F4-Del (and if you can't remember that, just look through the source code in command.com).

I can't show what's in my files under /sys now because I'm running Windoze at the moment because I'm afraid of Linux causing things to overheat.

Finally, how can I alert the developers about the default settings?  If someone is going to have a problem and no clue what to do about it, it is better that the problem be loss of performance that the computer constantly hitting thermal shutdown.  Therefore, the default should be for a trippoint well below critical to force the computer into maximum P-state, maximum T-state with configuration options for a less conservative approach.  Furthermore, there should be a tool with a reasonably intuitive interface that would allow users to control trippoints and actions taken at those trippoints.  One should not have to be a wizard in order to be able to stop one's computer from hitting a critical trippoint.

---

### Post by inso_741 on 2010-09-01
read [this thread]("http://ubuntuforums.org/showthread.php?t=1563911")

---

