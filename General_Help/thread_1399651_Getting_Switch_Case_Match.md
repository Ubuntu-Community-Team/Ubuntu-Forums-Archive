---
title: "Getting Switch Case Match"
date: 2010-02-05
forum: General Help
---

### Post by sharpdust on 2010-02-05
I am not a shell scripting expert, so I'm hoping somebody can help me out here. 
This may not be possible, but consider this code:

```
#!/bin/sh

string="this"
case "$string" in
  this | that)     echo "It matched " ;;
   *)   echo "Not this or that" ;;
esac
```

Is there a way to extract out from the switch case which string $string matched?
In other words, when I do the echo, I want it to say "It matched {this|that}" picking the correct one. Like does shell scripting store which one it matched in some special variable?

And yes, I understand, I can just drop it down "that" onto another line, but I'm trying to compress some code in another program of mine.

Thank you.

---

