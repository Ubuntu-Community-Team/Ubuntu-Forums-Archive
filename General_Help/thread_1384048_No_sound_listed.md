---
title: "No sound listed"
date: 2010-01-17
forum: General Help
---

### Post by dirtblack on 2010-01-17
I have installed 9.10 and do not have any sound at all.  i did do a list of playback devices with aplay-l and it did not list anything. I looked in sound props and didn't find one either.  I have had other versions of Ubuntu and had no problems. the machine I've loaded is a Toshiba laptop. Any help greatly appreciated.

---

### Post by mörgæs on 2010-01-18
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by dirtblack on 2010-01-19
Thanks for your help.  I did try almost everything on the page but still no sound.  At the most I now get a card displaying in sound settings as Internal analog stereo. Now I do get a pop when a vid starts but that's it. Anything else I can try?

---

### Post by alexfish on 2010-01-19
hi
could you post the output of the 

 aplay-l

---

### Post by dirtblack on 2010-01-19
Ok, after reading a bunch on the problem I tried this from another user

 Re: Karmic: No Sound
Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)
All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.

1. Backup (and then delete) your previous configuration files:
Code:
$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/ $ rm -r ~/.pulse ~/.asound* $ sudo rm /etc/asound.conf Warning: As always, use caution when removing files on your system. Any typos can potentially cause data loss.
Note: Don't worry if some of these files did not exist on your system.


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:
Code:
$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio 3. Ensure the evil "libflashsupport" library is not installed:
Code:
$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound Note: the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks!

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
Note: Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

Note: If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:
Code:
$ pulseaudio & pavucontrol 6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):
Code:
$ alsamixer -Dhw Note: When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.

7. Continue to Part B if you are running Hardy Heron (8.04), or Part C if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect!


NOW REBOOT TO TAKE EFFECT.
__________________
Remember hence where you come and pass it down. 


Now I do have a mic and I can hear sound faintly with my headphones. I can prob hear it from the speakers but it's noisy in here.  I will now try some of the others from your link and will get back to ya.

---

### Post by dirtblack on 2010-01-20
After trying everything I still can't get sound out of the speakers.  I also reloaded to no avail. Anyone else have a fix?

---

### Post by dirtblack on 2010-01-20
Sure Alex

dana@dana-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
dana@dana-laptop:~$ 

Shows nothing at all.

---

### Post by dirtblack on 2010-01-21
After messing with this problem I decided to remove pulse and add alsa. At first it didn't work and then went into synaptic and added the alsa drivers and low and behold I have sound!  Thanks everyone who helped.

---

