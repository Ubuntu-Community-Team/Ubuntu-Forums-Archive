---
title: "Stops loading after login"
date: 2006-03-16
forum: General Help
---

### Post by kidcharles on 2006-03-16
Hi all, I have a pretty serious error where the gnome desktop stops loading after the login screen. It hangs on the brown background. I can move the mouse pointer, but that's it. I suppose there is a log file that might help?

---

### Post by kidcharles on 2006-03-16
I should mention that I can't even get a terminal login by switching screens (ctrl-alt-F1). There is just an underline cursor, but hitting enter doesn't bring up a login prompt, just moves the cursor down the screen.

---

### Post by kidcharles on 2006-03-16
Ok, I was able to fully load the desktop by not having a network connection when booting. I noticed that it was getting hung up during initialization of the NFS service (saw this using ctrl-alt-F8).

(Hehe, I feel like I'm putting on a one-man theater performance.)

---

### Post by kidcharles on 2006-03-16
Ok, I don't think it was the NFS service, I uninstalled the package, and have the same problem. So basically I can't load up the Gnome desktop if I have my network connection established. It was working fine earlier today, made no changes.

---

### Post by rfruth on 2006-03-16
So you *can* login without the X windows system and no network connection, how about startx without NIC ?

---

### Post by mwrobert on 2006-03-17
Same issue here.  Started after I configured my wifi card - but that was one of the first things I did, so not sure that the issue is with that.  

But it is that I get the login screen, authenticate, then it hangs for literally 10 minutes before loading the desktop. It will always load, but it takes quite a long time.

---

### Post by chrisdavitt on 2006-03-17
Similar problem with me too. I get a Gnome login screen and then login, it then goes to a brown screen and you can still move the pointer, about 15 seconds later an ubuntu logo appears but nothing else happens. I then go get dinner and return an hour later to find that the desktop has appeared. This has happened several times and is on a new installation along with latest updates. I think it maybe a gnome configuration problem but I'm not certain were to start looking as I usually use KDE.

From syslog
Mar 17 18:01:44 localhost gconfd (chris-8619): Resolved address "xml:readwrite:/home/chris/.gconf" to a writable configuration source at position 0

Any ideas?

---

### Post by Second_Player on 2006-03-17
it just happened to me too, i tried putting a bigger harddrive in my imac g3, i ended up putting the old hardrive back in and nothing happens now after login.

---

### Post by kidcharles on 2006-03-17
I have recently installed a wi-fi card myself. It worked fine at first, then I had some problems with it configuring the network on startup, now this problem. I tried turning off wireless and only having it configure a wired connection on startup but the same problem still happens.

I have some similar problems with gconf errors popping up in /var/log/syslog, I don't know for sure if they are related to this problem.

---

### Post by kidcharles on 2006-03-17
rfruth:

Basically I turn off my router during startup, and don't have any problems (except of course no network access). I can then restart my network devices and they work fine.

When it freezes on the brown screen, I can do a ctrl-alt-backspace to restart X, and it does restart, but hangs again on the brown screen.

---

### Post by kidcharles on 2006-03-19
I'm still looking for a solution to this one.

---

### Post by chrisdavitt on 2006-03-21
I'm getting this problem from an new installation. No updates. I've tried disconnecting the network during boot. The only time it has ever started up Gnome straight away was after a brown out which shutdown the computer after which the router was unable to get a ADSL connection.

Well tried disconnecting the WAN side of the router and rebooting but no success. This makes no sense...

What modules and services does Gnome startup after user authentication?

---

### Post by chrisdavitt on 2006-03-21
There appears to be a number of reasons why Gnome can be slow for example [http://www.gnome.org/~lcolitti/gnome-startup/analysis/](http://www.gnome.org/~lcolitti/gnome-startup/analysis/) makes for some interesting reading. not sure if it is directly applicable as some of you may have been using ubuntu for a while. I think part of my problem maybe due to me running this on an old KT7A_RAID motherboard and the drive it is installed on is old and connected by the HPT raid chip causing IO access to be rather slow.

However, I'm still not quite convinced....

---

### Post by elektronaut on 2006-03-22
@kidcharles

I found your thread because I just had the same problem. As it turned out, I had a stupid error in  /etc/network/interfaces. I had to change this file because I switched temporarily to another wireless network and when I set everything back to the old values I took out all '#', by mistake also the one in front of one comment line... As you were mentioning that you configured some network card: Maybe it's the same reason?

---

### Post by kidcharles on 2006-03-26
elektronaut

If I'm understanding you correctly you had a bad /etc/network/interfaces file because you uncommented a line that had to be commented (like a plain english note?) That's definitely not my problem, but thanks for the idea.

---

### Post by kidcharles on 2006-03-26
Success!

Looks like my /etc/network/interfaces file was missing a little line: auto lo. I believe this configures the loopback interface which is non-optional. Here's my working interfaces file for reference:
```

iface lo inet loopback
auto lo

iface ra0 inet static
wireless-essid mynetworkname
address 192.168.11.2
netmask 255.255.255.0
gateway 192.168.11.1

auto ra0

```

---

### Post by chrisdavitt on 2006-03-27
Well that doesn't solve my problem. auto lo is present within the /etc/network/interfaces file

Not really a problem as I moved to KDE which doesn't have this speed problem ;) 

sudo apt-get install kubuntu-desktop

---

### Post by adam.mech09 on 2006-04-02
Hi Everybody

I've been having this same issue for a couple weeks now, accidentally been posting on a dapper forum instead.  They've all been saying network issues with /etc/network/interfaces, but i've checked it all over for things like auto lo.

If it's woth anything, i've been having the same issues on both my desktop and laptop, and they both hang after the Window Manager icon shows up.  What's after that?

Thanks

---

### Post by leechin on 2006-04-07
even I am having the same problem.

everything just hangs after the login pane.

i can neither move my mouse pointer, nor does ctrl+alt+f1, ctrl+alt+f8 work.

i just have to hard reboot.

funny thing is that it happens sometimes at other times everything works just fine.

then at other times, the system hangs after i open a UI.

has anyone been able to find a solution to this?

---

### Post by adam.mech09 on 2006-05-07
Hi

Sorry that I cant help anymore.  I broke both my laptop and desktop trying to install kde, so i just did a fresh install of breezy.  Just waiting for the official release of dapper, might try again before then, but as of now both systems are running smoothly.

Sorry

-Adam

---

### Post by Jeff™ on 2006-05-13
I had the same problem, and it seemed that it was because of metacity ater deleting my ~/.metacity folder.

I solved it by hiting Alt + F2 then running gnome-session-save

It saves you whole gnome session so if you like to log in to an empty desktop you should consider to close all running programs.

---

### Post by crowdofone on 2006-06-04
had this problem after a fresh install (pxe over the network install) and seem to have solved it by doing an 'apt-get install gnome-session' and 'apt-get install gnome-panel' at the commandline

after that i could get into gnome although i was getting a few error messages and many things seemed missing. i could at least load synaptic though and from there it i noticed that ubuntu-desktop in the base system was unchecked and many of its dependencies appeared to not be installed

having now installed the ubuntu-desktop package things seem normal.

as gnome-session and gnome-panel are dependencies of ubuntu-desktop my suggestion would be to just try a 'apt-get install ubuntu-desktop' if you are having the same problem.

---

