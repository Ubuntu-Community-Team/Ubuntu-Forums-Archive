---
title: "Help With Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller"
date: 2010-02-17
forum: General Help
---

### Post by kyle2595 on 2010-02-17
Hi, I was reading this article on how to fix the sound in Ubuntu 9.10 after upgrading from 9.04 ([http://www.howtogeek.com/howto/10964/how-to-fix-sound-issues-in-ubuntu-9.10/](http://www.howtogeek.com/howto/10964/how-to-fix-sound-issues-in-ubuntu-9.10/)) and when I open “GNOME ALSA Mixer”, nothing shows up (I have included a picture).  I typed in: ```
aplay -l
``` into terminal it says: ```
aplay: device_list:223: no soundcards found...
``` So then I thought that it was that my sound card was not recognized.  I typed in:                                   ```
lspci -v
``` and found out that my sound card was an "          Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)".  Can anyone help me with getting this to work?  Thanks.
P.S. Thanks to "Trevor Bekola" who helped me get this far.

---

### Post by jamesisin on 2010-02-17
Did you remove PulseAudio?

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Normally PA would handle your audio mixing.

---

### Post by kyle2595 on 2010-02-17
When I get to the part that says

"4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
[COLOR=Blue]**Note:** Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead."

[COLOR=black]I can't find [/COLOR][/COLOR][COLOR=black]"System/Preferences/Sound".[/COLOR]

---

### Post by jamesisin on 2010-02-17
Sorry, I use Gnome.  Is there something sound-like under System &#8212;> Preferences?

---

### Post by kyle2595 on 2010-02-17
I was looking around on Google and found this: [COLOR=Red][http://www.ghacks.net/2010/02/03/managing-sound-in-ubuntu-9-10/](http://www.ghacks.net/2010/02/03/managing-sound-in-ubuntu-9-10/)[/COLOR].  When it says 

"Head over to the [COLOR=Red][Alsa Project]("http://www.alsa-project.org/alsa-doc/")[/COLOR] ([http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)) and&#65279;&#65279;&#65279; search for suitable drivers. On this site you will want to match your sound card chipset with a compatible driver. When you have found the compatible driver install it and then you will have to add it to the kernel. Type the command:sudo modprobe snd-
and hit the Tab key twice. You will want to view all of the listings to make sure the module you need is there.  When you find the exact name of the module you need you can load it with the command:
sudo modprobe snd-XXX
Where XXX is the actual name of the module you need to load."

I think that my module is either "snd-intel8x0" or "snd-intel8x0m".  Can someone conferm which one it is, I was never able to find out how to match my sound card chipset with a compatible driver.  Thank you to anyone who helps me!

---

### Post by kyle2595 on 2010-02-17
Never mind, the only Intel cards that are supported are the ICH Southbridge ones.
Still looking for a solution to my original problem...

---

### Post by efflandt on 2010-02-17
I have that sound device on my Toshiba laptop.

Sound should work no problem, **unless** you are still running a Jaunty kernel (things changed).  What is the output of **uname -a**?  If that is a .28 kernel (before .31), that is your problem.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

Well, same device, but different revision.

---

### Post by kyle2595 on 2010-02-17
The output for the code is:
```
Linux KylesLaptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```
I had upgraded from 9.04, I know that a fresh install of Ubuntu 9.10 would fix everything, but I was hoping to fix it without having to do that.

---

### Post by jamesisin on 2010-02-17
Maybe I'm missing something, but shouldn't kernel updates be included somewhere in the upgrade/update process?

---

