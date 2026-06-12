---
title: "Cron Help"
date: 2011-07-11
forum: General Help
---

### Post by Crunchie69 on 2011-07-11
HI I'm trying to get cron to run a bash script every 15 minutes to change my desktop background

running crontab -e I added
```
*/15 * * * * sh /home/ME/Documents/scripts/background.sh
```(at first i didnt have the sh before the path of the script but read somewhere i needed that)

But it doesnt seem to be running

my script works fine if ran straight from the terminal so Dont think thats the problem.

first time trying to use cron so super noob.

Thanks.

---

### Post by Toz on 2011-07-11
Cron is not aware of the display (desktop). Try it with:
```
*/15 * * * * DISPLAY=:0.0 sh /home/ME/Documents/scripts/background.sh
```

---

### Post by Crunchie69 on 2011-07-11
Hi thanks for the help, Tried that but still not working. 
I'm using ubuntu 11.04 if that helps.

---

### Post by Toz on 2011-07-11
How about ```
*/15 * * * * DISPLAY=:0 /bin/sh /home/ME/Documents/scripts/background.sh
```

How does your file change the background? What method are you using?

EDIT: If that doesn't work, have a look at: [http://ubuntuforums.org/showpost.php?p=5996758&postcount=12]("http://ubuntuforums.org/showpost.php?p=5996758&postcount=12")

---

### Post by Crunchie69 on 2011-07-11
hmmm nope

my script

```
#!/bin/sh

# Script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/home/sam/Pictures/backgrounds"

# Command to Select a random jpg file from directory
PIC=$(ls $DIR/*.jpg | shuf -n1)

# Command to set Background Image
gconftool -t string -s /desktop/gnome/background/picture_filename $PIC
```


also i just rebooted my computer and the background changed... but only once. (i have changed the 15 minutes to 1 minute for testing)

---

### Post by Toz on 2011-07-12
You may need to give localhost access to X. Try:
```
xhost +local:
```

---

### Post by ruffEdgz on 2011-07-12
If you look at the cron logs in /var/log/cron, I wonder if the error is shown there.

One thing I would change in your script is to put the full path of the gconftool and shuf in the script like so:
```

PIC=$(ls $DIR/*.jpg | /usr/bin/shuf -n1)

/usr/bin/gconftool -t string -s /desktop/gnome/background/picture_filename $PIC
```

Once that is done, you can use this in your crontab:
```
*/15 * * * * /home/ME/Documents/scripts/background.sh > /dev/null 2>&1
```
Since you placed the #!/bin/sh in the script and you made the file executable, you shouldn't have to call /bin/sh to run your script.

Cheers!

**NOTE** Just tried it on my end and it seems it did not work even with the full paths. Read the article that Toz posted above and found it interesting to get the randomization of your desktops to work. Going to try it myself now to see if that still works.

---

### Post by Crunchie69 on 2011-07-12
ok trying the method provided in the link..

getting stuck at > 2) Make .make_Xdbus run each time you log in by selecting System ->  Preferences -> Sessions and add /home/your_name/.make_Xdbus as a  Startup program.  To test, log out and log back in and check to be sure a  file called .Xdbus is there.any chance of some updated instuctions for this bit

thanks heaps

---

### Post by ruffEdgz on 2011-07-12
> **Crunchie69 said:**
> ok trying the method provided in the link..

getting stuck at any chance of some updated instuctions for this bit

thanks heaps

He is talking about 'Startup Applications' if you are using 11.04.

---

### Post by Crunchie69 on 2011-07-12
OK so I'm not getting the .Xdbus file created.. any ideas?

---

### Post by ruffEdgz on 2011-07-12
Ok, found a solution to this that isn't as complicated. Found this at this url provided but made small changes to it ([URL Here](http://stackoverflow.com/questions/2182468/run-cronjob-as-user-to-change-desktop-background-in-ubuntu)):
```

#!/bin/bash

# Script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/home/sam/Pictures/backgrounds"

# Command to Select a random jpg file from directory
PIC=$(ls $DIR/*.jpg | /usr/bin/shuf -n1)

if [ -z "$DBUS_SESSION_BUS_ADDRESS" ]; then
        TMP=~/.dbus/session-bus
        export $(grep -h DBUS_SESSION_BUS_ADDRESS= $TMP/$(ls $TMP | head -n 1))
fi

 #Command to set Background Image
/usr/bin/gconftool-2 -t string -s /desktop/gnome/background/picture_filename $PIC

```
The reason for this is a cronjob does use a users ENV variables when executing and since gconftool/gconftool-2 need the variable DBUS_SESSION_BUS_ADDRESS, it doesn't work. The if statement will see if that variable is there and if not, it will set it by looking in the users directory under .dbus/session-bus.

Works for me as we speak, hope it works for you.

---

### Post by Crunchie69 on 2011-07-12
YES thank you so much! working perfectly

Cheers

---

