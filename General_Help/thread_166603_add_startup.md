---
title: "add startup"
date: 2006-04-26
forum: General Help
---

### Post by RevengerPT on 2006-04-26
Hi there. I'm trying to run some programs at startup. I already tryed out to put them on that menu at System > Preferences > Sessions > Startup Options but it didn't worked. As a matter of fact, I thing what I really need is some sort of script to launch this two apps followed by their arguments:

1) ~/TeamSpeak/tss2_rc2/teamspeak2-server_startscrip start
2) x11vnc -passwdfile ~/x11vnc/passwd

I really need this because I have two PC's but only one screen, mouse and keyboad. Can anyone help?

Thanks a lot. :p

---

### Post by RevengerPT on 2006-04-26
bump

---

### Post by RevengerPT on 2006-04-26
:(

---

### Post by cosmoshell on 2006-04-26
I as well need to be abled to do something like that.

---

### Post by nanotube on 2006-04-26
so when you put them into System > Preferences > Sessions > Startup Programs, it did not do anything at all? in that case, first thing i would try is give the full path to the executable, and see if that helps. 

ie, put in
```
/home/yourusername/TeamSpeak/tss2_rc2/teamspeak2-server_startscript start
/usr/bin/x11vnc -passwdfile /home/yourusername/.x11vnc/passwd
```

---

### Post by ZylGadis on 2006-04-27
You could certainly write a script, put it in /etc/init.d/ and go the usual route from there. I guess that is the appropriate thing for you, having in mind that you actually want to start services.

---

### Post by nanotube on 2006-04-27
[QUOTE=ZylGadis]You could certainly write a script, put it in /etc/init.d/ and go the usual route from there. I guess that is the appropriate thing for you, having in mind that you actually want to start services.[/QUOTE]

but that would run these things as root, which is probably not what you want for these types of things...

---

### Post by ZylGadis on 2006-04-27
Not really. You can su to another user in the script and run the thing with that user's permissions. I have a custom init.d script for tomcat that runs it under tomcat:tomcat.

---

### Post by RevengerPT on 2006-04-27
Wow, that's something. But I don't really know how to do a script yet. How can I make one that launches those services, not as su but as gabriel (my username)?

Thanks a lot for your help. :-D

---

### Post by RevengerPT on 2006-04-27
bump

---

### Post by ZylGadis on 2006-04-27
Here is my custom tomcat script, located in /etc/init.d/tomcat

```

#! /bin/sh

export JAVA_HOME="/usr/lib/j2sdk1.5-sun"

. /lib/lsb/init-functions

case "$1" in
  start)
    log_begin_msg "Starting servlet container (Tomcat)..."
    su -c"/usr/local/apache-tomcat/bin/startup.sh" -s/bin/sh tomcat
    log_end_msg $?
    ;;
  stop)
    log_begin_msg "Stopping servlet container (Tomcat)..."
    su -c"/usr/local/apache-tomcat/bin/shutdown.sh" -s/bin/sh tomcat
    log_end_msg $?
    ;;
  force-reload|restart)
    sh $0 stop
    sh $0 start
    ;;
  *)
    exit 1
    ;;
esac

exit 0

```

I assume you know the exact commands to run the things you need, so not much trouble replacing the relevant portions of the above. JAVA_HOME is just an environment variable that tomcat requires to run properly.
Of course, in order to run something as another user, you should first create that user. The password does not matter (best set something unintelligible), because the su command from root doesn't need the user's password.
Remember that only root can listen on ports below 1024. My tomcat instance is on 8080 because of that (I'd rather use a nonstandard port than compromise security).
The commands for using the script obviously are:

sudo /etc/init.d/tomcat start
sudo /etc/init.d/tomcat stop
sudo /etc/init.d/tomcat restart

The sudo part is to test it. When booting, everything is run as root, so no sudo needed.
After you have the script in /etc/init.d/ and ensure it works, install BUM from synaptic. Then find it in System->Administration->Boot-up Manager. It should find your new script. Checkboxes there are self-explanatory. There are easier ways to do this, but all are terminal-based and you are a newbie, so BUM is your friend.
Hope that helps.

---

### Post by elamericano on 2006-04-27
That's a lot of bumping. You were expecting instant gratification?

I'd go with the sessions->Startup Programs too. If the commands require sudo, then use gksudo for the GUI launch. Just cut and paste to the terminal to verify what you've typed will work.

---

