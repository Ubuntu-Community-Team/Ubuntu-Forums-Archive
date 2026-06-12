---
title: "Microphone problem"
date: 2006-04-05
forum: General Help
---

### Post by buttari on 2006-04-05
Hi,
I'm running Dapper on a thinkpad T60p which has the following audio card (according to lspci):

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I use Skype with no problem at all but with other applications microphone doesn't work. For example in the "sound recorder" or, also, in ekiga. Everything is enabled and at max level in gnome-volume-control.
I used to have the same problem on an older Thinkpad T40.
Any suggestion?

Regards,
Alfredo Buttari

---

### Post by luopio on 2006-04-06
Just got my mic on my laptop working (ICH4). Looking at your problem it sounds a classic case of ESD taking control. Last time I checked Skype uses ESD (Enlightened Sound Daemon) to play. ESD steps on alsas toes a bit too much on the capture side and prevents ALSA from controlling the mic. This leads to the problem with more advanced programs that use gstreamer ;) (which in turn uses ALSA, not ESD, on dapper). 

Solution: open a terminal and type "killall esd". Then use the Ekiga druid to test the mic. Check that you have your microphone and capture channels up and unmuted (all crosses taken out) in gnome-volume-control and that gstreamer uses ALSA for all audio things (run gstreamer-properties in the terminal)

If all is well, I suggest giving up esd by unchecking the sound server box in system->preferences->sound, this should prevent esd from starting up. Also I think that Skype can use ALSA or at least OSS instead of ESD.

Happy hacking.

---

### Post by cosmolee on 2006-04-07
I have the same problem with Breezy.  

My microphone works fine for Skype, but I can't capture the sound from it with either Audacity or Sound Recorder.  All my levels are up in the Gnome/Gstreamer mixer.  I can hear myself talking into the microphone through the speakers.

The odd thing in Audacity is that it doesn't give me any options in the recording source drop-down box (next to the recording level slider) - not microphone, line - nothing.  It doesn't give me any options at all.  

ESD is not running on my system, I've disabled the Sound Server in System->Preferences->Sound, and in System->Preferences->Multimedia Systems Selector, Alsa is set for Default Sink and Default Source.

I'm banging my head against the wall on this one...](*,)

---

### Post by Jindro on 2006-04-07
install alsa-oss
run: aoss skype

---

### Post by japs_it88 on 2006-04-07
i have a similar but reversed problem. if i unmute my mic i can hear it on my speakers, but the recording level and volume monitors remains as if no sound was captured nor playied. skype too doesn't "hear" my microphone.

lspci returns: Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller, it should be a realtek ALC850

---

### Post by Jindro on 2006-04-07
check this:
[http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html)

Skype uses ESD.

OSS is converted with no problem.

If you use ALSA ( e.g. in dapper you will), the solution above should help.

---

### Post by cosmolee on 2006-04-07
install alsa-oss
run: aoss skype
__________________
Jin

What does the above accomplish?  I'm not having any trouble using my microphone with Skype - my problem is using a microphone with Audacity & Sound Recorder.  Is this supposed to fix a problem with Skype or the other programs??

In other words: 

I can use Skype fine.  This proves that my microphone is working OK & that my settings for the microphone in the mixer(s) are OK, I think.

My problem is that I can't record any input from my microphone from Audacity or Sound Recorder.  

I hope that helps clear things up...

Cosmo

---

### Post by Avilion on 2006-04-09
I too am having a problem with this. Now, I haven't tried it in Skype, but I am having the same issues as others; that is, I can hear myself over my speakers when I speak into the microphone, but when I go into Sound Recorder or Audicity to record, nothing gets recorded. 

I've gone into alsamixer, and made sure the correct sound card was selected and everything. However, I can't seem to adjust the volume of my microphone in the Capture settings. Here is a screenshot of the alsamixer:

[IMG]http://www.benpachter.com/alsamixer.jpg[/IMG]

Following all the guides here in the forums had done nothing. Does anyone have any suggestions?

---

### Post by buttari on 2006-04-12
I tryied all of your suggestions but, simply, the microphone is not working. It is working with skype but not with ekiga, sound record, sjphone etc.

any further suggestion?

Thanks

Alfredo

---

### Post by kagashe on 2006-04-12
Hi,

I don't use Dapper but don't have any problem on Breezy after using Skype. See my post [here]("http://www.ubuntuforums.org/showthread.php?t=155053&highlight=kagashe")

---

### Post by bignickel on 2006-06-27
I had a similar problem with my microphone under ekiga, and I just need to make sure BOTH Microphone and Capture were active and unmuted in volume control.  Now I can capture using sound-recorder, audacity, and ekiga.

---

### Post by iveevi on 2006-07-12
My 5 cents. Almost the same problem. 
ThinkPad x60
 Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Microphone doesn't work neither with skype nor with sound recording applications. I've been testing different distros lately and it worked for a while on RH4 with 2.6.16.16. kernel, but then I kept playing with the kernel and it stopped working at some point.

Now I have a scratch Drapper installation and it does not work. 
Everything looks perfect in gnome mixer, alsamixer shows the same picture as attached above mic capture is read and you're unable to change anything.

I'm banging my head against the wall as well ](*,) since it seems to be the only thing that does not work! A bloody fingerprint reader works for Gods sake!
:)

---

### Post by larch on 2006-07-23
> **buttari said:**
> Hi,
I'm running Dapper on a thinkpad T60p which has the following audio card (according to lspci):

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I use Skype with no problem at all but with other applications microphone doesn't work. For example in the "sound recorder" or, also, in ekiga. Everything is enabled and at max level in gnome-volume-control.
I used to have the same problem on an older Thinkpad T40.
Any suggestion?

Regards,
Alfredo Buttari

I have a Thinkpad T-23 and was having trouble getting an external microphone to work with Audacity.  I installed alsa-oss and that did the trick.

Dan French

---

### Post by sog on 2006-08-02
just an FYI that on a Thinkpad x60s, i could not get the microphone - internal or external - working with Audacity, gnome-sound-recorder, Gizmo or otherwise, but killing esd seems to do the trick. 

all of a sudden Audacity can hear me. will try the external headset mic tomorrow, but so far so good. 

hardware is: 

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by envykris on 2006-08-13
gentlemen,
this is crazy! everybody seems to say install alsa-oss.  But thats what i am not able to figure out how.  
I keep doing, sudo apt-get install alsa-oss.  But it doesnt seem to find the package.
does anybody know if i need to add addl repositories in my sources list in order to get hold that piece of !@#$

Dapper is a big flop becos of all sorts of sound issue, it is certainly not ready for the "user".

pls help..
cheers..

---

### Post by Leif on 2006-08-23
I'm having more or less the same problem.

Advent 7093 laptop
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Audio playback was fine out of the box with Dapper, but the microphone is not working, for skype, ekiga, sound-recorder etc. Everything is unmuted in the sound settings, but as in the picture in an [earlier post]("http://ubuntuforums.org/showpost.php?p=905224&postcount=8"), under alsamixer I can't get the microphone settings to a non-zero value.

This is really starting to annoy me, and I don't want to have to use Windows on this computer, but at the same time, I need to use skype. Except for hibernation and mic, everything works, and I can kinda live without hibernation. Can anyone help ?

---

### Post by ajesh on 2006-08-27
I almost had the same problem with my desktop in that I could hear my micropphone through my speakers, but I could not record anything using the sound recorder.

I enabled Microphone, Line in in the capture tab and nothing worked.

Finally, I also enabled Capture. If this is not shown in the capture tab in the volume control. You will have to go to Edit -> preferences and add Capture which is way at the bottom (not in alphabetical order). Then you will have to enable capture through microphone....this should make the recording work through microphone

---

### Post by Leif on 2006-08-28
**ajesh**'s solution may help some of the people on this thread, but unfortunately not me (I do, of course, realize that it's not all about me, though :) ). 

I don't hear myself over the speakers, or anything like that. I have no confirmation of my mic working in any way whatsoever.

Oh, and I also already have the capture tab working, and everything enabled.

---

### Post by cybertoast on 2006-09-07
Ok, this is weird - I had all of the same symptoms and problems. The thing that worked for me was to enable the microphone in the Capture option of the volume control applet (double-click the loudspeaker icon at the top of the screen). The Capture tab needed to have the Capture slider's microphone icon (bottom right) to NOT have the red X through it. I'm still not clear on why Skype works fine. If anyone would be kind enough to explain how the mic inputs are controlled by Skype and other audio devices I would be very grateful :-)

One other thing - I'm not sure whether killing esd makes a difference. I'll test this out some more, and post an update in a bit.

---

