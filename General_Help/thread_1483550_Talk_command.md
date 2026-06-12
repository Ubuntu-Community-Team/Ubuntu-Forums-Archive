---
title: "Talk command?"
date: 2010-05-14
forum: General Help
---

### Post by mghis on 2010-05-14
Hello to all! I'm a new ubuntu user, and i use the 9.10 Karmic Koala version.
Just a question: where is the talk command? It is'nt installed with the system. I tried with 'sudo apt-get install talk talkd'. When i try 'talk user /dev/pts/1' it says 'No connection yet' an then 'Checking for invitation on caller's machine'. Nothing apparese on pts/1.
How can i get talk working?

It may be a dumb question but i'm a newbie...

Thanks for any answer!! :)

---

### Post by mghis on 2010-05-31
No one? :(

If you need more informations about my problem... ask me!
I did not solved that!

**Thanks in advance for any reply!** :)

---

### Post by gmargo on 2010-05-31
> **mghis said:**
> When i try 'talk user /dev/pts/1' it says 'No connection yet' an then 'Checking for invitation on caller's machine'. Nothing apparese on pts/1.
How can i get talk working?

The correct syntax is "talk user pts/1"; you must leave out the "/dev/" part.

---

