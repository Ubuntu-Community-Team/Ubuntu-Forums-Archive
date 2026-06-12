---
title: "A few questions"
date: 2010-04-10
forum: General Help
---

### Post by new_tolinux on 2010-04-10
I have my test webserver running on Ubuntu 9.04 desktop, along with some other server-programs.

1. Is it possible not to start Gnome at boot-time without removing it (so that I can start Gnome manually if needed).
2. Is it possible to lock a tty after logon without logging off?
3. Is it possible to start a program as a user in tty and keep the program running after logging off?

I have one program and I run it by hand, currently using a starter. If 2 (or 3) can be done, I don't need Gnome to boot anymore. It has to be started as a local user, without using sudo. I don't want it to run with root privileges.

---

### Post by sisco311 on 2010-04-10
[list=1]
[*] Boot with the *text* kernel parameter: [uhelp]community/GrubHowto#Setting%20kernel%20parameters[/uhelp]

[*]vlock

[*]rungetty to autostart an app
[/list]

---

### Post by Wardje on 2010-04-10
1. I assume this means removing the gdm entry from ```
/etc/init.d/
``` but I am not sure so you're best to wait for confirmation on that.

2. Not sure what you mean

3. I think what you want is the screen program :) Check out ```
man screen
```


edit: seems someone beat me to the pitch and also more correctly probably ^_^

---

### Post by sisco311 on 2010-04-10
> **Wardje said:**
> 1. I assume this means removing the gdm entry from ```
/etc/init.d/
``` but I am not sure so you're best to wait for confirmation on that.


Removing the symbolic links from the /etc/rc.{0,1,2,3,4,5,6,S}.d directories should work in Ubutnu 9.04:

```
sudo update-rc.d -f gdm remove
```
to enable gdm:
```
sudo update-rc.d -f gdm defaults
```

But in 9.10 the System-V style init script is replaced by an Upstart job. The *text* kernel parameter should work in all (supported) Ubuntu releases.

---

### Post by new_tolinux on 2010-04-10
> **sisco311 said:**
> 
[LIST=1]
[*] Boot with the *text* kernel parameter: [uhelp]community/GrubHowto#Setting%20kernel%20parameters[/uhelp]
[*]vlock
[*]rungetty to autostart an app
[/LIST]

Thanks, I managed to boot in text-mode.

After some googling on rungetty I actually still have a little problem.
In [http://manpages.ubuntu.com/manpages/gutsy/man8/rungetty.8.html](http://manpages.ubuntu.com/manpages/gutsy/man8/rungetty.8.html) it says:
>         In /etc/inittab, these lines:
        r1:12345:respawn:/sbin/rungetty tty1
        r2:2345:respawn:/sbin/rungetty tty2 telnet mail.foo.com
        r3:2345:respawn:/sbin/rungetty tty3 -u support top
        r4:2345:respawn:/sbin/rungetty tty4 -n 20 -w /etc rc5des
        Would   run   a   local  login  on  /dev/tty1,a  [telnet(1)]("http://manpages.ubuntu.com/manpages/gutsy/man1/telnet.1.html")  session  to
        mail.foo.com on /dev/tty2,and [top(5)]("http://manpages.ubuntu.com/manpages/gutsy/man5/top.5.html")on /dev/tty3.  Note that  [telnet(1)]("http://manpages.ubuntu.com/manpages/gutsy/man1/telnet.1.html")
        is  run  as user nobody, while [top(5)]("http://manpages.ubuntu.com/manpages/gutsy/man5/top.5.html") is run as user support, and start
        the program [rc5des(5)]("http://manpages.ubuntu.com/manpages/gutsy/man5/rc5des.5.html") at the  lowest  priority  level  with  a  current        directory of /etc.I also read [here]("http://www.linuxquestions.org/questions/ubuntu-63/since-we-have-no-etc-inittab-506281/") that there is no /etc/inittab and that it's replaced by /etc/event.d/*

Does that mean that this is a correct edit for /etc/event.d/tty5 ?
```
start on runlevel 2
start on runlevel 3

stop on runlevel 0
stop on runlevel 1
stop on runlevel 4
stop on runlevel 5
stop on runlevel 6

respawn: /sbin/rungetty tty5 -u myuser -g mygroup /path/to/program

```I really don't want to mess up my system, as it took me a long time to tweak it the way I want it.

Edit:
> **Wardje said:**
> 2. Not sure what you mean

3. I think what you want is the screen program :) Check out  ```
man screen
```edit: seems someone beat me to the pitch and also more correctly  probably ^_^

I want to run a program at boot-time, that keeps running. I don't want it to run as root.
2 (lock the tty) is meant to "solve" that by starting it manually, and not logging out of the tty. But "just" leave tty accessible to everyone seems to be a bad idea

In this case, nohup seems to do the trick with sabnzbd, although I still have to login, but that's not that big of a problem.
For some reasons my USB-disk doesn't mount at boot (it's in /etc/fstab) and therefore my MySQL database won't start, and stunnel also have some strange issues which are gone after I restart it manually.
Edit 2: "solved" USB-disk and with that "solved" MySQL also.

---

### Post by sisco311 on 2010-04-10
> **new_tolinux said:**
> I really don't want to mess up my system, as it took me a long time to tweak it the way I want it.


It looks good. Don't worry, backup the original file! If it doesn't work, you won't be able to access tty5, that's all. Even in the worst-case scenario you should be able to boot in recovery mode & restore the backup.

---

### Post by sisco311 on 2010-04-10
> **new_tolinux said:**
> 
I want to run a program at boot-time, that keeps running. I don't want it to run as root.


Oh, then you can create a System-V style init script (use the /etc /init.d/skeleton file as a template). With start-stop-daemon's -c option you can specify a user & group.

---

### Post by new_tolinux on 2010-04-10
> **sisco311 said:**
> Oh, then you can create a System-V style init script (use the /etc /init.d/skeleton file as a template). With start-stop-daemon's -c option you can specify a user & group.
I had a look at the skeleton-file, and there even is a sabnzbdplus-file in /etc/init.d

But googling on [FONT=Courier New]/etc/init.d script[/FONT] and [FONT=Courier New]start-stop-deamon -c[/FONT] didn't produce any useable results for me.
I had a look in the apache2 file as well, because that one needs www-data to have access, but there's no mention of www-data in the whole apache2-file.

Edit:
sabnzbdplus is a program to download from usenet. I think a download program should never run as root, that's why I want to run it as my default user.

Edit 2:
I managed to mount my USB-disk. Because of that, MySQL does start on boot.
Only "problems" left:
1. run sabnzbd at boot as local unprivileged user
2. stunnel only running after manual restarting with /etc/init.d/stunnel4 restart

---

### Post by sisco311 on 2010-04-10
[list=1]
[*] You can set the user in /etc/default/sabnzbdplus.


[*] try to start it as the last daemon:
```
sudo update-rc.d -f stunnel4 remove
sudo update-rc.d stunnel4 defaults 99
```[/list]

If you are still interested, a very basic init script looks like this
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: 
# Description:       
#                    
### END INIT INFO

# name of the init script
NAME=
# full path to the application
DAEMON=/usr/bin/$NAME
# full path to the init script
SCRIPTNAME=/etc/init.d/$NAME
# username
USER=
# additional args 
DAEMON_ARGS=

#
# Function that starts the daemon/service
#
do_start()
{
	start-stop-daemon --start --quiet --chuid $USER --exec $DAEMON -- $DAEMON_ARGS
}

#
# Function that stops the daemon/service
#
do_stop()
{
	start-stop-daemon --stop --quiet --name $NAME &> /dev/null&
}


case "$1" in
  start)
	do_start
	;;
  stop)
	do_stop
	;;
  restart)
	do_stop
	sleep 1
	do_start
	;;
  *)

	echo "Usage: $SCRIPTNAME {start|stop|restart" >&2
	exit 3
	;;
esac

:

```

---

### Post by new_tolinux on 2010-04-10
Ok, got sabnzbdplus up-and-running.
I did as you mentioned:
```
sudo update-rc.d -f stunnel4 remove
sudo update-rc.d stunnel4 defaults 99
```After a reboot and a "sudo -i":
```
telnet localhost 2830
```result:
```
Trying ::1...
Trying 172.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
```Then:
```
/etc/init.d/stunnel4 restart
```Result:
```
Restarting SSL tunnels: [stopped: /etc/stunnel/stunnel.conf] [Started: /etc/stunnel/stunnel.conf] stunnel.
```After that:
```
telnet localhost 2830
```result:
```
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
200 news.myusp NNRP Service Ready (posting ok) (yEnc enabled).
```Edit:
Maybe it's better to mark this thread as solved, and open a new topic for this specific stunnel problem.

---

