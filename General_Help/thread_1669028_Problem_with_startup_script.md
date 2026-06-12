---
title: "Problem with startup script"
date: 2011-01-17
forum: General Help
---

### Post by jahau on 2011-01-17
I seem to have a problem with running a startup-script remapping my keyboard.

I can run the script manually, where it works fine. But when i add it to the start-up services (System - Preferences - Startup applications), it doesn't run properly - it appears that some of the script is run correctly, but not all of it.

Specifically the script moves around on my right shift and some of the arrow-keys like in this wiki: [http://wiki.eeeuser.com/howto:moveshiftkey](http://wiki.eeeuser.com/howto:moveshiftkey)

Previously I've run 10.04 where I as far as I remember had put the script itself into a folder, where it loaded upon login, but I can't seem to find it anywhere after upgrading to 10.10 with a clean install.

Hope you can help.

Best regards

Jacob

---

### Post by lmarmisa on 2011-01-17
Could you post the contents of your startup-script and the command you have added to the Startup Applications?.

---

### Post by jahau on 2011-01-17
Sure:

#!/bin/sh
# set up keyboard to exchange the Shift and Up keys, and the Down and Right keys
xmodmap -e "keycode 62 = Up" # Shift => Up
xmodmap -e "keycode 105 = Prior" # Shift-shift => PgUp
xmodmap -e "keycode 111 = Shift_R" # Up => Shift
xmodmap -e "keycode 112 = Control_R" # PgUp => Shift-shift
xmodmap -e "keycode 116 = Right" # Down => Right
xmodmap -e "keycode 117 = End" # PgDn => End
xmodmap -e "keycode 114 = Down" # Right => Down
xmodmap -e "keycode 115 = Next" # End => PgDn
xmodmap -e "add shift = Shift_R" # Make the new Shift key actually do shifting
xset r 62 # Make the new Up key autorepeat
xset r 105 # Make the new PgUp autorepeat
xset -r 111 # Prevent the new Shift key from autorepeating
# echo "All Done setting up keyboard."

Is the script I'm trying to run. The commands in running the script upon startup is simply using the build-in startup applications in ubuntu, where i set it to run: ~/.scripts/keyboard-remapping.sh (I've ofcourse made the file executable with chmod +x)

---

### Post by lmarmisa on 2011-01-17
I propose two changes:

1) Substitute /bin/sh with /bin/bash in the startup script:

```

#!/bin/bash
...

```

2) Try to use the full path for calling your script: /home/your_user/.scripts/keyboard-remapping.sh

---

### Post by jahau on 2011-01-17
no luck with the changes... the script moves some of the keys around correctly, but not all unless i run it manually...

the problems in specific is with the new placing of the r-shift key, which doesn't work at all. the new up key does move up, and when i hold it functions as r-shift. down and left keys both work like they should.

what really confuses me is, that when i run the script manually it works, but when running in startup it only works partly...

-Hauge

---

### Post by lithopsian on 2011-01-17
Something else may be configuring your keyboard after you run that script at boot.  Kick it off in the background with a 60 second delay and see if the changes take.

---

### Post by jahau on 2011-01-17
well - that "sort of" solved the problem... the keys now work, except that when i hold the new up key, it still functions as a r-shift and not a repeating up...

i hadn't considered that there might be some other process that was configuring my keyboard before my script... now comes the question of what..? i'd rather like to not use the unelegant soloution of using the sleep command to make the script work, altough i can live with it...

-H

---

### Post by lithopsian on 2011-01-17
"What" is simple.  X :)  And quite possibly your desktop manager as well.  We tend to ignore all these little thinks that just work, but X puts quite a lot of effort into messing with your keyboard and it can still be working on it when we think we have "booted".

---

### Post by jahau on 2011-01-17
yeah - that pesky X ;) i just still don't get, why it worked in 10.04 and now doesn't work in 10.10... also the small issue of the up key not repeating but retains it's old shift behavour...

---

### Post by jahau on 2011-01-18
The script still doesn't run properly - now it seems that even though it still runs with 'wait 60' the keys are just as unwilling to change...

Any further tips would be greatly appreciated...

---

