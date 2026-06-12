---
title: "Filesystem manager goes forever"
date: 2010-07-04
forum: General Help
---

### Post by hoffmaster on 2010-07-04
Hi everyone,

I am so lost with this.

I have a shared network folder on my server called torrents.  It is a folder that I drop .torrent files into to start automatic downloading.  When I navigated there from my Ubuntu PC (10.4) I was provided a nice shortcut on my desktop.  I have no idea when the problem started but after I rebooted and logged in I noticed a "thing" on my desktop.  

torrents on peter.volume <- peter is my server name.
Places -> x-nautilus-desktop:///torrents on peter.volume <-also showing up.

I cannot delete I get The file is an unkown type.

Now if I navigate Places -> Network -> Peter (server) I can see the folder "torrents"  If I click the folder to open I get a never ending number of "starting file manager" windows.  

The other folders work just fine, its just this one.  I would love some advice.

---

### Post by lkjoel on 2010-07-04
Yeah, I have sorta the same problem, except it is with my product I made:
LinuxEssentials.
I discovered a fix for that:
First download LinuxEssentials from my sig.
Then type this when it happens:
```
killall nautilus
chmod +x FASTGNOME.sh
./FASTGNOME.sh
```

---

### Post by hoffmaster on 2010-07-04
Well I did that and it made no difference.

torrents on peter.volume is still on the desktop and I still cant delete it
x-nautilus-desktop: torrents on peter is still in Places
and lastly "Starting File Manager" fills up my bottom task bar forever.

---

### Post by hoffmaster on 2010-07-04
wow on top of that it seems my whole system is pretty much toast.

Can't run WOW on WINE, window just terminal pops up then disappears....  Whatever I did seems to have toasted this system for me :(.  Is there anyway to re-install Ubuntu without having to totally format this drive?

---

### Post by lkjoel on 2010-07-05
Yes there is, but first try:
```
sudo apt-get update
sudo apt-get upgrade
```

---

