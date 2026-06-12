---
title: "Please explain this tutorial"
date: 2009-11-08
forum: General Help
---

### Post by Shmalignant on 2009-11-08
Can someone please explain what every step of this tutorial is doing in layman's terms.  Your help is greatly appreciated.

1) Open a terminal (Applications->Accessories->Terminal)
2) Run the following command: mkdir ~/bin
3) cd ~/bin
4) gedit volume-adjust.sh
5) copy the following information into gedit:

#!/bin/sh

. /lib/lsb/init-functions
AMIXER="/usr/bin/amixer"
VOLUME="50%"
test -x $AMIXER || exit 1

case $1 in

    start)
        log_daemon_msg "Adjusting Volume" "volume-adjust"
        $AMIXER -c 0 sset Master,0 $VOLUME > /dev/null
        log_end_msg $?
        ;;

      *)
        log_success_msg "Usage: /etc/init.d/volume-adjust start"
        exit 1
        ;;
esac

exit 0

6) Save the file and close gedit.
7) Run the following command in the terminal: chmod +x volume-adjust.sh
8) Run the following command in the terminal: ./volume-adjust.sh start
9) Ensure that running the script adjusts the volume and that no errors are echoed to the terminal.

If it does, it is then just necessary to put this script into your startup process. If it doesn't post back here and we can see if we can find a different solution. To put the script in your startup process do the following:

10) Open a terminal.
11) sudo cp ~/bin/volume-adjust.sh /etc/init.d/volume-adjust
12) sudo update-rc.d volume-adjust start 99 2 3 4 5 .

This should put the script into your startup process. It may output some error information about the script not having lsb information. Don't worry about that. You could alternatively put that in one of your session startup programs, but that wouldn't affect the volume of the sound when the login screen is ready.

---

### Post by kaivalagi on 2009-11-08
The script file looks like it restores volume to 50% when run. The steps are to set it up, test it and then add it into your existing daemons (services) so it is run on boot before login.

Your system volume should be fine without this though...

---

### Post by Shmalignant on 2009-11-08
Ok, I got it...

This makes a directory in your home directory called bin.  Then it opens up gedit where you paste the script and save.  Then, step number 7 gives permission to execute to all.  Step 8 runs the script.  I omit steps 10-12 and just add volume-adjust.sh to start up programs.  

So, in conclusion, I already knew this was a script to automatically lower the volume at login.  What I didn't know (but I know now) is what is written above.  

I have this script set to run at start-up on my laptop.  It is helpful because most of the time I forget to turn down my volume upon logout.  When I login (which is usually in class) I don't have to worry about the intro sound blasting from my speakers.  

I don't take credit for this script.  Here is my reference: [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/70666](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/70666)

---

