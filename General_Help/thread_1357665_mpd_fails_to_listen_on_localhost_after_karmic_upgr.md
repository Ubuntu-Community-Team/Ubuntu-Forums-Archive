---
title: "mpd fails to listen on localhost after karmic upgrade"
date: 2009-12-17
forum: General Help
---

### Post by treehouse on 2009-12-17
After my recent update to Karmic Koala, mpd is all jacked up. Everytime I try to use --create-db, I get an error. At first it was:
```

listen: Failed to listen on localhost (line 27): Address already in use
Aborted

```
ever since I added the line
```

state_file		"/home/nicholas/.mpd/state"

```
to my config files (both /etc/mpd.conf and ~/.mpdconf) it has changed to
```

listen: Failed to listen on localhost (line 37): Address already in use
Aborted

```
which is pretty much the same result. On my netstat it seems to be the only thing on its port and ip
```

nicholas@nicholas-desktop:~$ sudo netstat -tapn | grep 127.0.0.1
[sudo] password for nicholas: 
tcp        0      0 127.0.0.1:40162         0.0.0.0:*               LISTEN      2058/python     
tcp        0      0 127.0.0.1:6600          0.0.0.0:*               LISTEN      18878/mpd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1170/cupsd      
tcp        0      0 127.0.0.1:58846         0.0.0.0:*               LISTEN      2081/python     
tcp        0      0 127.0.0.1:52502         127.0.0.1:6600          ESTABLISHED 8987/conky      
tcp        0      0 127.0.0.1:6600          127.0.0.1:52502         ESTABLISHED 18878/mpd       

```

I killed cupsd just to be sure (as I own no printer), and tried again, no dice.

I run mpd as my user, and have all permissions to all log, config, music, music, and playlist folders.

I have no idea what could be wrong. Any ideas?

my config files (minus the commented out lines):
```


######################## OPTIONAL PATHS ########################
#
# If specified, MPD will save its current state (playlist,
# current song, playing/paused, etc.) at exit.  This will be
# used to restore the session the next time it is run.
#
state_file		"/home/nicholas/.mpd/state"
#
################################################################


######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            "nicholas"
#
# The address and port to listen on.
#
bind_to_address                 "localhost"
port                            "6600"
#
# Controls the amount of information that is logged.  Can be
# "default", "secure", or "verbose".
#
#log_level                       "default"
#
################################################################

## Workaround to change audio from ALSA because of Intrepid Ibex 
## Update
audio_output {
        type "pulse"
        name "My MPD PulseAudio Output"
}

```

Thanks guys.

---

### Post by ww2 on 2009-12-17
I'm having the exact same problem.

---

### Post by ww2 on 2009-12-17
Well, apparently mpd has problems dealing with more than one config file at once. The daemon starting process failed everytime because mpd attempted to use the files and directories specified in /etc/mpd.conf instead of ~/.mpdconf, which I created and configured.

So I gave up the .modconf file and set the proper permissions for all the files and directories as they were given in the original /etc/mpd.conf file.

This should help: [http://mpd.wikia.com/wiki/Music_Player_Daemon_HOWTO_Troubleshoot](http://mpd.wikia.com/wiki/Music_Player_Daemon_HOWTO_Troubleshoot)

---

### Post by treehouse on 2009-12-19
I've checked, double-checked, and triple-checked my permissions. They're all spot on what they should be, and both of my config files are exactly the same. There's no way that this should be a permissions problem. I don't see why I would get an error message saying "already in use" if it were a permission problem anyways.

---

### Post by ww2 on 2009-12-27
Anyway, I followed the guide below to run mpd as a user service, instead of a system service, and now it works perfectly in my Ubuntu Karmic notebook.

[http://gmpc.wikia.com/wiki/MPD_INSTALL_USER_SERVICE_UBUNTU](http://gmpc.wikia.com/wiki/MPD_INSTALL_USER_SERVICE_UBUNTU)

---

### Post by treehouse on 2010-01-02
> **ww2 said:**
> Anyway, I followed the guide below to run mpd as a user service, instead of a system service, and now it works perfectly in my Ubuntu Karmic notebook.

[http://gmpc.wikia.com/wiki/MPD_INSTALL_USER_SERVICE_UBUNTU](http://gmpc.wikia.com/wiki/MPD_INSTALL_USER_SERVICE_UBUNTU)

Still gives me the same error. Interestingly enough, my netstat output is slightly different:

```

nicholas@nicholas-desktop:~$ sudo netstat -tapn
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:6600          0.0.0.0:*               LISTEN      2879/mpd        
tcp        1      1 192.168.1.2:48007       74.125.170.149:80       LAST_ACK    -               
tcp6       0      0 ::1:6600                :::*                    LISTEN      2879/mpd        

```

I'm still at a loss...


EDIT: I tried to do it from inside of ncmpc. It turns out that it works just fine from inside of mpc and ncmpc. Still doesn't work by using the command "mpd --create-db". Still don't know why, but everything works perfectly, just not from that one command.

---

### Post by fenian on 2010-01-03
Have you tried this...

Install paprefs...

```
sudo apt-get install paprefs
```

Then apply some settings to pulse audio...

> Open PulseAudio prefrences from the menu System->Prefrences->PulseAudio Preferences

Click the Network Server tab

Check the box "Enable network access to local sound devices"

Check the box "Don't require authentication"


---

### Post by treehouse on 2010-01-03
> **fenian said:**
> Have you tried this...

Install paprefs...

```
sudo apt-get install paprefs
```

Then apply some settings to pulse audio...

Still didn't work, but thanks anyways! At least I got mpd to do what I want it to.

---

### Post by henriquemaia on 2010-01-27
I had the exact same problem. What I did to solve this was to revert the *pid* file location to its original place. When I restarted MPD, the problem was gone.

---

### Post by dunnemann on 2011-04-02
I had the same problem, and searching and searching I could fix it (if can called fix).

The solve to this problem was make 2 simple shell scripts:

```
#!/bin/bash

DEMON="cupsd"

if ps ax | grep -v grep | grep $DEMON > /dev/null
then 
	gksu kill -9 `netstat -antp|grep 127.0.0.1|awk '{ print $7 }'|cut -d'/' -f 1`; 	
else
	kill -9 `netstat -antp|grep 127.0.0.1|awk '{ print $7 }'|cut -d'/' -f 1`;
fi

```
This script is for kill all proceses who listen in host 127.0.0.1
And I use before anything else.

```
#!/bin/sh

SERV1='gmpc'
DEMON="mpd"

if ps ax | grep -v grep | grep $DEMON > /dev/null
then 
	if ps ax | grep -v grep | grep $SERV1 > /dev/null
	then
	    	mpc play;
	else
		gmpc | mpc play;
	fi
else
	if ps ax | grep -v grep | grep $SERV1 > /dev/null
	then
	    	`\\mpd` && mpc play;
	else
		`\\mpd` && gmpc | mpc play;
	fi	
fi	
```
This script is to run and play MPD.

I use both scripts using keyboard shortcuts, 


Sorry for my bad english.

---

