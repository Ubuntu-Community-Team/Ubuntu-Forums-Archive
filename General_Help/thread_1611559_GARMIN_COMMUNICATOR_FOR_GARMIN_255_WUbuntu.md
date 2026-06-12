---
title: "GARMIN COMMUNICATOR FOR GARMIN 255 W/Ubuntu"
date: 2010-11-02
forum: General Help
---

### Post by gdiloren on 2010-11-02
My last problem with Ubuntu. I fixed all others! Garmin Communicator isn't available for Linux OS. So I installed wine, I installed the windows version of Firefox 3.6.12 and it still can't detect my GPS. So I'm stuck there. If I ever want to install maps on my Garmin 255W I will need it to work on Linux or at least Wine. I'm awaiting a solution from their support too...!!!

---

### Post by vsh3r on 2010-11-02
Linux support is probability coming soon.  Garmin online updater does work on OSX.

V$H.
:mad:

---

### Post by gdiloren on 2010-11-03
In Wine, I installed Firefox 3.6.12 for Windows and the Garmin Communicator plugin is installed from the Garmin Web site but it doesn't "see" the GPS when connected to the USB port because the USB port is in Ubuntu 10.10. At this point, I wonder if trying Virtual Box would work... Garmin support officially contacted me telling me crudely it doesn't support Linux, at least for the moment. I'm left with the option of using my sister's computer on Windows for future maps uploads!!!

---

### Post by Spynexes on 2010-11-04
You might want to try:
[http://www.andreas-diesner.de/garminplugin/](http://www.andreas-diesner.de/garminplugin/)

```
sudo add-apt-repository ppa:andreas-diesner/garminplugin
sudo apt-get update
sudo apt-get install garminplugin
```As far as I know your Garmin nüvi 255 is a file based device, so you should easily get it running.
Maybe the author will also implement auto detect for your device. 

What do you need the Garmin Communicator Plugin for when doing map upload? Does it even support map upload? 

~Spynexes

---

### Post by gdiloren on 2010-11-04
> **Spynexes said:**
> You might want to try:
[http://www.andreas-diesner.de/garminplugin/](http://www.andreas-diesner.de/garminplugin/)

```
sudo add-apt-repository ppa:andreas-diesner/garminplugin
sudo apt-get update
sudo apt-get install garminplugin
```As far as I know your Garmin nüvi 255 is a file based device, so you should easily get it running.
Maybe the author will also implement auto detect for your device. 

What do you need the Garmin Communicator Plugin for when doing map upload? Does it even support map upload? 

~Spynexes
It happens only once a 2 or 3 years I would have to upload new maps, I tried switcher agent but still doesn't work. I guess I'll wait until Ubuntu finds something about it.:)

---

