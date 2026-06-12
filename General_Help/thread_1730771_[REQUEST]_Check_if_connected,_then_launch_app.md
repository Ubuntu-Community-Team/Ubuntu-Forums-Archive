---
title: "[REQUEST] Check if connected, then launch app"
date: 2011-04-16
forum: General Help
---

### Post by D0nJ0seph on 2011-04-16
[FONT=Comic Sans MS]Hello everybody!

Well, i have some applications that i use everyday so i add them to the startup applications, but they require Internet, otherwise the configuration is lost. I'll like a command that first check if i'm connected to Internet and if i am, launch the app. If not, don't do nothing. 


This is a problem because for some reason everytime i turn on my laptop the wireless adapter doesn't turn on automatically (it always did when i was running windows). This is not THAT annoying but if any of you know a solution for this please let me know.

THANKS FOR TAKING YOUR TIME TO READ THIS POST! And 1,000,000 thanks if you post in it!
[/FONT]

---

### Post by kseise on 2011-04-17
Number 1 - Right click on your wireless icon.  Click on edit settings and set it up so that your wireless connection (broadband card or whatever) is available to All Users.  That should hopefully set it to start with the computer and be up and running when you sign in.  Some cards act weird though.  My Verizon aircard gets mounted as a disk drive and won't connect until I unmount it.  

Number 2 - If you want to autostart the applications, consider a shell script that would do the following
[LIST=1]
[*]Wait for internet connection
[*]Launch your app
[*]Do this on every login
[/LIST]

In order to do that, I would recommend a script like this.  (please somebody smarter verify that I am doing this correctly)

```
#!bash
sleep 60 & appname

```

save that file as a script.  I recommend to save it in /home/username/bin or as a hidden file in your home directory.  Either way, when it is saved, chmod +x yourfile.

Then go under start up programs and add yourfile to the list of programs to start up.

If you want to prevent a program from launching without a connection, than I don't know.

---

### Post by D0nJ0seph on 2011-04-17
THANKS KSEISE!
   I never thought in adding a script before... thanks.
   And about the wireless, set it as available for all users did connect but not on startup, it took like 30 seconds but i'm happy with that.

THANKS AGAIN

---

### Post by kseise on 2011-04-17
My pleasure.  Happy to help.  If the network is taking 30 seconds, set the sleep number to 90 in my little script.  That is not the ideal solution, but as long as it works, who cares!

---

### Post by D0nJ0seph on 2011-04-17
After your suggestion to use a bash script, i looked for someting like that and get with this page [http://forums.techarena.in/operating-systems/1295863.htm](http://forums.techarena.in/operating-systems/1295863.htm) using some commands i allready know i came up with this script

> #!/bin/bash

sleep 60

WGET="/usr/bin/wget"

$WGET -q [http://www.google.com](http://www.google.com) -O /tmp/index.google &> /dev/null
if [ ! -s /tmp/index.google ];then
gnome-terminal --execute "/home/donjoseph/Documents/Software/Startup config/No internet.sh"
else
/opt/TweetDeck/bin/TweetDeck & emesene & skype
exit
fi
This will wait for my wireless connection to get stablished and then open my applications.

And the bash script named "no internet" is like this

> #!/bin/bash

whiptail --title "Internet status" --msgbox "Please connect to internet and run your apps manually." 8 78
So if i don't have internet, it will display a msg telling me to turn on the wireless.



I JUST TEST BOTH AND WORK PERFECTLY!:popcorn:

---

