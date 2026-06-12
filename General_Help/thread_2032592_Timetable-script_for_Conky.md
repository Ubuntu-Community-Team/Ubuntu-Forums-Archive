---
title: "Timetable-script for Conky"
date: 2012-07-24
forum: General Help
---

### Post by Kols on 2012-07-24
Good evening!

Third year of my bachelor in engineering is coming up in a few weeks, and in that regard, I could need a nifty timetable.

I'm not skilled in writing new codes and scripts, but I'm fairly good at editing existing codes to suit my needs. This thread is for people willing to help me write a simple (I think it's pretty simple) code for giving an output in conky to say which classes are going on at a given day.

Sudo code for what I'm guessing must be a script

INPUT

[time] 

Monday
  Subject X, time 0900-1200 hrs
  Subject Y, time 1300-1500 hrs
Tuesday
Wednesday
Thursday
Friday
Saturday
Sunday
#same goes for remaining days

OUTPUT

#to display current subject
if [time] is [range week], [range hrs]
   display correlating input within range of week and hrs

#to display first next subject
display next [range week], [range hrs]

end


Sudo code for using the script in conky

#well, that depends on how the script was made, I guess - still, I don't know how to do that=P
 

Okay! I hope you understood what I meant, and that someone takes an interest in this project. I'm thinking it's actually quite easy, but then again; I don't have that knowledge. 

So thank you in advance, if you wanna help me with this!

Cheers!

---

### Post by dino99 on 2012-07-24
rebuilding the wheel :P

[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

but if you need some planning tool, then "search" into the package manager

example:
Org-mode is a mode for keeping notes, maintaining ToDo lists, and
doing project planning with a fast and effective plain-text system.

---

