---
title: "unable to mount ipod unhandled lockdown error (-4)"
date: 2011-11-25
forum: General Help
---

### Post by 4soul on 2011-11-25
Hi since I've been at this for days without much progress; I've finally decided to start a thread. So far this is what I've done (and the best link I've found on this error (-4)...> I've installed and attempted to use both Amorak, and GTKPOD Ipod manager with the same "....error (-4)" message;
[QUOTE]Also libimobiledevice-utils is up to date
[IMG]http://i1125.photobucket.com/albums/l598/Dahlsim/Screenshot-1-1.png[/IMG][/QUOTE]

[IMG]http://i1125.photobucket.com/albums/l598/Dahlsim/Screenshot-2.png[/IMG]

---

### Post by 4soul on 2011-11-25
I'm having issues with screen shots and typing so I'm posting the next part separately. 

I found this page which has proved the most promising...

[http://geeknizer.com/sync-iphone-linux/](http://geeknizer.com/sync-iphone-linux/)

At step two of the instructions there was code which [COLOR=#000000]I adjusted according to terminal suggestions  of replacement packages (as some weren't found and thereby ended up  putting this into terminal: I figured the code was written for iphone..[/COLOR]

Code:
sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse  libgvfscommon0 ifuse libgpod-dev libgpod-common libiphone-utils  libiphone0 python-iphone libplist++1 libplist-utils python-plist  libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd[LEFT][COLOR=#000000]
Code: 
sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod-dev libgpod-common libimobiledevice-utils libimobiledevice0 python-imobiledevice libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd


... seemed to work perfectly until the end: user/bin/dpkg returned an error code (1)

[IMG]http://i1125.photobucket.com/albums/l598/Dahlsim/Screenshot-2-1.png[/IMG]

Now I have a circular ERROR/Update button at the top right of my screen which when clicked tells me I have unmet dependencies, offers updates which I tried to install but returned this 'broken packages' message and suggests running code which I tried to run but gives me message: "open (13 permission denied)...

[IMG]http://i1125.photobucket.com/albums/l598/Dahlsim/Screenshot-4.png[/IMG]



[/COLOR][/LEFT]

---

### Post by 4soul on 2011-11-25
I tried to install the updates again today and got another broken package message

[IMG]http://i1125.photobucket.com/albums/l598/Dahlsim/Screenshot-6.png[/IMG]

I went to synaptic package manager and used the broken filter to find it was libimobiledevice-utils so I completely removed it and went back to terminal to reinstall it, and I get the same ".... user/bin/dpkg error code (1)"

[IMG]http://i1125.photobucket.com/albums/l598/Dahlsim/Screenshot-7.png[/IMG]

---

### Post by rrice on 2011-12-05
Ubuntu 10.10, iphone 4 with OS 5.0.1, installed imobiledevice-utils but still get "unable to mount xxx iphone unhandled lockdown error (-4)

---

### Post by londonbabs on 2011-12-27
same exact problem here, no easy fix yet ?
There seems to be patches for this but did anyone worked them out or could explain how to apply them in a very noob way ?
I know I can't apply them or am wary of messing up my system, anyone with a little help ?

iphone 4S on Ubuntu 10.10 Maverick

EDIT: I just went ahead and installed virtualbox with a windows XP guest and it all works like a charm, still getting the error from ubuntu but once all packages are installed and usb enabled on the virtualbox it couldn't be easier, I'll use that until they update libimobile

---

