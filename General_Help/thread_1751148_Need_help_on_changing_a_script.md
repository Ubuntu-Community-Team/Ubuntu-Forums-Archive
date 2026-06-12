---
title: "Need help on changing a script"
date: 2011-05-06
forum: General Help
---

### Post by Allen-B on 2011-05-06
First off, I'm a complete ruby newb, but I have a macro, and I want it to do a little more than it does. Here's what is is so far:
 
val = pitch
whole = val.round
txt = "#{whole} : 12"
txt << " +/-" if((val-whole).abs >= 0.0625)
txt
 
What it does, is if my roof pitch value is a fraction of a number at least 1/16 under or over, it returns a displayed value of a whole number followed by a +/-.
 
So, a "4 5/8 : 12" pitch would display as "5:12 +/-". What I would like to do, is get it to display to the nearest 1/2 pitch, instead of the nearest whole pitch, or in this case "4-1/2 : 12 +/-"
 
Any idea how I would write it?
 
Thanks in advance!
 
Allen

---

