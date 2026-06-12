---
title: "Daemon not starting up automatically"
date: 2011-06-04
forum: General Help
---

### Post by kesh_ on 2011-06-04
Hi, 

I'm a "quasi-noob" who has used Ubuntu to develop some programs over the last few years without much messing around with the OS.

I've been trying to get mpd (music player daemon) to run properly on my Ubuntu 10.04 box and have everything set up the way I like it with one problem: it doesn't start up automatically when I boot up.

MPD starts properly if I manually type in "sudo /etc/init.d/mpd start" and stays running once I start it.

With my limited Linux knowledge, I thought placing files in /etc/init.d is equivalent to placing entries in HLMS\Microsoft\Windows\CurrentVersion\Run registry location in Windows.

I tried "cat /var/log/messages|grep mpd" and "cat /var/log/boot.log|grep mpd", and both returned nothing.

Can anyone here help me out solving this problem?

Thanks,
Kesh

---

### Post by macaholic on 2011-06-04
You could try the *easy* way, by adding the command to startup applications which is in System>Preferences>Startup Applications (if I remember correctly).
Note that this will not start the daemon on boot, but rater whenever you start a session with your user, i.e. when you log in.

---

### Post by pksadiq on 2011-06-04
You might try:
```
sudo update-rc.d mpd enable
```

---

### Post by kesh_ on 2011-06-04
@macaholic - thanks but I need mpd to run without a desktop user as it is serving remote users.

@pksadiq -

Tried as you suggested, but still no cigar :( 

Is there a start up script that I can check to see what's starting up at the boot-up?

Kesh

---

### Post by Lateralis on 2011-06-05
I'm shooting from the hip here!  


Are there mpd scripts in the /etc/rc?.d directories?

```

ls /etc/rc?.d/*mpd*

```

I've just installed mpd on my machine and the scripts are there.  As far as I know, scripts in the multi-user run-levels (?=2,3,4,5) should execute at start-up.  So if you have them, then I'm not sure.  

If you don't have scripts in these directories, try

```

sudo update-rc.d mpd defaults

```

That should add the necessary scripts to the rc?.d directories.  

If that still doesn't work, try adding a link in the /etc/rcS.d to the script in the /etc/init.d

```

sudo ln -s /etc/init.d/mpd /etc/rcS.d/mpd

```

According to some READMEs and manpages, everything in rcS.d gets executed at boot, irrespective of the run-level.

---

### Post by kesh_ on 2011-06-05
@Lateralis - 

I think this did the trick! (Or at least it worked this time around) :P

```

sudo update-rc.d mpd defaults

```

Although I'm not completely certain...

One more question. How do you control the boot order?

If I recall, the MPD did start on its own when I first installed it, but it stopped starting-up when I bind it to my wireless IP. So, I wonder if MPD was started before wireless network service (among other networking subsystems) started and it just quit up on failed to bind to the IP. Does this make sense?

---

### Post by Lateralis on 2011-06-05
The order in which services are started depends upon the priority number in the script name.  On my Lubuntu virtual machine (currently in Windows... eurgh), I have the following:

```

$ ls /etc/rc?.d/*mpd
 /etc/rc0.d/K14mpd 
 /etc/rc1.d/K14mpd
 /etc/rc2.d/S30mpd
 /etc/rc3.d/S30mpd
 /etc/rc4.d/S30mpd
 /etc/rc5.d/S30mpd
 /etc/rc6.d/K14mpd
$ ls /etc/rc?.d/*networking
 /etc/rc0.d/S35networking
 /etc/rc6.d/S35networking

```

The K stands for Kill, the S stands for Start, so when the system is exiting a multi-user run level the service is stopped.  When entering a multi-user run level, the service is started.  To change the order in which services are started, change the number - the larger the number, the later the service will start.  (Note: the reverse is true of the kill scripts.  A script with a larger priority number is executed before one with a smaller number.)  If you wish to start the service after networking, then we need to change the run priority.  In my case above, that means giving the mpd daemon a priority number greater than 35.  

Having just done a few tests on my virtual machine, I think you will need to first remove the existing scripts before creating new ones:

```

sudo update-rc.d -f remove mpd
sudo update-rc.d mpd defaults 36

```

36 is what is appropriate for my system, but you should check yours out with the ls command.  You may have separate wireless and networking scripts - I don't really know and can't check on here right now - so you should chose a number appropriate for your system.  

Whether that will work or not I don't know, but it certainly won't hurt your system if you start mpd after networking.


Edit: For more info, check out this link: [http://www.debuntu.org/how-to-manage-services-with-update-rc.d]("http://www.debuntu.org/how-to-manage-services-with-update-rc.d")

---

### Post by kesh_ on 2011-06-05
Awesome! Thank you for the explanation. Now things are making a lot more sense now.

For daemons to run, I suspect that you need to be in multi-user mode. So I looked at /etc/rc2.d content:

```

README         S30mpd         S50rsync      S90binfmt-support  S99ondemand
S20fancontrol  S50cups        S70dns-clean  S99acpi-support    S99rc.local
S20kerneloops  S50pulseaudio  S70pppd-dns   S99grub-com

```

dns-clean and pppd-dns are the two things that look like remotely related to networking, so I think I'll put mpd after 70 just be on the safe side.

Thanks again for the quick tutorial (and the link)!

---

### Post by Lateralis on 2011-06-05
You're welcome!  As I said in my first post, I'm kinda shooting from the hip here and learning as I go along too!  I'd be interested to know if this works, so keep us posted! =D

---

### Post by mpiter on 2011-07-18
kesh_, although you tagged this thread as Solved, I am not sure you fully understood the relationships between MPD and the network.  You do not need to start MPD AFTER starting the network, it does not matter.  You can actually keep S30mpd instead of replacing it by S70mpd.  But keep in mind that a wifi connection is not automatically opened in Ubuntu without a user logged in for security reasons.  For example, you would not like your computer to open a wifi public connection at boot time in a foreign place without knowing it.  That would be an open door to piracy since a wifi connection is so easy to hack.  So, you usually need to log in to have a startup program to automatically search for a wifi network.  As a consequence, if your computer is not wired connected to a network, you will not have a network connection opened without a user logged in.  Hence, you will not be able to access your MPD server from an MPD client without a user logged in in your computer in that situation.  That might be the source of your problems.

---

