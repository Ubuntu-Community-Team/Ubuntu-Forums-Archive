---
title: "any shell or hack that makes the shell command line take vi commands?"
date: 2012-05-30
forum: General Help
---

### Post by marqul on 2012-05-30
basically i'm tired of hitting the left arrow a few dozen times when correcting a mistake or modifying a history command

i'd like to use vim style key shortcuts while on the command line so that a 55[left arrow key] moves the cursor 55 places to the left...

and i want all the other vi goodies, search of history maybe - a dream?, replace, etc

---

### Post by ratcheer on 2012-05-30
Just enter "set -o vi" and you will have it. I keep it in my profiles so it is always ready. To get command history, Esc-k. Can be repeated as long as the history goes back. If you go back too far, Esc-j moves you forward.

Sometimes it helps to have an old UNIX geek around.

Tim

---

