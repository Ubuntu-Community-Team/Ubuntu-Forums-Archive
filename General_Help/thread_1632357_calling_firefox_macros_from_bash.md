---
title: "calling firefox macros from bash"
date: 2010-11-27
forum: General Help
---

### Post by conradin on 2010-11-27
Hi All,
I would like to call some firefox macros from bash so that I can manipulate them in some scripts. Does anyone know how to do that?
Currently I'm using the imacros firefox add-in

---

### Post by conradin on 2010-11-28
For my purposes I have this issue solved.
While I haven't figured out how to load the macro directly, 
I made a bookmark to the macro so that I could navigate to it. 
Then in bash I used the command firefox <URL_TO_Macro>

if I wanted to call multiple macros Im not sure how that would work, but for now I'm all set. I hope this can help someone else in the future!

What I'm doing is logging into a website, every 4 hours, authentication lasts 20 minutes without interaction. where I could interact via firefox after that if I'm around. else cron will run the script again, and I'll use it later.

---

### Post by Calangao on 2012-01-05
I spent some time trying to solve something similar, to get me a news clipping every day at 6 am, but I couldn't get my macro to run if I had no Firefox and terminal windows open. Using the command line to use Firefox to open iMacros directly didn't work for me. Here is how I got it done.

myBashFile.sh
```

#!/bin/bash
export DISPLAY=:0
xhost localhost
xdg-open 'http://www.google.com'
sleep 5
xdg-open 'http://run.imacros.net/?m=MY_MACRO'
```

Then I set up the crontab:

```
0 6 * * * /fullPathTo/myBashFile.sh
```

You must have have Firefox as your default browser for the xdg-open command open your macro on Firefox. I suppose you can call multiple macros this way if you set up Firefox to open links in new windows instead of new tabs as default.

---

