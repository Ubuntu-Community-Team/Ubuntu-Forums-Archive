---
title: "How to autostart a script AFTER NICs are enabled?"
date: 2011-01-10
forum: General Help
---

### Post by gleemer on 2011-01-10
I have a script that I need to run on boot which requires my network interfaces to be already setup when it runs. On an old P4 test machine (all machines in question are running server 10.10) I have to add "sleep 1" in front of my script to get this to work. My application is boot-speed sensitive but I'm alright with this.

What I'm not alright with, and don't understand, is when I move the script to my Atom D510 platform I have to bump up to "sleep 9" to get it to work reliably but even as low as "sleep 5" works on occasion. I have been using both /etc/init.d and an @reboot command inside /etc/crontab with similar results.

I don't understand why I have to sleep so much longer on the Atom (everything else aside they both boot in about the same amount of time) and I don't understand why the duration I have to sleep on the Atom is not stable. 

Is there any way I can get a more fine grained control of when my script executes (ie as soon as possible after the network interfaces are started)?

---

### Post by sisco311 on 2011-01-10
Hi and welcome to the forums!

Write an [Upstart]("http://upstart.ubuntu.com/getting-started.html") job. Something like:

/etc/init/my-job.conf:
```

# name - long name
#
# description

author "author"
description "short description"

start on (local-filesystems 
          and net-device-up IFACE!=lo)

stop on runlevel [016]

script
  *your script here*
end script
```

---

### Post by gleemer on 2011-01-11
Hello sisco thank you for the prompt reply. Unfortunately I am not able to get this working.

Here is the first .conf I tried (/etc/init/reboot.conf):
```

#blah blah blah
#
#etc

author="<me>"
description="<blah>"

start on (local-filesystems and net-device-up IFACE!=lo)
stop on runlevel [016]

pre-start script
   #prepare environment
   RESTART="/root/1.6.3/<MyModule>"
   PGREP="/usr/sbin/pgrep"
   NAME="<MyModule>"
   cd=/root/1.6.3
end script

script
   <MyScript>
end script
```Nothing appears to happen (my script includes echoing a message to a log file stating pass/fail with a timestamp and this does not appear, it seems that the script is not even executing) and I cannot find anything in dmesg to indicate why (though I don't really know what to grep for either).

So I tried the following trivial .conf (3 different iterations, each with a different start on condition):
```

#start on (local-filesystems and net-device-up IFACE!=lo)
#start on net-device-up IFACE==eth0
start on runlevel [2345]
stop on runlevel [016]

script
   echo STEVEN!!! >> /root/1.6.3/<MyLog>
end script
```And again nothing. 

This does seem to be exactly what I want, starting the script directly after my interfaces turn on, but it doesn't work! I'm quite new to Linux so in addition to code errors there maybe something else very obvious that I'm missing.

Thanks for the help.

---

### Post by gleemer on 2011-01-20
After dithering around with some other problems I've returned to this one and still no joy. Having read around about upstart I question the syntax of the following:

```
start on (local-filesystems and net-device-up IFACE!=lo)
```but I can't find any consistent documentation on how it should be written. I've tried among other things interface-up eth0, interface-up IFACE=eth0, something about interface-added or net-device-added I cant recall anymore. 

So this is what I know:

*the script is valid and it can be run successfully from any environment but it must be run as root so I don't think I'm mixing up any variables but perhaps there is a permissions problem here? Though I would hope upstart has root privileges?

*the above is moot because the script isn't even being run: the first thing it does after initializing variables is write to a log and that write never occurs. Further, 
```
initctl list | grep <myJob> 
```almost invariably reveals that my job is stopped/waiting. The only time it wasn't stopped/waiting was when it couldn't find my job at all (for reasons unknown).

*CRON @reboot with a small sleep period inside the script works without fail so this is what I'm going to stick with for now but it is a suboptimal solution. I would really like to be able to start my script immediately after eth0 is configured.

---

### Post by sisco311 on 2011-01-20
Try to use **expect fork** and **respawn** stanzas.
[http://upstart.ubuntu.com/wiki/Stanzas](http://upstart.ubuntu.com/wiki/Stanzas)

---

