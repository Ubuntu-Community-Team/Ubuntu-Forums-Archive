---
title: "How to prevent Sleep during processing?"
date: 2011-06-19
forum: General Help
---

### Post by KonfuseKitty on 2011-06-19
If I set my Ubuntu 10.10 to sleep after an hour of inactivity, I can't leave Blender to render overnight. The processing that Blender is doing seems to be ignored, and the computer goes to sleep after an hour. How can I prevent this from happening? I don't want to set Sleep to Never, I would like the computer to sleep after Blender is done.

---

### Post by KonfuseKitty on 2011-06-20
Bump.

---

### Post by raja.genupula on 2011-06-20
i think in screen saver settings we have that option , just check it out once .

---

### Post by smithk on 2011-06-20
Yeah maybe the screen  saver..

Just set it to sleep mode..

---

### Post by redmk2 on 2011-06-20
> **KonfuseKitty said:**
> If I set my Ubuntu 10.10 to sleep after an hour of inactivity, I can't leave Blender to render overnight. The processing that Blender is doing seems to be ignored, and the computer goes to sleep after an hour. How can I prevent this from happening? I don't want to set Sleep to Never, I would like the computer to sleep after Blender is done.

Set the power management to never allow sleep mode.  

Go to System>>Preferences>>Power Management and select **Never** to the question "*Put Computer to sleep when inactive for:*"

I was watching a movie when that system went to sleep on me.  I changed the setting I just described and all was fine after that.  Remember you can re-configure when you are done with your project if you want to.

---

### Post by KonfuseKitty on 2011-06-20
Thanks, but I'd prefer not to set it to Never as I'd like the computer to sleep once it's done. Important if I leave it and go away for the day (as well as overnight). I was hoping there was maybe a more low level solution I could apply through the command line interface. Isn't there some way of controlling what "inactivity" means?

---

### Post by danjjl on 2011-06-20
Hello,
if I where you I would write a small script to do the job. It would look somthing like this :
```

#!/bin/sh  
sudo -u yourusername your_command
halt

```then launch it using 

```
sudo /path/yourscript.sh
```You will find information on the command to insert instead of your_command here :
[http://wiki.blender.org/index.php/Doc:Manual/Render/Command_Line_Options](http://wiki.blender.org/index.php/Doc:Manual/Render/Command_Line_Options)

Good luck

---

### Post by mike555 on 2011-06-20
I installed "caffeine " and set it to auto start and put Firefox-bin in settings , so my computer doesn't sleep while Firefox is running (good for watching Hulu ) , but you should be able to put almost any program in Caffeine's settings .....

---

