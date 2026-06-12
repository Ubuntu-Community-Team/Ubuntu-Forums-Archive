---
title: "sound problems with karmic clean installation"
date: 2010-02-08
forum: General Help
---

### Post by skn332 on 2010-02-08
I have recently installed Karmic kubuntu and i have sound problems. I did a clean installation. Sound works in amarok and that's it . I am running the sound through my video card which is an ati radeon 4890 hd. it is being run through the hdmi cable from the video card to the tv. i have uninstalled and installed flash player. i have tried running just alsa with no pulse audio and and i have tried with pulse audio. I tried both these fixes:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
The first one is a "comprehensive multimedia and video how-to" and the second is a pulseaudio guide.
I did have the opening and closing system jingle and dragon player working (no vlc or gnome or any others) but the system sounds and dragon player stopped working and now only amarok works.  please will someone help me get sound!

---

### Post by mörgæs on 2010-02-09
Maybe these will help:

[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by skn332 on 2010-02-10
ive done both of those guides and now i have no sound at all.  can anyone help me at all?

---

### Post by pheoio on 2010-02-10
I am still a newbie with Ubuntu but I have had a similar problem. Sometimes the wrong sound setting get automatically. In my case when I upgraded to Ubuntu 9.10 I had no sound what so ever. I read a page saying to install _GNOME ALSA mixer_ and once installed I noticed it had the setting _External Amplifier_ checked. Once it was unchecked it worked I had sound. I hope it is the same in your case with Kubuntu.

---

### Post by mörgæs on 2010-02-11
Hi Pheoio, welcome to the forum.

Skn332: Are you sure that you are using the newest Alsa? 
[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

---

### Post by skn332 on 2010-02-11
yes i did have the newest version of alsa.  so i deleted everything and did a clean installation.  i then upgraded alsa and reinstalled my video card driver.  i had sound in amarok and the system but no sound in flash or video players.
i then removed libpulse0 and now i get to a screen that has the computer name followed by tty1.  i reinstalled libpulse0 (i can use the console but i cant use gui)  if i type startx it just goes to a screen that looks like the console but i cant type or anything.
i am going to boot up from the cd and reinstall linux but not tonight. 
i will get back to the point before i removed libpulse0 and at least the gui worked. but from there i still won't have sound in flash or video.  any advice?

---

### Post by skn332 on 2010-02-13
so im back to where i was.  i have sound in amarok and i have sound at startup and shut down, but that is it. (both running thru hdmi).  video has no sound (which is weird to me because the sound is running through the video card).  when i do try to play a video, a popup says that hdmi doesnt work and it is switching back to the mobo sound.  any help?

---

### Post by mörgæs on 2010-02-16
How does the sound work, if you boot with a 9.04 live CD? 

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

### Post by menephous on 2010-02-16
YAY! This worked first time and was very simple after all the other threads I tried. No question this is the best, easiest fix for the no sound problem! Thank you sooooo much for posting this link!

[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

B-)

---

### Post by mörgæs on 2010-02-16
You are welcome. Glad to hear that it worked.

---

### Post by skn332 on 2010-02-17
i havent tried 9.04 or the newer version yet.  i was hoping for a fix in 9.10 because i don't really want to reinstall all of the drivers again.
when i entered this txt
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*

i got kmix and amarok as the programs being used.  i got rid of kmix and installed pulseaudio but nothing changed (i have sound in amarok and opening but no sound anywhere else) 
now when i enter the text above nothing comes up.  im going to try a pulse audio fix to see if that might work.

---

### Post by skn332 on 2010-02-17
here's a new one.  pulseaudio doesn't recognize my sound card.

---

### Post by mörgæs on 2010-02-17
> **skn332 said:**
> i havent tried 9.04 or the newer version yet.  i  was hoping for a fix in 9.10 because i don't really want to reinstall  all of the drivers again.


But what about trying the sound from a 9.04 live CD without installing?

---

### Post by skn332 on 2010-02-19
i booted 9.04 from the cd without installing and in order to get the sound to work i have to activate my video card which requires a reboot thus nullifying everything.  i really dont want to install it and have to redo everything. 
i have sound with everything but flash now (dragon player just started working).  it seems futile to install a new version just to get sound for flash.

---

### Post by mörgæs on 2010-02-20
Maybe these will help:
[http://ubuntuforums.org/showthread.php?t=1309931](http://ubuntuforums.org/showthread.php?t=1309931)
[http://ubuntuforums.org/showthread.php?t=1306234](http://ubuntuforums.org/showthread.php?t=1306234)

---

### Post by skn332 on 2010-03-04
sorry been busy lately.  so i tried both of these and neither workerd.  what i did read tho was that flash sends its audio to the integrated sound.  so i checked the sound on the integrated sound and lo and behold flash was working on that.  but i want the flash sound to work with my video card (which all the other sound deevices do).  how would i go about making flash use my default sound card (which is my video card using an hdmi cable) and not the integrated sound?

---

### Post by mörgæs on 2010-03-05
[http://ubuntuforums.org/showthread.php?t=1198071](http://ubuntuforums.org/showthread.php?t=1198071)

---

### Post by skn332 on 2010-03-06
morgaes, i am very grateful for your help.  thank you very much. 
the link you provided me seems to be the exact problem i am having.  the only problem is that the link is for 9.04 and it tells you to alter ~/.asoundrc .  9.10 doesnt have this file so i am at a loss.  i am searching through the forums and google but have not found anything useful.  any suggestions?

---

### Post by mörgæs on 2010-03-07
You are welcome! 

Sorry, I can't help you here. 9.10 is the only Ubuntu since 5.10 I am not going to use, so I don't have much experience.

---

