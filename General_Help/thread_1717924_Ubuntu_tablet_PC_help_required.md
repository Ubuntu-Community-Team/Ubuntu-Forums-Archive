---
title: "Ubuntu tablet PC help required"
date: 2011-03-30
forum: General Help
---

### Post by marketgarden on 2011-03-30
Hi,

I'm a recent convert from Windows so I dont have a bloody clue what I'm doing!

Anyway the issue I seem to be having is that the tablet PC I bought is unbranded, its a problem only because it makes searching for drivers/guides IMPOSSIBLE (!).

Under windows 7 it did everything right, the mutli-touch, on screen keyboard etc was all superb but the system wasnt the fastest.

Anyway one day I had a problem with a registry file after trying to modify the log-on screen, so I booted the machine up using knoppix from a usb to get into the hard drive.

Knoppix worked great, the touch screen functions were better than windows with no futher downloads/installation required.  So after a little research I decided I wanted to install Knop as my main OS but found it impossible to install an on screen keyboard, which was pretty important as I was only ever going to have a keyboard plugged in while working with it at home.

Anyway, I did a little research and found some superb looking ubuntu touch interfaces online, so I went for that distribution of Linux.  Also I dodnt have a bloody clue how to install debian without a DVD drive or an ethernet port..

Stupidly I assumed that Ubuntu would work just as well as Knoppix in terms of utilizing the touch screen, I was wrong.  I can get it to mouse click when pressed but it doesnt move the cursor around, much less scroll down through menus etc.

Any help for dummies would be appreciated, I might not have a clue about linux but I am very good at following instructions.

If this helps at all I'm using one of these tablets---

[http://www.youtube.com/watch?v=yci6GZPw040](http://www.youtube.com/watch?v=yci6GZPw040)

Difficult to find any info on what the hardware inside is as its unbranded... if it was a DEll or Toshiba etc then I could google it.

But if Knoppix recognises the touch interface out of the USB, then surely this issue IS fixable?

...and I wont have to go back to windows :)


Edit- I have searched this site but I need a real beginners guide.

---

### Post by marketgarden on 2011-03-30
sorry for the bump, but a quick yes or no if its possible or not is all all i need.


if its a YES then ill carry on trying, if its a no then ill look into how to configure knoppix to do everythin i need :)

---

### Post by davidmohammed on 2011-03-30
tablet PC's with linux distros are fairly new - obviously you are aware that android and IPad are battling things out at the moment.

This is some community stuff you can [read]("https://help.ubuntu.com/community/TabletPC") - it has some general beginners advice.  Hopefully this will help with either ubuntu or knoppix.

As an aside - you should really try natty (11.04) which goes beta tomorrow.  It has a better interface for tablets compared to standard ubuntu.

---

### Post by marketgarden on 2011-03-30
Hey,

I think my best bet is to reinstall knoppix as it actually recognizes when i run my finger across the screen that im moving the mouse pointer.

I think itd be easier to get knoppix to give me a decent keyboard, gestures etc than it is to get ubuntu to recognize my touch screen as something other than a giant left mouse button.

As far as I understand things, knoppix is based on debian, I think I should try and figure out a way of installing that first.

It seems to be alot more complicated than anything Ive ever attempted to install on a pc, ever.

---

### Post by davidmohammed on 2011-03-30
good luck - dont forget to update this thread.  Hopefully this will help others who may try to do something similar.

---

### Post by marketgarden on 2011-03-30
Thanks.

Whatever solution I come up with I'll post, even if its 'I re-installed Windows 7'

If anybody knows an answer to this, please let me know, I'd love to stick with ubuntu but it doesnt look like I can.

---

### Post by Favux on 2011-03-30
You should enter *lsusb* in a terminal and post the output.  Hopefully the internal connection to the touchscreen is usb and the output will contain a line that describes the touchscreen OEM.

---

### Post by marketgarden on 2011-03-30
bash: /susb: No such file or directory

---

### Post by marketgarden on 2011-03-30
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 20b3:0a18  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 001 Device 005: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 001 Device 004: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



____________
so its finding my mouse and keyboard i have plugged in just now, realtek semiconductor corp?

---

### Post by marketgarden on 2011-03-30
A quick google search tells me that

Bus 003 Device 002: ID 20b3:0a18  <- is a touch screen



[http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html)

 Hanvon	20b3:0a18 < on that list


OK, thats major progress, thanks for the heads up on the commands above :)

---

### Post by Favux on 2011-03-30
OK, real progress.  We know what you have now.
```
Bus 003 Device 002: ID 20b3:0a18 
```
From:  [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)
> 20b3  Hanvon
	0a18  10.1 Touch screen overlay

and from:  [http://www.fuduntu.org/forum/viewtopic.php?f=10&t=89](http://www.fuduntu.org/forum/viewtopic.php?f=10&t=89)
> [    5.206411] usb 5-2: New USB device found, idVendor=20b3, idProduct=0a18
[    5.206421] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.206427] usb 5-2: Product: 10.1
[    5.206432] usb 5-2: Manufacturer: Hanvon     
[    5.237676] input: Hanvon      10.1  as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input6
[    5.238110] generic-usb 0003:20B3:0A18.0003: input,hidraw2: USB HID v1.11 Device [Hanvon      10.1 ] on usb-0000:00:1d.3-2/input0

So vendor ID = 20b3 = Hanvon
and product ID = 0a18 = 10.1 Touch screen (same/similar to Viewpad 10)

So now we have some keywords to search with.

---

### Post by marketgarden on 2011-03-30
Well theres bad news, bad news and bizarre news.

Bad news is that not only do they not support linux but they dont have any interest in supporting linux.

The Bizarre news is that most of the functions I want work under Knoppix :confused:

---

### Post by Favux on 2011-03-30
So some driver works.  You just have to figure out which one by searching if others have got it working.  Is it evtouch or evdev or something else?

---

### Post by marketgarden on 2011-03-30
> **Favux said:**
> So some driver works.  You just have to figure out which one by searching if others have got it working.  Is it evtouch or evdev or something else?


those two destroyed somebody elses viewpad, according to google.

is there anyway I can see whats running it via knoppix?  ive got the usb plugged in to it just now and its booted up.

im trying various gestures with it, using one finger its letting me 'left click' and is pretty responsive.

its also following my finger around the screen.

holding down my finger for a few seconds simply creates multiple 'left clicks' (maybe this isnt as suitable as i suspected), so its usable but there doesnt seem to be a right click function.

infact i just tried the on screen keyboard with it, its registering every key stroke as being multiple taps.

ill need to get my thinking cap on.  or get my windows 7 usb out again.

---

### Post by Favux on 2011-03-30
> those two destroyed somebody elses viewpad, according to google.
Drivers shouldn't be low level enough to do something like that, so I seriously doubt it.  I'd have to see the site or post.

Enter while on Knoppix in a terminal *xinput list*.  The output should give the "device name" of the touchscreen.  Then in a terminal enter:
```
xinput list-props "device name"
```
with the quotes.  The driver should be listed multiple times.  My guess is evdev.

Natty beta1 is due out tomorrow.  Natty should have more support for touchscreens.  I think they may be dropping evtouch in favor of the Synaptic touchpad driver or evdev or something.  The Ubuntu multi-touch/Utouch stack wiki has a link to a list of supported hardware.

---

### Post by marketgarden on 2011-03-30
> **Favux said:**
> Drivers shouldn't be low level enough to do something like that, so I seriously doubt it.  I'd have to see the site or post.

destroyed is perhaps too strong a word, he had to do a re-install however as everytime the user attempted to move the pointer, it was popping up in random screen positions.  for a newcomer like myself its a scenario best avoided.


I'll just have to keep a lookout for Natty Beta 1 tomorrow night.  Thanks for the help thus far Favux.

---

### Post by marketgarden on 2011-03-31
ok, downloaded and installed the new release.

lets test it out....

---

### Post by marketgarden on 2011-03-31
yep, definite improvement in terms of touch capability.

the cursor follows my finger around and recognises single left clicks, rather than a continues stream of left clicks.


as things stand thats all i have, but theres real potential here, just looking to see if i can download some applications to give me more touch gestures.

---

### Post by marketgarden on 2011-03-31
well, ive downloaded pretty much everything i could find relating to a touch interface and nothings giving me more than single left click gestures.

tbh i can live with that if i can find a way to get my virtual keyboard to stay as an icon in the task bar and increase the width of the scrollbars.

looking at all the answers on here for those issues, i dont think itll be a problem.

---

