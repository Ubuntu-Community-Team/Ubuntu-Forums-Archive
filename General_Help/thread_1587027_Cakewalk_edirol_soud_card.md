---
title: "Cakewalk edirol soud card"
date: 2010-10-02
forum: General Help
---

### Post by granul on 2010-10-02
HI! I just installed Ubuntu in dual with windows 7 it's working perfectly. The only problem is that my sound card does not work with Ubuntu. I use a Cakewalk Edirol UA-25 Ex. Is there a way to make it work.

Thank you

---

### Post by stinkeye on 2010-10-03
I have the Cakewalk Edirol UA-25 Ex and it works perfectly out of the box in Ubuntu and Ubuntu-Studio 10.04
Have you opened sound preferences and selected the Edirol as your input and output.
I would also install pavucontrol (PulseAudio Volume Control) and have a look in there.

---

### Post by granul on 2010-10-03
Thank you, it work perfectly.  Do know if a record program similar to Sonar exist for Linux?

---

### Post by hrickh on 2010-10-03
> **granul said:**
> Thank you, it work perfectly.  Do know if a record program similar to Sonar exist for Linux?
Rosegarden or Muse are going to be the closest to Sonar.

I like Rosegarden, myself.

R.
==

---

### Post by stinkeye on 2010-10-03
There is [**_[COLOR="DarkRed"]Ardour[/COLOR]_**]("http://ardour.org/")
Not sure if it is in the software centre.
You'll need to install the Jack Audio connection kit as well.
Easiest way is to install [**_[COLOR="#8b0000"]ubuntu studio[/COLOR]_**]("http://ubuntustudio.org/"), which is a purposely 
built distro based on Ubuntu with all the audio stuff included.

I Triple boot with XP, Ubuntu and Ubuntu Studio.

I have only Just started messing around with Ubuntu Studio, just using Audacity to record some guitar stuff.

Studio comes with a drum machine, midi keyboard, guitar effects, Jack audio, mixer etc.

Do a search on you tube for rakarrack if your interested in guitar effects.

---

### Post by granul on 2010-10-03
Can I install or upgrade Unbutu Studio over Unbtu?

---

### Post by stinkeye on 2010-10-03
> **granul said:**
> Can I install or upgrade Unbutu Studio over Unbtu?
No, Ubuntu studio is a complete operating system but you can install the same programs that ubuntustudio uses, in ubuntu.
You will need to install **JACK Control** to get your sound working though.
See here...[**_[COLOR="DarkRed"]http://www.youtube.com/watch?v=YXIFi2LPQp0&feature=related[/COLOR]_**]("http://www.youtube.com/watch?v=YXIFi2LPQp0&feature=related")

This wiki page shows the audio packages included with ubuntustudio. 
[**_[COLOR="DarkRed"]UbuntuStudio/PackageList[/COLOR]_**]("https://wiki.ubuntu.com/UbuntuStudio/PackageList")

---

### Post by granul on 2010-10-03
Ok I have installed [**_[COLOR=DarkRed]Ardour[/COLOR]_**]("http://ardour.org/") , when I open it shows a menu with driver, interface etc. there is 5 choice (Alsa, Oss etc.) for the driver which one should I choose for the cakewalk ua-25,

---

### Post by stinkeye on 2010-10-03
I have not used Ardour yet.
I have been using Audacity, a much simpler recording program.
[**_[COLOR="DarkRed"]Ardour manual[/COLOR]_**]("http://en.flossmanuals.net/Ardour/Introduction?q=flossmanual")

---

### Post by granul on 2010-10-03
I get error message witch would surely happen with Audacity: 
There are several possible reasons: Ardour could not start JACK

1) You requested audio parameters that are not supported..
2) JACK is running as another user.

Please consider the possibilities, and perhaps try different parameters.

---

### Post by stinkeye on 2010-10-03
> **granul said:**
> I get error message witch would surely happen with Audacity: 
There are several possible reasons: Ardour could not start JACK

1) You requested audio parameters that are not supported..
2) JACK is running as another user.


Please consider the possibilities, and perhaps try different parameters.

Check that you have jackd qjackctl and libjack0 installed.Search in the software centre.
Start  jack control before you start Ardour.[**_[COLOR="DarkRed"]Starting Jack[/COLOR]_**]("http://en.flossmanuals.net/Ardour/StartJackUbuntu")
I can't trouble shoot issues you might have as I've only just started 
using these programs and I'm using ubuntustudio which is preconfigured to work.

---

### Post by granul on 2010-10-03
Yes both of jackd qjackctl and libjack0 are installed. If I install ubuntu studio do I have to uninstall ubuntu before and do a new installation?

Thank you for the help :-)

---

### Post by hrickh on 2010-10-03
I'm not in front of my music machine at the moment, but I can tell you that if you've just installed some of these audio pgms in standard Ubuntu without recompiling the kernel for realtime use, you're going to have problems like this with Jack (not to mention constant xruns).

Honestly, if you haven't done too much in the way of customization, I'd recommend a clean install of Ubuntu Studio. That way you're assured of getting a good, clean realtime kernel and all your necessary programs with their dependencies met.

And you won't have problems with JACK.

R.
==

---

### Post by granul on 2010-10-03
Can I install unbuntu studio over unbutu, I don't want triple boot. Thanks again

---

### Post by hrickh on 2010-10-03
> **granul said:**
> Can I install unbuntu studio over unbutu, I don't want triple boot. Thanks again
Ubuntu Studio *is* Ubuntu, with the realtime kernel and multimedia apps. You would be installing in place of/replacing your current Ubuntu (which is why I mentioned the customization bit).

R.
==

---

### Post by transmogrifox on 2010-10-04
> **granul said:**
> Can I install unbuntu studio over unbutu, I don't want triple boot. Thanks again

Last time I set up an ubuntu machine for RT use, I just used standard Ubuntu, then installed the RT kernel, did a few customizations, then added the audio apps I wanted.  For me, Ubuntu Studio is not really much different than getting Ubuntu with default audio stuff already installed and configured.  

You can put in a little effort and get a system that performs just as well without having to triple boot, or reinstall the operating system.

However, if you're really new and want things to work out of the box, then a fresh install from the Ubuntu Studio CD may be easier for you than learning some of the things you need to do to get jack working.

I have a dual boot system:
1) Debian Sid w/ fluxbox (really stripped down) for RT audio stuff.
2) Linux Mint (basically Ubuntu) for flashy fancy things.

Both are set up to do RT audio, and Linux Mint works ok for RT even with the stock kernel.

I'm a big fan of improving realtime performance by eliminating worthless programs from running (panel applets, graphics effects, networkmanager, automatic removable storage detection services...etc).  If you don't have any programs trying to take priority, then real-time scheduling is simply a side-effect.  A stock Linux kernel is capable of much better real-time scheduling than what many give it credit for.

On my Debian Sid box, the current kernel I'm using is 2.6.35, and there is no RT patch for this kernel.  I have it configured as a Preemptive kernel (which is as good as you can get w/o the RT patch).  This kernel performs fine for what I do.  I can do 2.7ms latency with few xruns, and perfect performance at 5.1ms latency.  

If you want to have the full Ubuntu experience (applets, system tray clock, various services, etc.) then you will need an RT kernel to get any decent RT audio performance... but if you are willing to learn how to kill the X server and start it up in a really stripped down mode with only a window manager and RT audio apps, then you can get it down to this:
ctrl + alt + backspace...
login at console
xinit

Start playing.  If your local X configuration script run by xinit contains commands to start a very basic X session and kills any services that aren't necessary to your audio session, then there will be very few processes to pre-empt the RT audio processing, and then a stock kernel may give you acceptable performance.

It's just a steep learning curve to get there...thus audio-optimized Linux distributions proliferate.

Another idea is you can try something like GNUguitarINUX and do audio from a liveCD environment.

Either way it would be unfortunate to see a myth sprout and grow that Ubuntu Studio is different from Ubuntu.  Ubuntu Studio is stock Ubuntu configured to be optimized for multimedia applications out of the box.  Ubuntu Studio uses Ubuntu's repositories, and has the same software selection available. It saves the user some work, but you can go from Ubuntu to something equal to UbuntuStudio without having to do a fresh install.

Of course, in general, GNU/Linux is GNU/Linux.  Having played with CentOS, Fedora, Linux Mint, Debian, Ubuntu...and a few other less known distributions, I see the same principles in play for realtime audio.  In other words, you can make a good RT audio environment by customizing your install of any given Linux distribution.  The difference between Linuxes is not like the difference between Win, Mac, etc.  

I think I have rambled enough...but suffice it to say triple boot is not necessary.

---

### Post by granul on 2010-10-08
I finaly installed Ubuntu Studio. So now if I understand, before  i open Rosegarden, I have to run Jack audio connection. I did this but I can't record anything in Rosegarden, i choose audio and try to record a track but it does not work, I hear my guitar but no record. Maybe there is something to do with the Jack connectio?

Thank you

---

### Post by granul on 2010-10-11
I can record with Audacity but not with Ardour and musE, the configuration in Jack seems ok, I don't understand why it is not working. I need a little help, I'm new with Ubuntu Studio.

Thank you

---

### Post by stinkeye on 2010-10-11
Have a look at this youtube video.[**_[COLOR="DarkRed"]http://www.youtube.com/watch?v=7HkSNTY6vdM[/COLOR]_**]("http://www.youtube.com/watch?v=7HkSNTY6vdM")
In jack, check in preferences your using the edirol as your input/output
by clicking on the arrows circled in the pic.
In the connections window for jack I have capture1 and capture2.
capture1 is the integrated sound on my motherboard.
Capture2 is the edirol.

Pic2 shows the connections which are done automatically by Ardour
except the capture to the Ardour audio1/in 1

---

### Post by granul on 2010-10-11
Ok now it's working with Ardour but not with Muse. Thank you for the help

---

