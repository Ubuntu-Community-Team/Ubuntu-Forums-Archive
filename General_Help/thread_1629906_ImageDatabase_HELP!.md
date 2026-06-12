---
title: "Image/Database HELP!"
date: 2010-11-24
forum: General Help
---

### Post by thedirtyweeker on 2010-11-24
Hello to all :KS
 
Just like to say that I've been bowled over by Ubuntu so far. I had installed it about 1 year ago, and then within a month got a brand spanky new PC with Windows 7 installed. But I never forgot that month of Ubuntu loveliness.
 
So the brand spanking new PC is a year older (was enjoying Win7) so I thought I'd re-install Ubuntu (dual-boot), just because I was bored.
 
Ever since I've basically not stopped using Ubuntu. Loving how swish it is, the customizability, etc the usual so just wanted to say HIGH FIVE.
 
 
---back to topic---
 
The reason I have come to you is, I cannot find a solution to my Image/Database related problem. In fact I don't even know where to begin, so I just fancied picking the brains of some smart folk around here.
 
My problem is:
 
 have a particular brief for my blog that I'm struggling to deal with at all.

It is a sports blog (UK football / soccer) and the main aim of this little project is to accurately map where goals are scored from. So ultimately, in practice I would like a) A database of every single goal scored (who scored it, what time it was scored, etc) and b) an overhead view of the field where I can graphically display where each goal was scored from.

So for example, say my team was Real Madrid, I would like to apply a filter to my database - goals scored by Cristiano Ronaldo - and then magically on my football field, a graphic representation of all goals scored by Ronaldo.

Below is a much more complicated example of the exact same result, except this is for Thierry Henry at the team Arsenal:

[IMG]http://1.bp.blogspot.com/_gyc95FIYK60/SoFRdKaRYUI/AAAAAAAAS7o/eG6sFB4_d4U/s400/goals3.jpg[/IMG]

So the possibilities in practice would be:
 
Filter by-> Goals scored from long range
Filter by-> Goals scored from header
Filter bt-> Goals scored by goalkeeper
 
etc etc

I am so new to this it's embarassing [IMG]http://forum.codecall.net/images/smilies/vbmodern/set1/crying.gif[/IMG]

In practice I guess I'd need some kind of source database. And then for each single goal record a graphical representation (with a transparant background). And then the filter could layer these on top of a football field background...

I just have no idea how to get from DATABASE to IMAGE [IMG]http://forum.codecall.net/images/smilies/vbmodern/set1/confused1.gif[/IMG]

So....
 
A) Do you think this is a possible/realistic project for a complete noob (coding/databases more complicated than excel)
B) If possible, what do you think would be the best way to implement it? (Access database? ASP? MysQL? Anything!?)
C) This does not have to be online, I can run the "project" offline on my own PC and screen-capture any results and stick that capture jpg on my blog.

D) Thanks in advance for any thoughts [IMG]http://forum.codecall.net/images/smilies/vbmodern/set1/001_smile.gif[/IMG]

---

### Post by thedirtyweeker on 2010-11-24
Sorry mods, didn't realise this was the correct forum....
 
Just if anyone can point me VAGUELY in the right direction would be hugely appreciated.

---

### Post by czr114 on 2010-11-24
Are you describing what needs to be done, or what you're doing now?

If the latter, then what software are you using, and in what format is the dataset?

There's many ways do do any of the several things I think you might be trying to do.

---

### Post by s.shawky on 2010-11-24
there is GNU octave or QTOCTAVE(a gaphical frontend for gnu octave) like matlap which can plot your equation or relationships ,but I am not sure it will help you

---

### Post by bouncingwilf on 2010-11-24
Hmm... this should be moderately doable. Strikes me that there are two main elements.

1. An underlying database of every goal scored which should be carefully designed to include all the parameters (fields) - e.g. Date, name, location, point at which the ball was struck (x,y) , point at which it crossed the goal line (x,y,(z?)), Method (penalty,header etc) etc,etc..)  by which you ultimately wish to filter by (and any you think you may need in the future).  Having got a suitable underlying data block, then set up either pre-formatted SQL queries or design a simply query generator from a form based SQL builder.  At this stage you should be in a position to extract the appropriate dataset, filtered according to your wishes, from the Database.

2. This data should be then presented to a graphing engine to display the data in the required form.


I know I've made it sound simple but it's the sort of thing I used to do as part of my work. It's more tedious than difficult and if you break to down into little steps, you'd be surprised how quickly you can achieve something.

Bouncingwilf.

---

### Post by thedirtyweeker on 2010-11-24
Hi all, sorry I missed all your posts! This forum moves FAST!

@czr - no right now I have NOTHING. I think Boundingwilf actually describes very well what needs to be done, and I thank him for the advice so far. But in fact I'm going to bother him with some IM's  :D

Also thanks to Shawky for the suggestion, I'll also check that option....

---

