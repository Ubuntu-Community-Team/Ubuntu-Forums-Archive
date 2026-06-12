---
title: "script is starting x11vnc on boot"
date: 2012-08-07
forum: General Help
---

### Post by johnw230873 on 2012-08-07
Hi guys, new to Linux and the way services start on startup so any help here will be appreciated.

I'm trying to start up x11vnc at boot time, I have read a lot of posts that say they work but they require you to be logged in which is not what I'm after, I would like to be able to connect to my server before anyone has logged in.

I have downloaded and configure xrdp to run using vnc (eg console)
I then download x11vnc by
> 
sudo apt-get install x11vnc


I then tested the connect by running 
> 
 /usr/bin/x11vnc -forever -rfbport 5900


from the console and connecting from another computer.

I then create a init.d script and place it in /etc/init.d
> 

#!/bin/sh
# Starts and stops x11vnc
#


case "$1" in
start)

	start-stop-daemon --start --exec ./usr/bin/x11vnc -- -forever -rfbport 5900

		
;;

stop)
	
	start-stop-daemon --stop --exec ./usr/bin/x11vnc 

;;

restart)
  	$0 stop
  	$0 start
;;

status)
             if pidof -o %PPID x11vnc > /dev/null; then
                     echo "Running"
                     exit 0
             else
                     echo "Not running"
                     exit 1
             fi
;;

*)
        echo "Usage: $0 {start|stop|restart|status}"
        exit 1
esac


ran the commands 
> 
chmod +x /etc/init.d/x11vnc
updated-rc.d x11vnc defaults 


if I run this init.d script form the terminal it all works fine but it wont start on boot.

Any ideas?

---

### Post by MrGrey1 on 2012-08-07
Hi,
after much stuffing around and a fair bit of cussing I got x11vnc working at the login screen... again. Note to dev's: I wish you'd stop breaking it for us!

Install vnc
```
sudo apt-get install x11vnc
```

Set vnc password (saved in ~/.vnc/passwd)
```
x11vnc -storepasswd
```

Copy and paste password file to /etc/ directory:
```
sudo cp ~/.vnc/passwd /etc/x11vnc.pass
```

Create and edit the conf file /etc/init/x11vnc.conf
```
sudo gedit /etc/init/x11vnc.conf
```

Paste in:
```
start on login-session-start
script
x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5900 -localhost
end script
```

Note that I have -localhost set which enables me to connect via ssh. You should modify the script as appropriate for your connection settings.

Hope this helps. ;)

---

### Post by johnw230873 on 2012-08-08
Thanks MrGrey1, that worked really well.

Trying to understand more
what is the different between init and init.d and why didn't my approach work?
Ta

---

### Post by markbl on 2012-08-08
> **johnw230873 said:**
> 
I'm trying to start up x11vnc at boot time, I have read a lot of posts that say they work but they require you to be logged in which is not what I'm after, I would like to be able to connect to my server before anyone has logged in.
You can still start x11vnc before you have logged in on the target machine. Just use the -auth option to find the lightdm authority file. This is the best way to go, just ssh in to your machine and start x11vnc manually as per the x11vnc man page.

PS: Here's a post describing what I mean: [http://babilonline.blogspot.com.au/2012/06/ubuntu-1204how-to-use-vnc-even-at-login.html](http://babilonline.blogspot.com.au/2012/06/ubuntu-1204how-to-use-vnc-even-at-login.html).

BTW, I have found that the 3D desktops Unity and Gnome Shell work very poorly over VNC. You are best to log in with Unity 2D or Gnome Classic.

---

### Post by krunge on 2012-09-08
Perhaps there is a race condition for your script in that the X server has not started up yet, and when your x11vnc startup scripts runs, x11vnc cannot find the X server to connect to and so it exits.

MrGrey1 has a "start on login-session-start" which I would guess delays running the script until the X server is running.

As a quick and dirty workaround, x11vnc has an option, e.g. "-sleepin 30" that will cause x11vnc to sleep for 30 seconds before trying to connect to the X server.

---

