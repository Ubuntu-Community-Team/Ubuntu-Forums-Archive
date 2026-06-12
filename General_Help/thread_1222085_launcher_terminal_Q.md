---
title: "launcher terminal Q"
date: 2009-07-24
forum: General Help
---

### Post by mCion on 2009-07-24
So I'm trying to make a shortcut in my panel to tell me my CPU temperature through lm-sensors or IE
```
sudo sensors
```

I make a Launcher and put "sudo sensors" in the command line.

I believe it runs but after it's done it closes.  Is there a command to tell it to leave the terminal open so I can look at the results?

Thanks in advance

...

and...how do you make a Forum thread title bold?. XD

---

### Post by Johnny B on 2009-07-24
#  while true ; do sensors ; sleep 2 ; done

this will update every 2 seconds

---

### Post by Johnny B on 2009-07-24
Or:
> sen=`sensors` ;  zenity --info --text="$sen"

---

### Post by mCion on 2009-07-24
if I copy either of those in the Command box in the "properties" of my launcher/shortcut I get error results.

Maybe I didn't explain well at first.


Any ideas or did I do something wrong?

---

### Post by cariboo on 2009-07-24
The thread title is bold by default.

Is there a reason why you don't want to use the sensors-applet? That way you have a constant display of whatever temperatures you want to monitor, including cpu, motherboard, and video card. IF you install hddtemp you can also monitor hard drive temps.

---

### Post by mCion on 2009-07-24
mm.  I don't know much about monitoring software.

Personally, I'd rather just check it when I want to, instead of it working in the background constantly.

---

### Post by Johnny B on 2009-07-24
> **mCion said:**
> if I copy either of those in the Command box in the "properties" of my launcher/shortcut I get error results.

Maybe I didn't explain well at first.


Any ideas or did I do something wrong?

but those will work if you save them as a script, then calll the script through the "command box"

---

### Post by CatKiller on 2009-07-24
> **mCion said:**
> how do you make a Forum thread title bold?. XD

The bold titles are threads containing posts that you haven't read yet. You've already read this one, since you wrote it...

---

### Post by mCion on 2009-07-24
created the script.

command line in the launcher

sudo chmod ....(the script)

it runs but it closes before i see results.

maybe i should start from 0.

how could i see my CPU temperature when i want it (hopefully not running all the time in the background)?

---

