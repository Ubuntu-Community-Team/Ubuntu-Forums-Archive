---
title: "Firefox in Ubuntu 11.10 and table rendering"
date: 2012-01-09
forum: General Help
---

### Post by esteeven on 2012-01-09
Hello

I need to input sports result data on a website quite regulary. The table appears offset in Ubuntu (using Firefox and Chrome) ie the input boxes do not match with the vertical input descriptions. Consequently, the table is longer than it should be and the input boxes don't match up with the input descriptions. This does not happen on my Arch box - the table renders perfectly. I don't know where to start looking for a solution to this problem.

---

### Post by esteeven on 2012-03-12
nobody? :oops::-({|=:-({|=:-({|=

---

### Post by esteeven on 2012-03-16
Arch is currently using Firefox 10 but this problem has been present for quite a number of months and version upgrades of Firefox. What happens is this : there are two input cells side by side (where I add results of football (association) matches. These cells align with a team name eg

Team One [input 1] [input 2]
Team Two [input 1] [input 2]

Firefox in Arch renders the page as intended. The input cells are aligned with the team names. This also works in Firefox in Windows.

In Ubuntu, the cells are displayed on top of each other :

Team One [input 1]
[input 2]

This, unfortunately, causes the input boxes to become misaligned ie they are no longer next to the team they are associated with.


Team One [input 1]
Team Two [input 2]
[input 1]
[input 2]

Matching teams with the correct input boxes becomes a nightmare. Aaaaargh.

I can't give you a link because it's a password protected site. Here's what it should look like:
[http://i39.tinypic.com/2ev8bi1.png](http://i39.tinypic.com/2ev8bi1.png)

Here's what it looks like in Ubuntu 11.10 using Firefox 10

[http://i41.tinypic.com/ebdgr7.png](http://i41.tinypic.com/ebdgr7.png)

I have tried adjusting the fonts within Firefox but to no good effect. 

Just to stress - I am using this site and not building it.

---

### Post by squilookle on 2012-03-16
Odd. Not sure where to start with that one. 

I assume you are using Firefox from the repositories. 

The only thing i can think of is to try Firefox from the [Mozilla website]("http://www.mozilla.org/en-US/firefox/all.html") to see if you get the same issue? If it fixes it, great! (But you won't get the updates from Ubuntu). If it doesn't fix the issue, it might rule out any issues with the build of Firefox in the repositories and point to an issue caused somewhere else in Ubuntu (i.e raise more questions than it answers :))

Good luck

---

### Post by esteeven on 2012-03-16
(Thanks but... ) I have already tried that. Same result. This is such an irritating problem.:confused:

---

### Post by esteeven on 2012-03-16
Result. I don't get the same problem in Fluxbox but I do in Gnome-shell and Unity. Any ideas?

---

### Post by esteeven on 2012-03-16
Ah ha!!!!! :guitar: Fantastic. I removed the Ubuntu font family and set up Dejavu Sans on my desktop. Problem gone!!! I'm gonna party like there's no tomorrow. :)

---

### Post by squilookle on 2012-03-16
Well done. Glad you managed to fix it.

---

