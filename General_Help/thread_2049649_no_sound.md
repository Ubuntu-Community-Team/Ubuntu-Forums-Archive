---
title: "no sound"
date: 2012-08-29
forum: General Help
---

### Post by kadaj6 on 2012-08-29
no sound on xps laptop
I know there are a lot of topics on this but, i have read a lot of them and tried a lot of the solutions i have found and none have worked. i have an xps laptop. all i want is the sound to work. how can i make this possible? If you need me to post my hardware info telll me how to find it and ill post it.

Thank you!

---

### Post by qQChtIhpk1 on 2012-09-04
Try 'System/Preferences/Startup Applications' and make sure 'PulseAudio Sound System' is checked.

Early in August a change was made to U 10.04 (and possibly other releases), Requiring that this application be running for sound to work.  Previously this application was not required.

Peace & Happiness,

Chazbo  :D

---

### Post by Costas100 on 2012-09-04
I had frequent sound misses. In many cases it was resolved by opening a terminal then type alsamixer and check that no MM exist in any of the coloured bars (at the bottom) if it is then this means that this function is muted (it happens to me frequently. using the keyboard arrows, go to the bar with MM and press the M key on your keyboard. Then make sure you have at least 4 preferably 5 green small bars on each set and enough white small bars. At the top you may have one or max 2 red small bars. Play around and find what is best for you. To increase or decrease the green white and red small bars use the up and down arrows from the keyboard. You may get a static sound as you add more small coloured bars from your speaker. In this case reduce the red or white bars. If you find a good tutorial for Alsamixed, please post the link.

Good luck to you

Costas

---

