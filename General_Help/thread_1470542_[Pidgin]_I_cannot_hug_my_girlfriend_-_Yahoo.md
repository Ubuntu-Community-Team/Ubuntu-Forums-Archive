---
title: "[Pidgin] I cannot hug my girlfriend - Yahoo"
date: 2010-05-02
forum: General Help
---

### Post by guren on 2010-05-02
Hi all, as most of you may know, the hug emoticon for Yahoo is >:D<

Sadly, the "<" character is preventing me from sending messages containing <.

Sending the message as &gt;:D&lt; seems to work great on my end as pidgin translates this to >:D<

However, on my girlfriend's end, it is displayed as &gt;:D&lt;
She is using yahoo messenger


This problem started since I upgraded to 10.04.
Help! i still need the Human love.. :D

Does anyone know a solution for this? Thanks!!

---

### Post by guren on 2010-05-03
Solved it!

I edited the theme file for the smileys

$HOME/.purple/smileys/Yahoo/theme
then entered both of these lines
```

big_hug.gif                     &gt;:D&lt;
big_hug.gif                     >:D<

```

It only shows one hug in my Smiley set, but it works for both receiving and sending the hug! :popcorn:

---

