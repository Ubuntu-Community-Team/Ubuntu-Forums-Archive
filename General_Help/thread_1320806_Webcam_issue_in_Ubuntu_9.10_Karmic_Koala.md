---
title: "Webcam issue in Ubuntu 9.10 Karmic Koala"
date: 2009-11-09
forum: General Help
---

### Post by thanjaa on 2009-11-09
Hi Guys,
               
Very recently I switched to ubuntu 9.10 from Ubuntu 8.04. I experience the following problem.

From the "Suspend" state, whenever I try to log in to my Laptop, my laptop's inbuilt webcam light is getting lit. And thru skype I cannot access my webcam. It says no video device.

When I shutdown and restart my laptop everythin becomes quite normal. Any idea what the problem would be? Thanks in advance.

Laptop Model: HP Compaq C765TU

---

### Post by Morrighan on 2010-04-16
I have almost identical problem with my Lenovo U110 laptop. Except the camera never works (not in cheese or skype) and I couldn't find any solution yet. Can somebody help please?

---

### Post by no2498 on 2010-04-16
Morrighan

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

you can try cheese but if it breaks the cam
you need to do this again

and try it with this program wxcam
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)
getdeb also has it

for skype you need to ask a skype ?

hope this helps

---

### Post by Morrighan on 2010-04-17
> **no2498 said:**
> Morrighan

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

you can try cheese but if it breaks the cam
you need to do this again

and try it with this program wxcam
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)
getdeb also has it

for skype you need to ask a skype ?

hope this helps
Thanks!
I tried the gstreamer-properties, when I click test it turns on the LED and remains "testing" until I click OK. If I switch to the v4l1 it doesn't work at all. I ran lsusb (seems like standard advice), and as far as I could tell, it detects the camera.

For some reason I couldn't get wxcam installed :confused: (I'm still new to Ubuntu). But I don't think it's just skype or cheese related issue, the camera does act funny when I turn on the computer from hibernate mode.

I did some snooping around the directories, and it seems like Ubuntu (or linux?) recognizes my computer as Asus when in fact it's Lenovo. Just thought I mentioned it.

---

### Post by no2498 on 2010-04-17
have seen a few that need to restart after hibernate mode
i have never had my hands on a lap top

did you try the getdeb.net
[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)
as a mater of fact its in the synaptic package manager 910 and up
it should load

now that v4l1 and v4l2 are the same file you may need to do the skype thing

this is not it
v4l1 so skype or cheese or wxcam
just trying to help point you the right way

---

### Post by Morrighan on 2010-04-19
I'm not sure I follow, did I say that I'm VERY NEW to ubuntu? :oops:

One thing though - I probably assumed that it detects and lists the camera in the USB list (it had one with synaptic something, so I was pretty sure it's the camera). I just turned the laptop on from Suspend mode, the camera LED was switched on as always, but when I run lsusb, this is the output:
 ```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0b05:1759 ASUSTek Computer, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
No webcam in sight.

---

### Post by no2498 on 2010-04-19
lsusb will tell you something
i can not help you with skype it is diff
than just getting the cam on
look in the add /remove
see if you have the good bad and ugly installed gstreamer

---

### Post by oblocutor on 2010-12-03
@Morrighan: 
I  have a Lenovo U110 as well. I've been running Linux Mint on it for a while and figured that there was never going to be a way for me to run the webcam...but I just found the solution and wanted to share. 

I'm running 10.10 Maverick. There are instructions listed [here]("http://art.ubuntuforums.org/showthread.php?t=1125192") that offer different instructions (presumably for 10.04) but they didn't work for me.

What did work was pretty simple, though. 
To test:
```

# sudo rmmod uvcvideo
# sudo modprobe uvcvideo quirks=16
```

Then fire up Cheese, Skype, or test right from the terminal with:
```

mplayer -fps 15 tv://
```

If that works for you, then celebrate. :D When you're finished celebrating, make the changes permanent via:
```

gksudo gedit /etc/modprobe.d/uvcvideo.conf
```
Where you'll enter the following:
```

options uvcvideo quirks=16
```
Save the file and you should be good to go.

Disclaimer: I haven't restarted yet. I believe that the uvcvideo.conf modprobe syntax is correct, but I'll believe it when I see it. 

Enjoy! I hope that works for you.

---

### Post by ande_dong on 2011-01-25
dear oblocutor

I followed your method and it works for me!

im using a lenovo K13 machine, and it has the same lsusb info:
Bus 003 Device 002: ID 0b05:1759 ASUSTek Computer, Inc.

thanks alot! :p

---

### Post by oblocutor on 2011-02-10
@andre_dong:

I'm glad I could help!

For anyone having trouble with the webcam light staying on after waking from sleep, here's the fix:

```
gksudo gedit /etc/pm/sleep.d/99-uvc-webcam-reset
```

Then input:


```
#!/bin/bash

case "$1" in
    thaw|resume)
        rmmod uvcvideo; sleep 2; modprobe uvcvideo
        ;;
    *)
        ;;
esac
exit $?

```

Save the file, and the webcam light will turn off a few seconds after resuming from suspend-to-RAM.

---

### Post by langmarp on 2011-04-29
hi

this worked for me with 10.10, but do you have experience with 11.04?

Thank!

---

