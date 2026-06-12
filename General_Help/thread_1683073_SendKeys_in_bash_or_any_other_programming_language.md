---
title: "SendKeys in bash or any other programming language"
date: 2011-02-07
forum: General Help
---

### Post by Miyavix3 on 2011-02-07
I'm making a bash script and I have it all complete except for one thing.

I need to take a string and some key events like {ESC} and {ENTER}, and send them to a different window, that already has focus, as if I were typing them (but automated). On windows I would normally use SendKeys for python or C# (since I just learned it yesterday). Now I'm an OK programmer, so if this is an easy feature in another programming language, I can probably fumble around with it until I get it working. 

So I was wondering, is there's a language where I can make a key presser fairly simply?

I've looked around and I couldn't find anything for bash but if you know something I don't, please tell me about it. I would love to have this all in one language so it feels less sloppy.

---

### Post by Miyavix3 on 2011-02-08
Solved

For key-pressing automation, install a package called xautomation.

In that package is a util called xte.

usage:
xte "str this will be a message sent to a window in focus" "key Return"

---

