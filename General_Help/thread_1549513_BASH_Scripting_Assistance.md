---
title: "BASH Scripting Assistance"
date: 2010-08-09
forum: General Help
---

### Post by justinmiller87 on 2010-08-09
I have the following code
```

#!/bin/bash
COUNT=1
# bash until loop
until [$COUNT -gt 2]; do
pq A$COUNT\ [Pemptus].pq &
let COUNT=COUNT+1
done

```
in a bash script. I did this because I'm that much of a Progress Quest geek that I wanted to have a huge group on the online server, so I decided to make a script that would open all the files for me rather than having me do it manually.

I created some characters with the boring name of A1, A2, etc. When I ran the above script, it went into a continuous loop and I had to halt it, then run [FONT="Courier New"]sudo killall pq.exe[/FONT] to eliminate the 500 or so Progress Quest windows that popped open. Anyway, what is wrong with my script that I can't seem to get it to stop loading files at an arbitrary number? I want to get this part finished before I make any more boring named characters.

Thanks much.

---

### Post by amauk on 2010-08-09
I know nothing about Progress Quest, btw

You need spaces around the [ & ] in the script
```
#!/bin/bash
COUNT=1
# bash until loop
until [ $COUNT -gt 2 ]; do
pq A$COUNT\ [Pemptus].pq &
let COUNT=COUNT+1
done
```

I personally would use a while loop, though
(personal preference, but IMO it's logically "better" - you want to loop only while a condition is true, not loop indefinitely until a condition is false)

Also (again, probably personal preference, but) I tend to prefer incrementing stuff using expr

```
#!/bin/bash
COUNT=1
# bash until loop
while [ $COUNT -le 2 ]; do
pq A$COUNT\ [Pemptus].pq &
COUNT=$(expr "$COUNT" + 1)
done
```

---

