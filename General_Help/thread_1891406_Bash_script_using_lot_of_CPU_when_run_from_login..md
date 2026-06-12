---
title: "Bash script using lot of CPU when run from login."
date: 2011-12-05
forum: General Help
---

### Post by MrWestwood on 2011-12-05
[LEFT]Good evening.

I have made a simple bash script with the help of a youtube video which will lock my computer whenever my phone's bluetooth isn't detected. Or a bluetooth locker if you will.

block.sh

```

#!/bin/bash

while [ 1 ]
do
    x=`hcitool scan |grep -e "MAC removed"`

    clear
    if [ "$x" != "" ]
    then
        echo "Device found"
        gnome-screensaver-command -d
    else
        gnome-screensaver-command -l
    fi

done

```

There is the script. When I just run the script from terminal it does the job perfectly. The problem starts when I run the script from System>Preference>Startup Applications. Whenever I get the script to run at login via this method my CPU is nearly always maxed out. 

Is there any way to stop this? It seems to be linked to the way it is launched at login, is there another place I can put the script to launch at startup?

Many thanks

P.S. I love bash scripts. Obviously I'm a noob but these things are so cool. 
[/LEFT]

---

### Post by Slim Odds on 2011-12-05
Well, first off, this script will be running "hcitool" and "gnome-screensaver-command
 constantly. You should put some sort of a "sleep" in there so that it checks at some interval.

Also "clear" needs a terminal to work.

---

### Post by MrWestwood on 2011-12-05
> **Slim Odds said:**
> Well, first off, this script will be running "hcitool" and "gnome-screensaver-command
 constantly. You should put some sort of a "sleep" in there so that it checks at some interval.

Also "clear" needs a terminal to work.

Thanks. I did wonder if it's simply because it's running the commands over and over but I don't get the problem if I just run it from command line. I have removed clear for the launch at login script.

Any idea why it only uses so much CPU when run from login?

---

### Post by CoffeeRain on 2011-12-05
That's a great idea! While loops take a lot of power, because they run constantly.

---

### Post by CoffeeRain on 2011-12-05
Didn't realize you replied. :)

---

### Post by MrWestwood on 2011-12-05
> **CoffeeRain said:**
> That's a great idea! While loops take a lot of power, because they run constantly.

Is it a great idea? Is there a hint of sarcasm there? I'm just learning scripts so I'm always open to suggestions.

I understand the script is constantly running but when I just run it from command line it works fine. It's when I get the script to run at login via Startup Applications that my CPU usage goes crazy.

Should I be running it from elsewhere?

It was great when I was testing it. A bit disappointed that I can't have it running automatically. :(

---

### Post by MrWestwood on 2011-12-05
It appears it does use the same amount of CPU when run from a terminal. I guess it's a case of putting a pause for 5 minutes between runs. I wanted to use this on my work PC but 5 minutes can be a long time in our office.

Thanks for your help guys.

---

### Post by SlugSlug on 2011-12-08
save this as /home/user/scripts/btlock.sh


```

#!/bin/bash
    x=`hcitool scan |grep -e "MAC removed"`
    if [ "$x" != "" ]
    then
        gnome-screensaver-command -d
    else
        gnome-screensaver-command -l
    fi

```then this as /home/user/scripts/5sec.sh
```


#!/bin/bash
while true
do
bash btlock.sh
sleep 5
done

```then edit crontab to contain the line

```

@reboot /home/user/scripts/5sec.sh

```That should keep the pesky office workers out  ;)

---

