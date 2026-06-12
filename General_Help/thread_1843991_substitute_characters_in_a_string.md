---
title: "substitute characters in a string"
date: 2011-09-14
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2011-09-14
A lot of time with google and man sed and so far the farthest I've gotten is the vague suspicion that I can do what I want with sed if I can figure it out. I'd appreciate if someone can either confirm that sed is the right tree to bark up or point me in another direction.

What I want is simple:

A command that will take a string as input and output a string wherein all the characters that can cause problems as part of filenames are changed into something that won't. Basically a Caesarean code transformation on select characters. For instance, change spaces to underscores, non leading slashes to hyphens, leading slashes or hyphens to (-), back slashes to (bs), ? to (q), * to (star), etc., resutling in a string suitable for a plain vanilla file name acceptable in any file system under any OS provided its not too long.

Surely this need must have arisen thousands of times and this wheel must already be invented, probably as an internal bash command. Anybody care to give me at least a hint where to look if not a finished script? I'm not wedded to bash, btw, if I should invoke some other shell to do this easily. I'm still in shock from learning Bash sneers at "goto" so I'm open to alternatives.

---

### Post by dethorpe on 2011-09-14
Can do it in sed, but check out "tr", should do what you need and be easier.

---

### Post by Dreamer Fithp Apprentice on 2011-09-14
Thanks, Dethorpe. Yes, indeed, tr looks much more like the ticket.

---

### Post by Dreamer Fithp Apprentice on 2011-09-14
Odd, Firefox 6 bleeding edge won't let me mark this solved. I'll come back in FF 3.6.

---

### Post by Dreamer Fithp Apprentice on 2011-09-14
Yep, worked ok with 3.6.

---

