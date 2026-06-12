---
title: "Automatically connecting to various wireless networks?"
date: 2006-03-28
forum: General Help
---

### Post by Kaneda on 2006-03-28
Hi, sorry to post another wireless question, but I searched through the forums and couldn't find an answer to my problem.

So, here's some background information:  I'm very new to Linux--I just installed Breezy Ubuntu 5.10 last week.
My wireless card is an Intel PRO/Wireless 2200, which was automatically detected while installing Ubuntu, so there are no problems with drivers or anything like that.
In fact, I don't have any problems connecting to the internet using wireless, I just have a question:

Is there any way to set up your wireless settings to automatically detect the wireless networks in the area, and then connect to your preferred network using the appropriate WEP key?  For example, I travel between my house, school, and friends' houses with my laptop, and each of these places has a different wireless network with a different WEP key (or none at all), and I find myself having to go in and manually reset the WEP key depending on where I go.  Also, is there any way to see what wireless connections are available?

(I would appreciate information on how to do this in both GNOME and through the unix terminal)

Thanks!

---

### Post by Dafydd on 2006-03-28
[QUOTE=Kaneda]Also, is there any way to see what wireless connections are available?
(I would appreciate information on how to do this in both GNOME and through the unix terminal)[/QUOTE]

Try NetworkManager.  Do:  

sudo apt-get install network-manager


Someone suggested this to me a couple of days ago (thanks!). It's sort of working. Maybe it'll work for you. 

best
dafydd

---

### Post by Kaneda on 2006-03-28
Thanks!

---

### Post by anders.ostling on 2006-03-28
dont forget to install the nm-applet package too (if not included). You need to run the nm-applet from the command line. It will put itself in the system tray, and you choose "Other wireless network" to connect to a new wlan. Enter the wep key once and it will remember the settings. You need to do this for each new wlan. If the network is not using "simple" WEP, it becomes a little more complicated. Look for wpasupplicant documentation ...

Anders

---

### Post by seppo on 2006-03-28
I haven't played with it yet, but it sounds promising. 

Right now i'm using a simple parameter that grub passes tot rcS.d to make the right symbolic links to the right network configuration files

It is kind of ugly, but works perfectly if you travel between locations, provided that you reboot between those locations:

[http://www.atworkonline.it/~bibe/breezy/index.htm]("http://www.atworkonline.it/%7Ebibe/breezy/index.htm") (section netprofile)

---

### Post by Dafydd on 2006-03-28
just got home and needed to check sth on the net. D*** ubuntu wouldn't let me.

At the work network, I tried to get an ip etc but to no avail. Ended up using Puppy. Back at home, I need to reenter the dns servers and then reboot twice. Somehow doing  sudo /etc/init.d/networking restart doesn't work...

There must be an easier way.

Also I've got the dhcp script dns nameserver renewal thing commented out. Could that be part of the problem?

If it's not commented out then gaim will tme out...i

All strange and too complicated for me.

Now I'm on the net but the nm-applet is not working...

Why all this fiddling...

dafydd

---

### Post by Kaneda on 2006-03-28
Okay, a related question:

I tried to sudo apt-get install network-manager, and I got a long list of errors along these lines:

W: Couldn't stat source package list [http://mirrors.physics.byu.edu](http://mirrors.physics.byu.edu) breezy/main Packages (/var/lib/apt/lists/mirrors.physics.byu.edu_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)

It looks like it's trying to get the files from the school server that I got some files from when I originally installed ubuntu.  How do I set it in the right direction?

---

### Post by ronmarley1 on 2006-03-28
Wifi-radar will manage multiple wireless networks for you nicely.  I have one at home using WEP and another at school that's open.  Once I set up a profile for each, Ubuntu connects at boot with no problem.  Wifi-radar is in the repos.

---

