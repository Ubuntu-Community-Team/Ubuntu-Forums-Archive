---
title: "Allow only one instance of a start-up script after log-in - log-out."
date: 2010-05-03
forum: General Help
---

### Post by Randypan on 2010-05-03
Hello,

I have recently found a bash script that keeps my external HD from spinning down every now and then. I included it in /etc/init.d and update-rc.d'ed it so that it would run uppon every login.
Now, this works abolutely fine after rebooting or shuting down BUT if  I just log out and then log in as the same or a different user the script runs once more. If I check my running processes, I find two scripts with the same name and different IDs running.
... If i log out and back in once more there's three of them.
Of course this is no serious matter (I can manually end the excess process without any trouble) but it's kind of annoying.

How can I make the script run once and only once after the computer has been powered-up?

---

### Post by Randypan on 2010-05-13
Anybody?

---

### Post by dai_trying on 2010-05-13
I'm no expert, but could you run a logout script to stop it?

---

### Post by Randypan on 2010-05-13
I wanted to know if there is a way for a script to automatically prevent itself running more than once every time I log in, so that I won't have to end the excess instances of it manually. The script itself contains just the commands needed by it to perform its task. Are there any additional commands I have to add to the .sh File to make it run once after every log-in or any other configuration to be done?

---

### Post by dai_trying on 2010-05-19
I'm guessing you would need to put a command to check if the process is running first in the script and then not run again if it already is, but I do not know how to code it... sorry
Anybody?

---

### Post by Randypan on 2010-05-20
No problem. Thanks anyway

---

### Post by Randypan on 2010-05-22
So, any ideas? Anybody?...

---

### Post by gmargo on 2010-05-22
> **Randypan said:**
> How can I make the script run once and only once after the computer has been powered-up?

You are starting a script at boot time, and also at login time?  Choose one or the other.

If you want "once and only once" then run it at boot time only.

---

### Post by Randypan on 2010-05-25
Sorry for the confusion, I made a mistake in my first post. I didn't include the script in init.d, I just put it in the start-up programs from Menu>System. _Many apps are included there by default, like Indicator Applet or nmapplet and I don't get them in twos or threes everytime I log out and back in. What's the case with that script?_ Anyway, a while ago I removed the entry from Startup Programs, created a symbolic link of it in /etc/init.d and ran sudo update-rc.d keepactive.sh defaults (keepactive is the name of the script). When I rebooted, the system hanged badly after the ubuntu logo appeared. It just showed a black screen listing the programs that were loaded up to that point. I couldn't go past that screen, even after booting from the live CD and some hard reboots. I got everything fixed by restoring my whole /etc directory from a recent backup but that also took me back to where I started with the script. The script that's causing me all the trouble is this:
-------------------------------------------------------------------------------------------------------
 #!/bin/bash
 
while [ true ]
do
    touch /media/sdb2/.keepactive
    sleep 10s
done
-------------------------------------------------------------------------------------------------------
It's instructed to run a touch command on an empty file in my external drive every 10s to keep it from spinning down._ How could that script cause all that fuss when it was told to run at boot-time?_
_I just wanted to make that stupid script run on the first login. What can I do to make it work?_

---

