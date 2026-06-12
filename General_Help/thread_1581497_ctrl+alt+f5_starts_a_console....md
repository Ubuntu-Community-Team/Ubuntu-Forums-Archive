---
title: "ctrl+alt+f5 starts a console..."
date: 2010-09-25
forum: General Help
---

### Post by Kael Seoras on 2010-09-25
...this much I figured out. I can't find, though, how to change that. In DOSBox, ctrl+alt+f5 starts and stops video capture, but Ubuntu's command took precedence when I did that. I had to hard shut down before doing some searching and finding out ctrl+alt+f7 gets me out of there...that doesn't help me with the problem of taking video on DOSBox though. I went to System>Preferences>Keyboard Shortcuts to see if I could change the command or disable it, but it wasn't listed...so I'm stuck. I don't want ctrl+alt+f5 to bring me to a console, so how do I make it not do that?

---

### Post by robsoles on 2010-09-25
from memory of DOSBox it was highly configurable - occurs to me it may  be a better idea to change the key combo in DOSBox rather than in  Ubuntu.

There is a way to do it (pretty sure I've stumbled on it somewhere or  other) but I honestly think you will do better to investigate config  options for DOSBox more.

---

### Post by Kael Seoras on 2010-09-28
If I can change the command in DOSBox, I'm not successfully figuring out how.

---

### Post by robsoles on 2010-09-29
Took me a few minutes to find it but [CTRL]+[F1] (while running DOSBox) brings up a key mapper, in the window that appears you can find 'video' in the second column, third row, of a box toward the right just below middle of the window.

click 'Video' and then click a key on the keyboard - just guessing but I think you need to use 'mod1', in bottom left hand corner, to specify [CTRL] key and mod2 to specify [ALT] key.

How's that?

---

