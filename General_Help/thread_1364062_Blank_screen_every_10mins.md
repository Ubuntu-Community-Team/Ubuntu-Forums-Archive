---
title: "Blank screen every 10mins"
date: 2009-12-25
forum: General Help
---

### Post by c-m on 2009-12-25
I am running Mint 8 based on Karmic.

Everytime i watch a video in either movie player or online flash like i-player, my screen goes blank every ten minutes.

I have set my screensaver to every 120 minutes and turned off all power management, but still the problem persists.

A quick search hasn't thrown up any suggestions (its not an easy term to search for).

Any ideas?

Thanks

---

### Post by freddybob on 2009-12-27
Did you find a fix?

---

### Post by c-m on 2009-12-27
no fix. its a PITA - i've searched but haven't even found relevant threads.

---

### Post by lotharmat on 2009-12-27
please go to system --> Preferences --> screen saver

See if it is on

Sometimes the screen saver is set to be a blank screen and it will kick in if the computer is idle after 10 mins

---

### Post by lotharmat on 2009-12-27
Pants - Ignore me.

I have now fully read your original post! :redface:

---

### Post by c-m on 2010-01-14
Come on this is rediculous - Is there no fix?

Is it just in ubuntu 9.10 and Linux Mint 8 or other distros based on debian and gnome?

I don't want to have to live with this for the rest of my life

---

### Post by sisco311 on 2010-01-14
create a new Startup Application (System -> Preferences).
in the command field type: 
```
xset -dpms && xset s off
```

---

### Post by c-m on 2010-01-14
Thanks for the help - will try it

---

### Post by sisco311 on 2010-01-14
> **c-m said:**
> Thanks for the help - will try it

You are welcome!

If you still encounter problems, try [caffeine]("http://www.blastfromthepast.se/caffeine/index.php?title=Main_Page").

---

### Post by c-m on 2010-01-19
Aww man - that didn't work - still the same problem every 10mins

TBH i'm not sure the items in my startup in (System -> Preferences are actually starting.

The reason i say that is because i have nm-applet in there and i know for a fact that it isn't starting.

---

### Post by Ahriman on 2010-01-19
Could it be something with your monitor or BIOS? Sometimes there are options to enter low power states in the BIOS (more common) and the monitors themselves (less common).

---

### Post by c-m on 2010-01-19
nah - its only in linux doesn't happen in windows at all. i have run that code above manually into the terminal and it seems to have done the trick but i guess i need some kind of script to run it at boot?

---

### Post by sisco311 on 2010-01-19
> **c-m said:**
> Aww man - that didn't work - still the same problem every 10mins

TBH i'm not sure the items in my startup in (System -> Preferences are actually starting.

The reason i say that is because i have nm-applet in there and i know for a fact that it isn't starting.

what's the output of:
```
xset q
```
?

---

### Post by scouser73 on 2010-01-19
It sounds as if you may need a program called Caffeine.

[[COLOR="Red"]**Launchpad PPA for Caffeine**[/COLOR]]("https://launchpad.net/~caffeine-developers/+archive/ppa")

**1** - Click [B]Technical Details about this PPA
[/B]
**2** - Click on the **Choose your Ubuntu version** drop-down menu

**3** - Go to **Administration** > **Software Sources**

**4** - Enter your password

**5** - Click the **Other Software** tab

**6** - Click **Add**


[COLOR="Red"]**If you are using Ubuntu 9.04, then copy the following two lines**[/COLOR]

**7** - > **deb [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) jaunty main**

**8** - > **deb-src [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) jaunty main**

[COLOR="Red"]**If you are using Ubuntu 9.10, then copy the following two lines**[/COLOR]

> **deb [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) karmic main**

> **deb-src [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) karmic main**

**9** - Click **Close**, then click **Reload**

**10** - Open Terminal, copy & paste this command 
> **sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 569113AE**

**11** - Copy & paste this command > **sudo apt-get update**

**12** - Go to Administration > Synaptic Package Manager and enter **caffeine** in the search field & right click **Mark For Installation**

**13** - Click **Apply** & then click **Apply** again

Caffiene will now be installed & will be in the **Accessories** menu

Click on Caffeine, the program will then launch, you will now see a small Coffee cup icon in the system tray, right click and set the time for the monitor to stay in wake mode.

The longest that Caffeine can be set for is 168 hours & 59 minutes

---

### Post by sisco311 on 2010-01-19
@scouser73

Linux Mint 8 it's based on Ubuntu 9.10


to install caffeine, you can simply run:
```
sudo add-apt-repository ppa:caffeine-developers/ppa
sudo apt-get update
sudo apt-get install caffeine
```

---

### Post by scouser73 on 2010-01-19
The advice that sisco311 is the fastest option actually, lol.

---

### Post by c-m on 2010-01-19
```
carl@desktop ~ $ xset -dpms && xset s off
carl@desktop ~ $ xset q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00001002
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  0    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 1200    Suspend: 1800    Off: 2400
  DPMS is Disabled

```

Doesn't look like i can follow that for caffiene on Mint

```
   
W: Failed to fetch http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/helena/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Cardale on 2010-01-19
Power options for the monitor?

---

### Post by sisco311 on 2010-01-19
> **c-m said:**
> 
Doesn't look like i can follow that for caffiene on Mint

```
   
W: Failed to fetch http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/helena/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

D'oh! Replace helena with karmic in the /etc/apt/sources.list.d/caffeine-developers-ppa-*.list file.

---

### Post by Ahriman on 2010-01-19
> Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  600

Now, I'm no expert or anything, but that cycle: 600 looks suspiscious to me. 600 seconds = 10 minutes ... are you sure the screensaver time is set higher?

---

### Post by sisco311 on 2010-01-19
> **Ahriman said:**
> Now, I'm no expert or anything, but that cycle: 600 looks suspiscious to me. 600 seconds = 10 minutes ... are you sure the screensaver time is set higher?

The screensaver is disabled, the timeout is set to 0. 

timeout determines how long the X server must be inactive for screen saving to activate. 0 means never activate.

cycle is the  period  to change  the background pattern to avoid burn in.

---

### Post by c-m on 2010-01-19
> **Ahriman said:**
> Now, I'm no expert or anything, but that cycle: 600 looks suspiscious to me. 600 seconds = 10 minutes ... are you sure the screensaver time is set higher?

screensaver is set to 2 hours

---

### Post by c-m on 2010-01-19
installed caffeine. Not sure whats next though.

```
 carl@desktop ~ $ caffeine

(19 Jan 2010) 22:00:15 INFO:  User has clicked the Caffeine icon
(19 Jan 2010) 22:00:15 INFO:  Attempting to detect screensaver/powersaving type... (0 dbus failures so far)
(19 Jan 2010) 22:00:30 INFO:  Attempting to detect screensaver/powersaving type... (1 dbus failures so far)
(19 Jan 2010) 22:00:45 INFO:  Attempting to detect screensaver/powersaving type... (2 dbus failures so far)
  
```

---

### Post by DayLite on 2010-10-04
The 'coffee cup' was launched from Applications> Accessories.
It is now on the top panel. It **does not **have a timer! When I click on it, gives the option to disable screen saver. Under preferences, is no mention of a timer.

---

### Post by c-m on 2010-10-04
I gave up and just resinatlled a more upto date version - works fine.

---

### Post by DayLite on 2010-10-04
> **c-m said:**
> I gave up and just resinatlled a more upto date version - works fine.
My version is 2.0+280~lucid1

---

### Post by Supergibbon on 2011-06-17
In terminal:

$ gconf-editor

Go to:  Apps>Gnome-Screensaver and change idle-delay time.

---

### Post by evanct on 2011-06-17
I had this exact problem until today. The problem is with gnome-screensaver, all you have to do is replace it with xscreensaver.

[http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557)

---

### Post by Supergibbon on 2011-06-17
I lie.  I still got a blank screen, but changing the settings in Apps>Power-Management after running $gconfig-editor seems to have done it.

---

