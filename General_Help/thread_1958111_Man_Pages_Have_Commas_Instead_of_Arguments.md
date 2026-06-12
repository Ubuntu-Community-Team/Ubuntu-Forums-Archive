---
title: "Man Pages Have Commas Instead of Arguments"
date: 2012-04-13
forum: General Help
---

### Post by vectris on 2012-04-13
To elaborate on the title, when I literally type in "man <something>" I will see the man page just like everything is normal, except where it should be telling me "-a doesthiskindofstuff -execute canbeusedto" I have commas instead of all the "-<character>".

Effectively, I don't know what any of the arguments are because the man pages display them all as commas rather than the appropriate "-<character>".

For instance I know -a on ls shows hidden files. But "man ls" brings up the man page and -a as well as all the other arguments are just commas. I've been running Ubutunu 12.04 for the past 2 months and never had a problem with this until now. The only recent change I've made was installing openssh-server but I doubt that had anything to do with it.

How can I get my man pages back to normal as I really need to be able to see what arguments different commands have?

EDIT: Haha well I figured it out. I had set a custom color scheme where my background is black and foreground is white. What I didn't know was that my Bold was also set to Black and in the man pages all the arguments are bold so they disappeared into the background. I've had this color scheme for a while so I don't know why I haven't been noticing more missing things but glad to know that was it.

---

