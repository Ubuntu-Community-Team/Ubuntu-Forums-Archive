---
title: "Where is the pulseaudio/alsa main config file?"
date: 2010-12-16
forum: General Help
---

### Post by nysmo on 2010-12-16
Hi,

I'm looking to create a simple script that changes the audio profile of my ubuntu, through command line.

To change audio profile I normally go to System -> Preferences -> Sound -> Hardware and change between Analog stereo Duplex or HDMI digital output.

Is there a config file where I can change this without using the GUI?

Thanks in advance

---

### Post by jack0w on 2011-03-20
Bump!

I am currently looking to do the same as above... 

Anyone know how to do this? :)

---

### Post by tordeu on 2011-03-20
The alsa configuration files are in 
> 
/usr/share/alsa


Additionally, you can put custom configuration files in two places (I have not tested it yet):

User-specific settings can be put in a file called
> 
.asoundrc

(in your home folder)

System wide settings can be put at 
> 
/etc/asound.conf


The .asoundrc and asoundf.conf file probably do not exist,yet. So, you will have to create them. After changing them, you need to restart alsa:

```

sudo alsa-utils restart

```

I have not changed any alsa stuff yet, so I will probably not be of much help when you encounter any problems. Nevertheless, here is a link which might be useful for you as well:

[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

I hope this gives you something to start.

---

### Post by jack0w on 2011-03-20
Thanks for the reply though that wasn't quite what I was looking for, let me explain more fully.

I've spent a considerable amount of time playing around with all manner of settings to control the sound card. 

I'm running XBMC on Ubuntu 10.10 and have come to a point now where I am able to get music and menu sounds OR dd/dts/5.1 pass-through for movies.

The only way I have found to get both to work simultaneously is to open sound preferences and on the hardware tab change the profile to 'Digital Stereo Duplex' followed by changing it to 'Analog Stereo Duplex'. 

I have found that by making this change each time I boot up, I am able to get stereo music, menu sounds and dd/dts/5.1 pass-through all to output correctly over HDMI.

What I am hoping to do is make a script that will change the Audio Profile automatically when I boot - any ideas how to achieve this?

Many thanks

---

### Post by tordeu on 2011-03-20
Unfortunately I do not know how to achieve that via command line. On the other hand, it should not be necessary to do that after every reboot, so we should try to fix the underlying problem.

One possibility that comes to mind is that the digital output is muted by default and that choosing both output configurations after one another, all the corresponding outputs are enabled/unmuted. So, we could try to get rid of the problem, so that you do not need to go through this process of choosing both outputs at all.

When you boot your computer, which sound do you normally have? Normal menu sounds out of your speaker, but the digital output does not give you any sound? To test this, there are several ways to go, depending on whether you want to use command line or not.



Without command line you could do this:

First, we probably need to install an ALSA Mixer GUI:

1. Go to Applications > Ubuntu Software Center
2. In the search box in the upper right corner enter "GNOME ALSA Mixer"
3. It will show the GNOME ALSA Mixer now. Select it and click "Install"
4. After installation, start it by going to Applications > Sound & Video > GNOME ALSA Mixer
5. At the top you might have several tabs, one for every sound device. Choose the sound device where you want to enable S/PDIF
6. At the bottom there should be an option named IEC958, which is probably disabled. Enable it.

Try if this will work, even after a reboot.



If you want to do this with command line, you can do this like this:

First, you might need to install the alsa-utils (I am not sure if they are already installed or not):

```

sudo apt-get install alsa-utils

```now you can start the alsamixer in command line:
```

alsamixer

```1. You can use F6 to select your sound device (might be already selected)
2. Use your left/right arrow keys to go to S/PDIF (which probably shows "MM")
3. press 'm' (This should change it from "MM" to "00" and turn green)

Test if this works, even after reboot.

---

### Post by jack0w on 2011-03-20
Thank you so much for taking the time to write such a detailed reply! 

I should start by answering your question, after starting up the computer, the sound profile is normally set to Analog Stereo Duplex and I won't hear any sounds from Ubuntu, nor menu clicks or music in XBMC but I can play a DVD I have ripped with 5.1 DD passed through to my AV Reciever. Same goes for any other type of 5.1 Audio. 

As I described in my previous post I've been switch the sound profile back and forwards before attempting to play anything in XBMC which seemed to bizarrely cure the problem!

I followed your instructions and installed GNOME ALSA Mixer. I decided since I currently had the computer on (and all sound was working) I would take a screenshot of the current settings in GNOME ALSA Mixer, and repeat this after a reboot in the hope that I could see what was changing!

Interestingly after installing GNOME ALSA Mixer and rebooting I compared the screenshot from before the reboot to the current settings.... they were identical..

I opened XBMC and tried all types of media, and everything seems to be working without a hitch, including menu sounds!

I started to think it must be a fluke as I've never managed to get all media playing consistently over HDMI,  so I rebooted a few more times, but the problem seems to have disappeared entirely!

Can't see why installing GNOME ALSA Mixer would have any impact on it, but then again, thou shall not fix what is not broken!! :D

---

### Post by tordeu on 2011-03-20
I mean, I hoped that you could fix your problem with the steps I provided, but I certainly did not expect the problem to be fixed after just installing the GNOME ALSA Mixer ;)

Nevertheless, I hope that it stays like this and you can enjoy your media now without going through that process every time. Take care.

---

