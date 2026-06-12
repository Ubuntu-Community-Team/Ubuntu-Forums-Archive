---
title: "Gnome Terminal Profiles"
date: 2010-10-21
forum: General Help
---

### Post by oaxacamatt1 on 2010-10-21
Hi All,
I posted this problem a little while ago and did not get any responses.  I was wondering if someone knows the 'right' forum to post this in, Gnome or Ubuntu or ??
Just Curious,
M
-------------------------------------------
I am having trouble setting up a gnome-terminal to a specific profile.  For example, when I open up R-cran I want the title to be 'R-cran'. And when I run Octave I would like the title to be 'Octave'. Pretty straight forward, so I thawt.

So...I have been trying to set up and run different profiles for the different terminal windows that I want.  I have set up 2 new profiles, 1) for R-cran 2) for Octave, each with their own titles. 

I have tried 
1)adding the > gnome-terminal --geometry 71x30-0-25 --windows-with-profile=octave -e /usr/bin/octave-3.2.3
gnome-terminal --geometry 66x30-0-25 --windows-with-profile=R -e Rto the command line and point them to their own profile.  

2)I have also put those commands in the profile preferences hoping that it will run that way.
But neither R-cran or Octave profiles come up only the **default** one.
Any ideas??

---

### Post by AlphaLexman on 2010-10-21
According to the 'man page' you should change:
> gnome-terminal --geometry 71x30-0-25 --windows-with-profile=octave -e /usr/bin/octave-3.2.3
gnome-terminal --geometry 66x30-0-25 --windows-with-profile=R -e R                      to
```
gnome-terminal --geometry=71x30-0-25 --window-with-profile=octave -e /usr/bin/octave-3.2.3
gnome-terminal --geometry=66x30-0-25 --window-with-profile=R -e R                      
```Note the equal sign after '--geometry' and '--window' instead of '--windows'

---

### Post by oaxacamatt1 on 2010-10-22
Hi A,
Thank you very much.  I could not make heads not tails out of the man page, when I looked at it.  I guess I was too tired...  I think that did though.
Thanks again,
M

---

