---
title: "Karmic Koala: Howto startup SSH and MPD"
date: 2010-01-10
forum: General Help
---

### Post by rroic on 2010-01-10
As most users, I am new to Upstart.

I am looking for the easiest way to get my workstation running with the needed services. At this time, these include SSHD and Music Player Daemon.

I ve installed both and they work when activated manually by sudo /etc/init.d/ssh start, or mpd respectively. But I don t have a clue as to how to start them up with an Upstart job?

I ve tried this:

```
rroic@rroic-media-hp:~$ cat /etc/init/ssh.conf
start on runlevel [2345]
stop on runlevel [016]

exec /etc/init.d/ssh start
```

but to no success.

Any hints or specific Upstart jobs for these two would be much appreciated.

BTW. Can t believe that I installed a Linux distribution and can t get SSHD running. Makes you wander if Linux is still ready for the server, now that it s "ready for the desktop".

Cheers

---

### Post by m.maga on 2010-01-12
I have exactly the same issue with sshd. Samba service doesn't start on boot-up. No tty[1-6] at all.

It works using *sudo service ssh start* command. Console works using *sudo start tty[1-6]* from X11 terminal as xterm or gnome-terminal.

Some tips? Some help please?

Thank You.

---

### Post by doas777 on 2010-01-12
how did you configure your network? if you used network-manager (the gui) did you check the box that says "Avaliable to all users"? if not, then the network connection will be inactive until login.

I've never had to start sshd myself on ubuntu. the install sets it to start at boot, but if the network is not yet present, it exits, usually leaving a log indicating such.

---

### Post by m.maga on 2010-01-12
I digged a bit and I figured out that local interface was commented in */etc/network/interfaces*.

So I did *sudo nano -w /etc/network/interfaces* and uncommented the lines below:

[I]auto lo
iface lo inet loopback[/I]

Check the forum thread [**[COLOR="red"]9.10 Upstart Breaks Cron,Cups,SSH, etc...[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1305226&page=3") and the bug report [**[COLOR="Red"]Some essential services are not started[/COLOR]**]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520") for more information.

I suppose the bug [[COLOR="Red"]**grub nice 'recordfail' feature doesn't work for hibernation**[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/447725") comes together.

Thank You doas777.

Have a good day!

---

### Post by BigEd55 on 2010-09-14
For what its worth... I have tried just about all the items listed above and some work at times, and at other times they don't. Nothing was reliable... Hit and miss until I came up with these steps.

What I ended up doing was...
1- Reloaded the Upstart to the 0.6.3-11 version.
1a- Checked for any other upgrades (there was none)
1b- Reinstalled SSH and FreeNX with sudo apt-get install --reinstall {service}
   ** both 1a and 1b were done just to see if any entries were put into /etc/init (there were none)

2- Added these entries to rc.local (force them to start)
     /bin/bash /etc/init.d/ssh start
     /bin/bash /etc/init.d/freenx-server start

3- Un-Commented in /etc/ssh/sshd_config file the ListenAddress entries.
     I added in this order ListenAddress 127.0.0.1 and followed on the next line with ListenAddress 0.0.0.0 in this order...

Noted that the interfaces still had the default entry the whole time 
     iface lo inet loopback

My opinion is that these services aren't up-to-date with the upstart, thus failing. And with the above changes I've reboot many times and still am able to get logged onto the box. Also noting that my server is thousands of miles away with no physical access unless I want to pay for someone to do it. I only have rescue mode access provided by my Provider.

---

