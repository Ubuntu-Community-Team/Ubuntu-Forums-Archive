---
title: "Bayer Contour / Glucofacts"
date: 2009-11-07
forum: General Help
---

### Post by Olav on 2009-11-07
Hi,

Bayer, the well known pharmaceutical company is giving away free "Contour" glucose meters for diabetics to check their own blood sugar levels. Or at least in my country they are. Also for free, postage included, is a USB data cable to connect the glucose meter to your computer. Of course they don't give away these things out of the goodness of their heart, they hope you will buy the (expensive) needles and test strips you need to actually use their glucose meter. Only 10 of each of these are included in the free starter set.

Anyway, their application "Glucofacts" which is a Java program works well in Windows, of course, but not so well in Ubuntu Linux. It installs fine (though Java Web Start) and runs without errors, I can access all menus and get a good idea of the program. But ultimately it remains unable to find a serial port to which the glucose meter is connected.

The USB cable has a little square box (that presumably contains some magic) near the USB connector and a 3.5 mm "stereo" jack plug on the other end. When plugged into the computer it automatically installs a serial device in Linux called /dev/ttyUSB0. I have added my user account to the "dialout" group which has read and write privileges on the device. But the Glucofacts program just doesn't pick up the presence of the virtual serial port.

Any ideas? This may not even be too difficult but I feel quite stupid today... :oops:

I don't even care much for this particular application, I would much rather be able to download the data from the glucose meter myself and process it in a spreadsheet. But where do I start if I would want to reverse engineer the communication they use with the device? A simple "cat /dev/ttyUSB0" turns up nothing. I suppose they have a special communications protocol or something.

[IMG]http://img260.imageshack.us/img260/508/contourglucosemeterblau.jpg[/IMG]

---

### Post by julianb on 2009-11-07
Is there a way to try the program out as running-under-WINE program? Maybe the problem will be the same though.

If you have easy access to a dual-boot or windows-only computer (maybe a mac too?) then you could just take the easy way out. 

Well, I like to do things the easy way, anyway.

---

### Post by cariboo on 2009-11-07
A lot of those devices have a cable that converst from serial to usb, they need a driver. Plug the device in, then open a terminal and type:

```
lsusb
```

The result should look something like this:

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 002 Device 004: ID 045e:074f Microsoft Corp. 
Bus 002 Device 003: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 002: ID 0665:5161  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

find the id number of the device, then do a search to see if there is a driver for it.

---

### Post by Olav on 2009-11-07
Julianb, thank you for your reply. If I were to run the program under Wine I would also have to install the Java JRE into Wine. I am thinking, somehow, this is going to be ridiculous... ;) I already have Sun Java JDK + JRE installed in Ubuntu. Any program running on that should be "platform independent", no?

I have Windows XP running in VirtualBox so if I would really NEED to use this program I would be able to do so.

However I just decided that I don't even need any communication with the device at all. I'm only a Type 2 diabetic so it's not like I need to measure my glucose six times a day. More like four times a week, just to be sure. So I'll take a note the old fashioned way, with pen and paper.

Still as a Linux user it bugs me somewhat that such a thing would not work and that Bayer does not support our favourite operating system.

It would be a nice challenge to try to hack into this little gadget. But it's Saturday evening here and I have done enough for the week, feel a bit tired and don't know where to start...

---

### Post by Olav on 2009-11-07
Cariboo907, thank you also for your reply. But like I said, perhaps not clearly enough, the USB/serial cable is recognised (if that tells you anything, it has ID 1a79:6001), a driver is present, and a device node was automatically created in /dev even before I did anything else. So that is good, and for this reason I suspect the problem to reside in the application, not in the hardware or drivers. I think it may be looking for things called COM1:, COM2: and such...

Since I have the thing working in VirtualBox I start to wonder if there are ways to "eavesdrop" on a serial connection in Windows. That would perhaps give some insight into their data protocol.

---

### Post by Olav on 2009-11-07
> **Olav said:**
> Since I have the thing working in VirtualBox I start to wonder if there are ways to "eavesdrop" on a serial connection in Windows. That would perhaps give some insight into their data protocol.
To answer my own post partially, I found a freeware "serial port monitor" for Windows that lets me follow the conversations between the Glucofacts application and the Contour device. Interesting! I can see the blood sugar measurements I took, with timestamps, fly by in plain text. I need to analyse this a bit further, then perhaps I am able to make a script in Ubuntu that does the same. Anyone else interested? It's not going to happen tonight though, I think I'm going to turn off my computer now and watch a movie instead.

:popcorn:

---

### Post by jconnolly on 2009-11-19
I'm beginnging to do some work with linux and the bayer glucometer and USB cable.  I'll let you know my results, but some suggestions on using it...

If the serial device is recognized and you get a tty device, try using od or simply cat on the the device node to see what kind of data you see streaming in.  I'll check back in once I've received my USB cables.

---

### Post by jconnolly on 2009-11-23
> **Olav said:**
> When plugged into the computer it automatically installs a serial device in Linux called /dev/ttyUSB0. 

Hi Olav, you're able to see /dev/ttyUSB0?  can you uname -a and udevinfo -a -p $(udevinfo -q path -n /dev/ttyUSB0 ?  I don't see a device node with the identical hw.

Thanks!

---

### Post by __j__ on 2009-12-01
For what it's worth, getting results from the Contour using the serial connector is pretty straightforward:
[LIST=1]
[*]When you plug the meter in and press the "M" button, the device will send an ENQ (ASCII code 5) to signal that's it's listening.
[*]You reply with an ACK (ASCII code 6), saying "send me the next record."
[*]The device will send you a record. To signal you received it and want the next one, send another ACK.
[*]Repeat until you've exhausted all the records.
[/LIST]
The first record you get will be a header of sorts. The next 2 are misc information. Everything after that are glucose measurement records (or control solution).

You can check this out easily using a serial terminal like cutecom:
```
sudo apt-get install cutecom
```
Open /dev/ttyUSB0, set the input mode to hex, and just keep sending "6".

Once you've seen what the record format looks like, script to your liking in your favorite language.

Good luck!

---

### Post by jconnolly on 2009-12-04
> **jconnolly said:**
> Hi Olav, you're able to see /dev/ttyUSB0?  can you uname -a and udevinfo -a -p $(udevinfo -q path -n /dev/ttyUSB0 ?  I don't see a device node with the identical hw.

Thanks!

I got it... I needed to recompile ftdi_sio.c with a patch for bayer support.  [http://patchwork.kernel.org/patch/41191/](http://patchwork.kernel.org/patch/41191/)

---

### Post by Foub on 2010-01-10
Hum... and how do you do to get the configuration used by the glucometer (sound level, time format, date format) ?

Thanks a lot,
F.

---

### Post by nhb on 2010-02-08
Hi
I've just started using ubuntu, but I love it.
The Bayer glucofacts Express is almost working when you install it (after installing Java).

All the menus seems to be working. That seems to be missing is the ability to detect the meter or rather the ports.
The cable is using one of the com ports.

Do anyone know how to make these ports visible?
Otherwise I would like to of other types of software to use.
Also I would like to contribute with some coding and/or testing if necessacery.

I hate going back to windows.

Regards/nhb

---

### Post by bgeddy on 2010-02-11
Hey Guys,
I was just wondering if any of you have made any progress with this. I have a Bayer Contour and have recently got the USB cable attachment. I have also downloaded the Glucofacts software but I have to run Windows for that. Even then it won't recognize the meter and no amount of setting up seems to fix this. The host system is Vista and I really hate having to return to Windows while I am trying to get this working. So if anyone has made any further progress in accessing the device in Linux please let me know. (Actually accessing it just from Windows would be a start !)
Thanks

---

### Post by fflakey on 2010-06-17
Hi All

I'm a software development engineer and my daughters a Type 1

I've just been having a look at this godawful Glucofacts Deluxe software V2.07

I've got it starting to run under Java/Linux but the problem is that somewhere hard coded into it is a filename with a space in it. i.e. 'GLUCOFACTS Deluxe'

This is splitting the filename parameter passed to the update checker into 2 parts and causing it to crash and aborting the main software.

I'll be contacting Bayer about this (I have found out the name of a software developer there!). Any information that anybody else can gice me would be welcome

Regards
Tony

Daughters Diabetes Blog
[http://human-pin-cushion.blogspot.com/](http://human-pin-cushion.blogspot.com/)

---

### Post by szr4321 on 2010-08-26
> **__j__ said:**
> For what it's worth, getting results from the Contour using the serial connector is pretty straightforward [...]
Great, thank you very much for the info!

---

### Post by szr4321 on 2010-08-26
> **fflakey said:**
> 
I've just been having a look at this godawful Glucofacts Deluxe software V2.07
Did you have any luck getting this to run? I'm still unsure whether I should write a set of scripts myself or just stick with one of those software packages...

---

### Post by Galiphraen on 2011-01-24
> **szr4321 said:**
> Did you have any luck getting this to run? I'm still unsure whether I should write a set of scripts myself or just stick with one of those software packages...

I am interested in using this software as well with the cable and meter.  Has there been any progress?

---

### Post by Michael Richardson on 2011-09-03
There is a thread over at: [http://ubuntuforums.org/showthread.php?t=1672855](http://ubuntuforums.org/showthread.php?t=1672855)
But, note that this is NOT for the device I have, a Contour 7152B.
I can see activity... does it matter what baud rate I use?
(Some USB devices just ignore baud)

---

### Post by vaideheep on 2011-09-18
Hello,

I am working on my masters report and the focus of my project is enabling biometric devices on android smartphones for the purpose of telemedicine. I happened to select the Bayer USB Glucometer. I was able to reverse engineer it using free available usb snoop and conversion scripts I found online.  The output of these tools is C-code that triggers the readings from the glucometer, and you can run this in Ubuntu. You can leverage this code to put your own GUI around it and format the output into csv if you want.

A few months ago, I documented this reverse engineering in a stack overflow posting:
[http://stackoverflow.com/questions/6554863/migrating-linux-c-code-that-talks-toa-usb-glucometer-device-to-android](http://stackoverflow.com/questions/6554863/migrating-linux-c-code-that-talks-toa-usb-glucometer-device-to-android)

At the time, I was still struggling with the port to Android. Since that post, I have managed to get it working in Android as well.  I am working on my report write-up, so if anyone is interested I can post that when I am finished.

Hope this helps!

---

### Post by Michael Richardson on 2011-09-19
> **vaideheep said:**
> I happened to select the Bayer USB Glucometer.
...
At the time, I was still struggling with the port to Android. Since that post, I have managed to get it working in Android as well. 

Which model, specifically, did you test with?
I was going to ask about how you ran Android in host mode, but I see in your post that you got that to work.

Have you released an app?  Or source code?

---

### Post by pyemus on 2013-03-23
Hi,
Have you come any further with this project? I'm very interested in some documentation about this, if you have any, would you mind sending it to me at [email]pyemus@gmail.com[/email]?

---

### Post by oldos2er on 2013-03-23
[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---

