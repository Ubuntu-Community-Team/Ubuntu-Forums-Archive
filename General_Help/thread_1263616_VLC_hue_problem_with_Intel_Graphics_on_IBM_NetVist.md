---
title: "VLC hue problem with Intel Graphics on IBM NetVista"
date: 2009-09-11
forum: General Help
---

### Post by Nyken on 2009-09-11
Hello again.

Said in other posts how I like to post tips that specifically applies to a situation that I was in, in hopes it helps another like me looking for a solution to this problem. This particular one was colour values being reversed (blue skin, etc.) with VLC, using Intel graphics. Found a lot of posts for other set ups, but none worked for me, so I had to just back to experimenting on my own.

This was the solution: the settings for this particular computer running Ubuntu 9.04 should be thus:

Tools > Preferences > Video >

Chose for this particular application, XVideo Extension Video Support. This setting doesn't work for me at all with other videos apps, but it strangely works like a champ with VLC, and it fixes my color hue problem completely. MPlayer doesn't give me this problem, but I prefer to play DVDs with VLC. 

Hope you find this to be your solution as well.

---

### Post by Nyken on 2009-10-15
Solved.

---

