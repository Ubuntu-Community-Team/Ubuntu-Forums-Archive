---
title: "No sound in Ubuntu?"
date: 2010-01-26
forum: General Help
---

### Post by THE GMoD on 2010-01-26
From what I heard this is a popular problem, but I have NO sound in Ubuntu at all,
I just installed Ubuntu over Kubuntu and I had/Have no sound in either? any advice?

---

### Post by JackRock on 2010-01-27
Few things here.

1.  CALM DOWN.  It's a busy forum, and not everybody clicks on every link.
2.  What version of Ubuntu are you using?
3.  What type of sound card (make/model) do you have?
4.  Have you checked your sound settings under System>Preferences>Sound?
5.  Any other details you can provide, such as did you recently do an upgrade, or re-install?

---

### Post by THE GMoD on 2010-01-27
> **JackRock said:**
> Few things here.

1.  CALM DOWN.  It's a busy forum, and not everybody clicks on every link.
2.  What version of Ubuntu are you using?
3.  What type of sound card (make/model) do you have?
4.  Have you checked your sound settings under System>Preferences>Sound?
5.  Any other details you can provide, such as did you recently do an upgrade, or re-install?

1.Ok I will calm down -_-
2.9.10
3.An original Sound Blaster Audigy
4.Yes
5.I installed it over Kubuntu 9.10 using the Konsole today, had no sound on Kubuntu either.

As for the other person, I think my signature is appropriate as... well it is the truth, I am not a huge Linux fan but... its ok

---

### Post by t4thfavor on 2010-01-27
I have an audigy 2 ZS, and a platinum pro that work sorta. Make sure you have it plugged into the correct output, as all mine were gold, and unlabeled. 

Don't use the livedrive it you have one, I never got it to work.
Digital out is spotty, as the creative driver broke it, on vista as well as ubuntu. I think it still is.

Other than that, I have no more real input as mine works with normal speakers output only (no recording).

---

### Post by THE GMoD on 2010-01-27
> **t4thfavor said:**
> I have an audigy 2 ZS, and a platinum pro that work sorta. Make sure you have it plugged into the correct output, as all mine were gold, and unlabeled. 

Don't use the livedrive it you have one, I never got it to work.
Digital out is spotty, as the creative driver broke it, on vista as well as ubuntu. I think it still is.

Other than that, I have no more real input as mine works with normal speakers output only (no recording).
 
My sound worked before, after I reset, but then it died again, now reseting doesn't help?

---

### Post by zaphod777 on 2010-01-27
After doing a Google search for "Sound Blaster Audigy ubuntu 9.10"
The first result was your thread and the second one looks like the fix you need.

I have found that googling for a fix will usually yield some good results on where to start looking to fix a problem.

After posting in these forums try looking around and then posting any results or failures you have had and it will keep your thread more on top. 

Sometimes my threads don't always get answered but I just keep trying. 

Here is what looks like a fix for you:
[http://www.ubuntugeek.com/fix-for-no-sound-sound-blaster-audigy-after-upgrading-from-ubuntu-9-04-to-9-10.html](http://www.ubuntugeek.com/fix-for-no-sound-sound-blaster-audigy-after-upgrading-from-ubuntu-9-04-to-9-10.html)

---

### Post by THE GMoD on 2010-01-27
Ok well thanks for the link it would help if I had a tab called SigmaTel, I go into Alsa mixer and... nothing?
no Sigmatell anywhere...
but there is Analog Devices AD1985?
witch is strange? so is it trying to use something that is not there? or OnBoard audio?
I am not sure?
so I check sound Preferences.
and it is set to use Internal Audio, I think I have found the problem but....
setting it to
SB Audigy
doesn't change the fact that I have no sound? so I go back into the Sound Preferances and it is highlighting Analog Devices again?
So I am back at square 1?

---

### Post by zaphod777 on 2010-01-27
> **THE GMoD said:**
> Ok well thanks for the link it would help if I had a tab called SigmaTel, I go into Alsa mixer and... nothing?
no Sigmatell anywhere...
but there is Analog Devices AD1985?
witch is strange? so is it trying to use something that is not there? or OnBoard audio?
I am not sure?
so I check sound Preferences.
and it is set to use Internal Audio, I think I have found the problem but....
setting it to
SB Audigy
doesn't change the fact that I have no sound? so I go back into the Sound Preferances and it is highlighting Analog Devices again?
So I am back at square 1?

Mine is set to internal Audio but I have a laptop.

Did you try and install the option they suggested in the link?

---

### Post by THE GMoD on 2010-01-27
> **zaphod777 said:**
> Mine is set to internal Audio but I have a laptop.

Did you try and install the option they suggested in the link?
What option? Alsa Mixer I have?

---

### Post by garvinrick4 on 2010-01-27
[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][SIZE=4][B]go to software sources and make sure backports are checked on. And reboot when done with this process, only takes a minute

Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)[/B][/SIZE]
*All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.*

1. Backup (and then delete) your previous configuration files: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ rm -r ~/.pulse ~/.asound* [/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo rm /etc/asound.conf[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#ff0000]**Warning:**[/COLOR][COLOR=#ff0000] As always, use caution when removing files on your system. Any typos can potentially cause data loss.[/COLOR]
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Don't worry if some of these files did not exist on your system.[/COLOR]


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000] [FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio[/SIZE][/FONT][/COLOR] [[COLOR=#444444][FONT=Verdana, Arial, Tahoma][SIZE=2]_3_[/SIZE][/FONT][/COLOR]]("https://bugs.launchpad.net/bugs/192888")[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]. Ensure the evil "libflashsupport" library is [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]**not**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2] installed: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks![/COLOR]

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.[/COLOR]

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:[/COLOR][/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ pulseaudio & pavucontrol[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ alsamixer [COLOR=#0000ff]-Dhw[/COLOR][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.[/COLOR][/SIZE][/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]NOW REBOOT TO MAKE FIX STICK.
7. Continue to **Part B** if you are running Hardy Heron (8.04), or **Part C** if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect![/SIZE][/FONT][/COLOR]
 		                   		  		  		 		 			 				__________________
				Remember hence where you come and pass it down.

---

### Post by THE GMoD on 2010-01-27
> **garvinrick4 said:**
> [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][SIZE=4][B]go to software sources and make sure backports are checked on. And reboot when done with this process, only takes a minute

Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)[/B][/SIZE]
*All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.*

1. Backup (and then delete) your previous configuration files: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ rm -r ~/.pulse ~/.asound* [/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo rm /etc/asound.conf[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#ff0000]**Warning:**[/COLOR][COLOR=#ff0000] As always, use caution when removing files on your system. Any typos can potentially cause data loss.[/COLOR]
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Don't worry if some of these files did not exist on your system.[/COLOR]


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000] [FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio[/SIZE][/FONT][/COLOR] [[COLOR=#444444][FONT=Verdana, Arial, Tahoma][SIZE=2]_3_[/SIZE][/FONT][/COLOR]]("https://bugs.launchpad.net/bugs/192888")[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]. Ensure the evil "libflashsupport" library is [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]**not**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2] installed: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks![/COLOR]

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.[/COLOR]

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:[/COLOR][/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ pulseaudio & pavucontrol[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ alsamixer [COLOR=#0000ff]-Dhw[/COLOR][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.[/COLOR][/SIZE][/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]NOW REBOOT TO MAKE FIX STICK.
7. Continue to **Part B** if you are running Hardy Heron (8.04), or **Part C** if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect![/SIZE][/FONT][/COLOR]
                                                                                               __________________
                Remember hence where you come and pass it down.


Non of this helped sadly D:

OffTopic: I just reset and it said Catching Service Kernaloops...
its not the first time, and now I actually know what it means, I just thought I would share it with you :P anyways I reported it...

---

