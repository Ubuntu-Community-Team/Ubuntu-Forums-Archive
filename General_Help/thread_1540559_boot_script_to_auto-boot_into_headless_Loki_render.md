---
title: "boot script to auto-boot into headless Loki render?"
date: 2010-07-28
forum: General Help
---

### Post by MessyMoose on 2010-07-28
Hi everyone
 
 I'm fairly new to linux but have found lots of good advice online to  help me set up my home render farm for blender. I've gotten hold of 3  old pc's that I've installed with Jaunty & use Loki as a quick and  dirty render farm manager. 
 
 I've got one display between them and so i can check that each one works on its own as a 'grunt' of the 'master' (my main pc).
 
 To get the grunt to work I have to log in to a cli (to save on ram),
 start nm-applet (the only way the wireless cards work at mo)
 & start Loki in grunt mode. All whilst connected to a display. 
 
 I'd like to learn how to script all this so I can simply switch the pc's  on without needing to use a display. Do i need a boot script and how  does that work?

How do I set them to auto log in to command prompt?
 
 grateful for any help, thanks.

---

### Post by squaregoldfish on 2010-07-28
This is going to sound like spam, but it genuinely isn't - I just don't want to go through reproducing stuff here that I've written elsewhere.

I recently wrote some notes on getting wireless networking to work on a headless Linux box: [http://www.squaregoldfish.co.uk/2010/03/11/a-wireless-headless-linux-box/](http://www.squaregoldfish.co.uk/2010/03/11/a-wireless-headless-linux-box/)

As for getting Loki to start automatically, it's simply a matter of adding the loki command line to /etc/rc.local (with a trailing & character):
```

java -jar lokiRender_062.jar blender &
```

This should start up the loki grunt when the machine boots.

Hope this helps
Steve.

---

### Post by MessyMoose on 2010-07-28
Thank you squaregoldfish, very informative.
I've been busy trying your suggestions.
For my future benefit and others I will layout my steps so far:

First removing nm-applet
```

$ sudo apt-get remove network-manager network-manager-gnome
```then checking wpasupplicant is installed
```

$ sudo apt-get install wpasupplicant
```then editted the file
/etc/network/interfaces
```

$ sudo gedit /etc/network/interfaces
```Which didn't like wlan0.
$ ifconfig -a
listed all the network cards and mine was ra0, so replaced every 'wlan0' with a 'ra0' in /etc/network/interfaces to look like:
```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp

wpa-ap-scan 1
pre-up sudo /sbin/wpa_supplicant -ira0 -c/etc/wpa_supplicant.conf -Dwext -B
pre-up sleep 5
post-down sudo killall -q wpa_supplicant
```That saved I went on to edit /etc/wpa_supplicant.conf 
```

$ sudo gedit /etc/wpa_supplicant.conf
```And made it look like the following (the texts <your_router_SSID> & <security_passkey> have been changed to protect the guilty.
```

ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="<your_router_SSID>"
    psk="<security_passkey>"
    proto=RSN WPA
    key_mgmt=WPA-PSK
    pairwise=CCMP TKIP
}
```That's taken me a couple of days, so now I'm on to the next part :D auto login to shell without loading X / gnome 

thanks hugely

---

### Post by MessyMoose on 2010-07-28
tried to edit /etc/rc.local as follows
```

java -jar lokiRender_062.jar /usr/bin/blender &

exit 0
```but to no avail.

Also tried to auto log in using Gnomes menu
>> SYSTEM >ADMINISTRATION >LOGIN WINDOW
>Security TAB >enable Automatic login >User = my_username
>General TAB >Default Session = Failsafe Terminal

this also didn't quite work, it auto logged in to gnome desktop, not what i was after. Still didn't auto run Loki either.

Any suggestions would help, thanks

---

### Post by squaregoldfish on 2010-07-29
In the rc.local file, it's unlikely that the system will know the path to the loki jar file, so you'll probably have to put the full path in.

Steve.

---

### Post by MessyMoose on 2010-07-29
Thanks Steve, you've been very helpful. 

I've changed rc.local to read as follows 
```

java -jar /home/my_username/lokiRender_062.jar /usr/bin/blender &
```but still no joy.

however, the network is up and running :)

The last two remaining probs are 
1. starting in shell prompt 
2. getting Loki loaded in grunt mode

all without any intervention on my part. I'll keep searching for answers but any advice would be appreciated.

---

### Post by MessyMoose on 2010-08-10
This will have to be put on a back burner as I get on with other things,
maybe worth considering a distro without a windows manager.

Ho hum, try again when I got time.
Thanks again.

---

