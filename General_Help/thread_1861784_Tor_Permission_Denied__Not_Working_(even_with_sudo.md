---
title: "Tor Permission Denied / Not Working (even with sudo)"
date: 2011-10-16
forum: General Help
---

### Post by ex1t on 2011-10-16
Currently been getting this error when trying to start/stop/restart tor. 
It has been working fine up until last night when I got this error;
> Stopping tor daemon: FAILED (/usr/sbin/tor died: process 2766 not running; or permission denied).
dan@baby:~$ sudo /etc/init.d/tor start
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
Oct 15 23:41:59.921 [notice] Tor v0.2.1.30. This is experimental  software. Do not rely on it for strong anonymity. (Running on Linux  x86_64)
Oct 15 23:41:59.923 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Oct 15 23:41:59.923 [notice] Opening Socks listener on 127.0.0.1:9050
done.
dan@baby:~$ tor has been running properly until about 11pmEST.  Now I haven't modified the TORRC since the last time it was running  fine... I don't know exactly how this problem occured, but I do know  these things; 
I have not created any other accounts other than my (dan) user, and I  ran tor via "sudo", I am the only other user on my laptop, I  run Ubuntu 11.04 LTS  (was waiting for the next LTS before  upgrading) with 6Gb RAM / 1Gb VRAM and an intel i7 @ 1.66Ghz

I don't think all the information was neccesary but taking precautions,  any other information will be given upon request. Also; it claims that  it is running after I "start" it back (as seen in the quote) but when I  go to visit a site after it suspectedly claims to be working I get this  error; 
> The proxy server is refusing connections
Firefox is configured to use a proxy server that is refusing  connections.Then I am stuck right back at having a permission  denied error. I have no idea whats going on, and to note - I have been  using this laptop with Ubuntu for about 6 months with tor with no  problems like this before, so this is all pretty confusing for me.

**Edit Note:
Also can not uninstall(sudo apt-get remove tor) tor because of the same  error in this topic, so I can not technically reinstall to fix my error  either - which I have tried. ):

---

### Post by Dangertux on 2011-10-16
> **ex1t said:**
> Currently been getting this error when trying to start/stop/restart tor. 
It has been working fine up until last night when I got this error;
tor has been running properly until about 11pmEST.  Now I haven't modified the TORRC since the last time it was running  fine... I don't know exactly how this problem occured, but I do know  these things; 
I have not created any other accounts other than my (dan) user, and I  ran tor via "sudo", I am the only other user on my laptop, I  run Ubuntu 11.04 LTS  (was waiting for the next LTS before  upgrading) with 6Gb RAM / 1Gb VRAM and an intel i7 @ 1.66Ghz

I don't think all the information was neccesary but taking precautions,  any other information will be given upon request. Also; it claims that  it is running after I "start" it back (as seen in the quote) but when I  go to visit a site after it suspectedly claims to be working I get this  error; 
Then I am stuck right back at having a permission  denied error. I have no idea whats going on, and to note - I have been  using this laptop with Ubuntu for about 6 months with tor with no  problems like this before, so this is all pretty confusing for me.

**Edit Note:
Also can not uninstall(sudo apt-get remove tor) tor because of the same  error in this topic, so I can not technically reinstall to fix my error  either - which I have tried. ):


Ok , a few questions for you here. Can you verify if Tor is actually running 

```

sudo ps aux | grep tor

```

```

sudo netstat -anlp | grep :9050

```

Also are you using an intermediate caching proxy (polipo? privoxy?) If so verify those are running properly as well.

If not is your browser point to the correct proxy address 127.0.0.1:9050?

Also what happens if you do the following

```

sudo /etc/init.d/tor restart

```

Still the permission denied / service not running error? 

As far as reinstalling Tor goes you can do the following 

```

sudo killall -9 tor
sudo update-rc.d -f tor remove
sudo apt-get remove --purge tor tor-geoipdb
sudo apt-get install tor tor geoipdb

```

Hope this helps.

---

### Post by ex1t on 2011-10-16
tor is not running, i do have the proxy addresses setup properly, polipo is running properly, and thanks i will try to reinstall it and see if this solves my problem and yes, i still get the permission denied with restart, ill post it the stuff here.

```
dan@baby:~$ sudo ps aux | grep tor
[sudo] password for dan: 
dan       1774  0.0  0.0 162024  4092 ?        S    Oct15   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
dan       1786  0.0  0.0 142888  2632 ?        Sl   Oct15   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
dan       1792  0.0  0.0  63556  2640 ?        S    Oct15   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
dan       1898  0.0  0.0   4220   584 ?        Ss   Oct15   0:00 /bin/sh -c /usr/bin/compiz-decorator
dan       1899  0.0  0.2 252504 12836 ?        Sl   Oct15   0:05 /usr/bin/unity-window-decorator
dan       2027  0.0  0.1 315016  8424 ?        Sl   Oct15   0:00 /usr/lib/indicator-datetime/indicator-datetime-service
dan       2029  0.0  0.0 245456  5756 ?        Sl   Oct15   0:00 /usr/lib/indicator-me/indicator-me-service
dan       2031  0.0  0.0 240040  6044 ?        Sl   Oct15   0:00 /usr/lib/indicator-session/indicator-session-service
dan       2033  0.0  0.0 207364  4928 ?        Sl   Oct15   0:01 /usr/lib/indicator-application/indicator-application-service
dan       2035  0.0  0.1 344208  7476 ?        Sl   Oct15   0:02 /usr/lib/indicator-sound/indicator-sound-service
dan       2037  0.0  0.0 226908  5096 ?        Sl   Oct15   0:00 /usr/lib/indicator-messages/indicator-messages-service
dan       2815  6.0  0.4 368820 27556 ?        Sl   00:40  50:04 gnome-system-monitor
dan       8945  0.0  0.0  13128  1052 pts/0    S+   14:32   0:00 grep --color=auto tor
dan@baby:~$ sudo netstat -anlp | grep :9050
dan@baby:~$ sudo /etc/init.d/tor restart
Stopping tor daemon: FAILED (/usr/sbin/tor died: process 2832 not running; or permission denied).
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
Oct 16 14:34:33.202 [notice] Tor v0.2.1.30. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Oct 16 14:34:33.204 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Oct 16 14:34:33.204 [notice] Opening Socks listener on 127.0.0.1:9050
done.
dan@baby:~$ 
```
ps thanks for the help and sorry for the late reply, took forever to find this post after i got done sleeping xD

---

### Post by Dangertux on 2011-10-16
Alright well let me know if reinstalling helps. Also make sure your polipo configuration file is correct.

---

### Post by ex1t on 2011-10-16
> **Dangertux said:**
> 
```

sudo killall -9 tor
sudo update-rc.d -f tor remove
sudo apt-get remove --purge tor tor-geoipdb
sudo apt-get install tor tor geoipdb

```Hope this helps.

reinstalling using these commands were the backbone for my overall success. 
i really didn't understand how i got the error i did and wish i had more info to give out for a better solution, i think it was after removing it from startup and restarting the computer then using the apt-get remove was what made it possible, otherwise i would of kept getting those permissions denied errors. now i don't get any, can restart stop and stop as i please. 
thanks again Dangertux :)

---

### Post by ex1t on 2011-10-16
Just noticed how I keep getting this problem, it was solved after I reinstalled. but I had to reconfigure my torrc so that I can be running a hiddenservice, well as soon as i do that and restart tor, I then get that permission denied error. maybe it has something to do with the tor version, i just noticed there is a more updated one then the one i am getting via apt-get anyhow.

---

