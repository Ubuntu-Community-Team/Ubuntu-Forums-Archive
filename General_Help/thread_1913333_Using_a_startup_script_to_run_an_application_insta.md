---
title: "Using a startup script to run an application installed in the opt folder..."
date: 2012-01-22
forum: General Help
---

### Post by MacTribe on 2012-01-22
Hi There

I'm a Mac user who dabbles in a bit of the awesome ubuntu, I'm not a complete noob but I'm no expert! I've followed some really great steps on installing the airvideo server on my ubuntu 10.04 box at home. It all works nicely however I'm a little confused over the /opt folder - and not just for this application but in general when it comes to any application I would like to run from boot.

The issue I'm having is when I run a script from /etc/init.d it wont work on boot. If I move the application to my home folder e.g move /opt/airvideo-server to /home/media and change the script to reflect the path, then it works. Obviously there is a permissions issue. 

If you want to know what steps I've taken so far (copied from the website instructions I'm following) see below:

[B]Fire up a terminal and enter

sudo [text editor of choice] /etc/init.d/airvideo-server
In the file (which should be blank), paste the following:

#!/bin/bash
case "$1" in
  start)
    echo "Starting AirVideo"
    start-stop-daemon --start --quiet -b -m -p /var/run/airvideo-server.pid --chuid airvideo --exec /usr/bin/java -- -jar /opt/airvideo-server/AirVideoServerLinux.jar /opt/airvideo-server/AirVideoServerLinux.properties
  ;;
  stop)
    echo "Stopping AirVideo"
    start-stop-daemon --stop --quiet --pidfile /var/run/airvideo-server.pid
    rm -f /var/run/airvideo-server
  ;;
  *)
    echo "Usage: /etc/init.d/airvideo-server {start|stop}"
    exit 1
  ;;
esac
exit 0
Save the file out, then create the user which is going to be used to run the file. You should also double check to make sure that /opt/airvideo is readable by this account.

sudo adduser airvideo
Make the file executable, then add it to the startup defaults.

sudo chmod +x /etc/init.d/airvideo-server
sudo update-rc.d airvideo-server defaults
When you next reboot your system, airvideo should start automatically.[/B]

I've added the user 'airvideo' to my list of users as instructed, but what permissions need to be in place for:

1) the user? 
2) /opt folder itself?
3) /opt/airvideo-server folder?
4) who needs to own the folder? or folders? 
5) what else would be needed for the script to work?

This problem / solution would also help me with my teamspeak server setup which also only works outside of the /opt folder with a simple startup script. 

I appreciate any input and help! Thanks!

---

### Post by partloer on 2012-01-22
I don't know for sure if this will work but what I have done is create the bash file in a local folder (ie /home/smith/bash/script1.sh) then in the file /etc/rc.local call that file (ie sh /home/smith/bash/script1.sh).  This should run the script upon start up right after the end of boot processes also this can be ran as sudo.

---

### Post by MacTribe on 2012-01-24
Thanks for your suggestion. The only issue with this method is it will be dependent on a script in a home folder, which I'd prefer to avoid encase I make any changes or remove any of the home folders later on. 

Is there no other solution that would work within the /etc/init.d folder and /opt folder?

---

### Post by User 04 on 2012-05-15
A very simple way is to install your script in /usr/bin or /usr/local/bin.

Then access  Startup Applications and link to your script.  Script will then be enabled at startup.

---

