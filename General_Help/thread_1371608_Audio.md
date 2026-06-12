---
title: "Audio"
date: 2010-01-03
forum: General Help
---

### Post by suncross on 2010-01-03
I just installed ubuntu 9.10, and I updated my system to find out I don't have any audio.  I have the Creative Audigy sound blaster audio card, and I cannot hear anything from it.  Is there some place I can get audio from?

---

### Post by suncross on 2010-01-03
Ok so I typed in:

sudo aplay -l 

to the console, and it says n soundcards found...

What does this mean and how can I fix it?

(note, before I typed that in I just put my speaker jack in the on board sound system)

---

### Post by suncross on 2010-01-03
Ok I have been following guides that I have found throughout the forums and non of them worked.  I think I totally messed up my sound, is there anyone that can help from step 1 or something?

---

### Post by CausingTraumaZ on 2010-01-17
I also had this problem but I just fixed it. You should just go to System>prefences>sound and be sure that the (V) icon is unchecked at Mute. And you may now here your voice..
I hope this helped

---

### Post by garvinrick4 on 2010-01-17
Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)
All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.

1. Backup (and then delete) your previous configuration files:
Code:
$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ rm -r ~/.pulse ~/.asound* 
$ sudo rm /etc/asound.conf
Warning: As always, use caution when removing files on your system. Any typos can potentially cause data loss.
Note: Don't worry if some of these files did not exist on your system.


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:
Code:
 $ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
3. Ensure the evil "libflashsupport" library is not installed:
Code:
$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
Note: the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks!

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
Note: Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

Note: If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:
Code:
$ pulseaudio & pavucontrol
6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):

Code:
$ alsamixer -Dhw
Note: When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.

7. Continue to Part B if you are running Hardy Heron (8.04), or Part C if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect!

---

### Post by garvinrick4 on 2010-01-17
I am sorry I did not read your problem well. This fix is for
sound problems in 9.10 but not for helping to discover a device not
found. Sorry getting late here.

---

