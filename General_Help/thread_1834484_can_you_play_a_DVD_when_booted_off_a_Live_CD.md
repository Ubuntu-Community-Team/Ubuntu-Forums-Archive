---
title: "can you play a DVD when booted off a Live CD?"
date: 2011-08-27
forum: General Help
---

### Post by sdowney717 on 2011-08-27
Want to test the DVD player on a laptop.

edit, you can do this by using a live USB

---

### Post by sam_delta on 2011-08-27
i believe not, i might be wrong tho.

you could always put ubuntu into a usb and boot a live usb (its pretty easy)
or you could extract an image of the dvd into a usb and play it in your cd live session

sam

---

### Post by snowpine on 2011-08-27
Yes! :)

You will need to install the codecs as explained here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

And obviously you will need 2 CD/DVD drives (one for the Ubuntu Live CD and one for your DVD). ;)

---

### Post by sdowney717 on 2011-08-27
her laptop is running XP and has issues when trying a play a DVD. I have power DVD working but the playback constantly stops and starts jerkily.
The laptop can play flash well like HULU.
so I was wondering if ubuntu could play it ok. 
BUT, I only have one dvd drive

---

### Post by sdowney717 on 2011-08-27
how about this. boot off cd drive running plop, then tell it to boot the liveCD off the usb?
do you just copy the live CD onto the USB?
Likely that is where I will make the mistake.
format then copy or special commands required, etc...
[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

---

### Post by snowpine on 2011-08-27
How to run Ubuntu from a Live USB: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by sdowney717 on 2011-08-27
yes, that works if the laptop lets you boot a USB stick, I think her's does not. Even so it is a core 2 duo with 4gb from toshiba.

so doing the plop method, do you just copy the live cd to the blank usb drive?

---

### Post by sdowney717 on 2011-08-27
its always something now got this error so it wont copy the live cd onto the usb!
so how to fix this new problem?

---

### Post by sdowney717 on 2011-08-27
here is filesystem for the usb after it copied most of it with error, says it is ms dos filesystem. does this mean the usb drive must be reformated?
then will it work with windows?

---

### Post by snowpine on 2011-08-27
No, you cannot make an Ubuntu Live USB by simply copying the files to a USB stick.

[Follow this guide]("http://www.ubuntu.com/download/ubuntu/download") carefully step-by-step, if you get stuck, tell us specifically which steps you have tried so far and which step you're stuck at. :)

---

### Post by jwbrase on 2011-08-27
I don't think Ubuntu can play a DVD in a live CD environment without 2 drives, but there are some Live CD Linux distros that can move everything they need into RAM, which would free up the DVD drive. 

Puppy Linux, for example, seems to include libdvdcss, so you might want to try that.

---

### Post by sdowney717 on 2011-08-27
first time ever booting off a live usb and it works on this laptop.
surprise! now just need to configure the dvd player

---

### Post by sdowney717 on 2011-08-27
uh, how to start a terminal window with ubiquity?

i am used to menus at top so cant show you what is going on now.
i tried alt f2 run synaptic but libdvdread4 comes up blank

i have no idea how to open a terminal window with the menus at the left 

   Install the libdvdread4 package (no need to add third party repositories) via Synaptic or command line: 

sudo apt-get install libdvdread4

    Then open a terminal window and execute: 

sudo /usr/share/doc/libdvdread4/install-css.sh

---

### Post by snowpine on 2011-08-27
> **sdowney717 said:**
> uh, how to start a terminal window with ubiquity?



I assume you mean Unity? Ctrl+Alt+T I think.

[http://www.ubuntugeek.com/list-of-ubuntu-unity-keyboard-shortcuts.html](http://www.ubuntugeek.com/list-of-ubuntu-unity-keyboard-shortcuts.html)

You can launch any application by pressing the Windows/Super key and typing its name.

You can also choose "Classic" mode from the login screen if you prefer the old interface.

HOWEVER you may find the easiest way to install an app is using the Ubuntu Software Center; everything is available with just a few clicks of the mouse. :)

---

### Post by sdowney717 on 2011-08-27
ubuntu@ubuntu:~$ sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libdvdread4
ubuntu@ubuntu:~$ 

does not exist so instructions dont tell you add repository?

> Install the libdvdread4 package (no need to add third party repositories) via Synaptic or command line: 

---

### Post by snowpine on 2011-08-27
Try this first:

```
sudo apt-get update
```

Looks like they left this step out of the how-to. :)

---

### Post by sdowney717 on 2011-08-27
well I added the universe repo using synaptic and reload and installed vlc.
So it plays DVD ok unlike XP which has a terrible unexplainable periodic fast glitch.

Thanks for posting the info.

So you can boot the usb live and play dvd's.

I think she just has the intel video chip builtin. Does this work now with s video output? She has an s video port.

totem player wont play the disk gave an error so tried vlc and it plays, go figure.
totem wanted to search for plugin, said ok, then came back no suitable plugins found

---

