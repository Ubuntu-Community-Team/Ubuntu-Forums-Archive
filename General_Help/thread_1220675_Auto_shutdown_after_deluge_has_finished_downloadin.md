---
title: "Auto shutdown after deluge has finished downloading"
date: 2009-07-23
forum: General Help
---

### Post by dopple on 2009-07-23
Is there a way to make my laptop shutdown automatically after deluge has finished downloading? I usually leave deluge up and running when I'm in the house so that I can seed, but if I'm out of the house, I'd like to be able to shut down my laptop automatically.

---

### Post by bacil on 2009-07-23
dont know deluge this good but it should be easy job. you can probbaly write script that checks network traffic and if there is none shuts down the laptop. 

i wil look on to deluge if we can even hook up with it

---

### Post by Johnny B on 2009-07-23
install conkydeluge:
[http://ubuntuforums.org/showthread.php?t=946664]("http://ubuntuforums.org/showthread.php?t=946664")

run this script with sudo before you walk away

edit:you may need to install zenity, i dont remember if its included by default
# sudo apt-get install zenity

> #!/bin/bash
DL=`conkyDeluge |grep Downloading`
while [ "$DL" != "" ] ;do
    DL=`conkyDeluge |grep Downloading`
#    echo "not yet"
    sleep 10
done 

#gtk warning
#zenity --info --text="computer will shutdown in 20 seconds"
#sleep 20

#GTK warning better version
#wait time = 100 x 0.2 = 20
(for a in `seq 1 100` ; do echo $a; sleep 0.2; done) | zenity --auto-close --auto-kill --progress --text=" Shutting down\n click cancel to stop" --title="Shutdown"

#echo now shutdown
halt


---

### Post by dopple on 2009-07-24
You the man. I'll give this a pop.

---

### Post by dopple on 2009-07-24
I am going to mod this with a little sendEmail script so that it emails me before shutting down so that I know it's worked. Thanks dude.

---

### Post by dopple on 2009-07-24
```
#!/bin/bash
DL=`conkyDeluge |grep Downloading`
while [ "$DL" != "" ] ;do
DL=`conkyDeluge |grep Downloading`
echo "not yet"
sleep 10
done


#GTK warning better version
#wait time = 100 x 0.2 = 20
(for a in `seq 1 100` ; do echo $a; sleep 0.2; done) | zenity --auto-close --auto-kill --progress --text=" Shutting down\n click cancel to stop" --title="Shutdown"

ls /home/graham/Downloaded > /tmp/Downloaded.txt
sendEmail -f xxxxxxxx.com -t xxxxxxxxxx -s smtp.gmail.com:587 -xu xxxxxxxx -xp xxxxxxxxxx -u Laptop has shutdown -m Torrents have finished. Laptop has shutdown. -a /tmp/Downloaded.txt
rm /tmp/Downloaded.txt

#echo now shutdown
halt
```

---

### Post by bigeyes0x0 on 2009-08-06
I try to do this through cron on 9.04 server but I wasn't successful.

```
#!/usr/bin/perl
use strict;

if (!open CONFIG, "</home/username/bin/shutdown-config") {
        die "Cannot open shutdown config file: $!";
}

while (<CONFIG>) {
        chomp;
        if ($_) {
#               print "setup to shutdown if dl complete\n";
                my $DL = `conkyDeluge | grep Downloading | wc -l`;
                if ($DL == 0) {
#                       print "no download\n";
                        system "halt";
                } else {
#                       print "still download\n";
                }
        } else {
#               print "not setup to shutdown if download complete\n";
        }
}
close CONFIG;
```

Any idea why?
It runs fine though command shell though. And the config file is just a simple text file with 1 if I want to set the schedule and 0 for not.

EDIT: Solved it myself, somehow perl system call does not run as root, need to sudo it. Any idea for better implementation, instead of system and sudo?

---

### Post by stonecold82 on 2010-04-10
This script works only with conkydeluge 2.12 installed in karmic koala (9.10)

I tried with 2.13 conky it's not working.

:)

---

### Post by dopple on 2010-06-28
In the most recent version of deluge there is an option to run a command after torrents have finished downloading. just enter the halt command in there.

---

### Post by stonecold82 on 2010-08-07
Thanks working Great with this command :D

---

### Post by apsot on 2010-12-02
> **dopple said:**
> In the most recent version of deluge there is an option to run a command after torrents have finished downloading. just enter the halt command in there.

you mean edition 1.3.0? where exactly is that option?

---

### Post by Vaphell on 2010-12-02
in deluge prefs look for plugins, execute is the one you need - you mark it, new menu option shows up

edit: i got 1.2.2 though but it should be present in 1.3, it's mentioned on deluge page
[http://dev.deluge-torrent.org/wiki/Plugins](http://dev.deluge-torrent.org/wiki/Plugins)

---

### Post by joelstitch on 2011-04-07
> **dopple said:**
> In the most recent version of deluge there is an option to run a command after torrents have finished downloading. just enter the halt command in there.

Would I just add the word **halt** to the command?

Like this?:
[IMG]http://img193.imageshack.us/img193/3857/halt.png[/IMG]

---

### Post by joelstitch on 2011-04-08
I figured out. For the newbies like me that are wondering exactly how to do it here are the directions:

1. Open gedit and paste this in it:

> #!/bin/bash
DL=`conkyDeluge |grep Downloading`
while [ "$DL" != "" ] ;do
    DL=`conkyDeluge |grep Downloading`
#    echo "not yet"
    sleep 10
done 

#gtk warning
#zenity --info --text="computer will shutdown in 20 seconds"
#sleep 20

#GTK warning better version
#wait time = 100 x 0.2 = 20
(for a in `seq 1 100` ; do echo $a; sleep 0.2; done) | zenity  --auto-close --auto-kill --progress --text=" Shutting down\n click  cancel to stop" --title="Shutdown"

#echo now shutdown
halt 			 		

and save it as **shutdown.sh**

2. Open Deluge and click on Edit > Preferences > Execute

3. On Event choose **Torrent Complete** and on Command write the address for the .sh file you just created. In my case is /home/name/Desktop/shutdown.sh

4. Click on **Apply**

---

### Post by Cas07 on 2011-04-18
joelstitch you should post that script on our forums: 

[http://forum.deluge-torrent.org/viewtopic.php?f=9&t=35057](http://forum.deluge-torrent.org/viewtopic.php?f=9&t=35057)

Thought I would emphasis that currently the Execute plugin will only parse scripts (python, bash) and not individual commands. There is a [user guide]("http://dev.deluge-torrent.org/wiki/Plugins/Execute") with more info.

---

### Post by Splat_NJ on 2011-09-25
I know this is a few months old but you don't have to use Conky to get Deluge to shutdown the PC when it completes downloads. Use the Execute plugin and use this for the "Torrent Complete"'s command (no quotes):

"/usr/bin/dbus-send --print-reply --dest=org.gnome.SessionManager  /org/gnome/SessionManager org.gnome.SessionManager.RequestShutdown"

I couldn't get Deluge to simply close/kill itself when downloads completed so I'm running qbittorrent. It was so much easier to install, setup, and get it to act like I want it to.

---

### Post by npjoseph on 2011-12-23
here's a plugin to do that.

[http://code.google.com/p/raychen/downloads/detail?name=AutoShutdown-0.1-py2.6.egg](http://code.google.com/p/raychen/downloads/detail?name=AutoShutdown-0.1-py2.6.egg)

---

