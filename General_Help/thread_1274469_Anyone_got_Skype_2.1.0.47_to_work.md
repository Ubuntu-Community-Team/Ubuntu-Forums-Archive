---
title: "Anyone got Skype 2.1.0.47 to work?"
date: 2009-09-24
forum: General Help
---

### Post by donsy on 2009-09-24
If anyone has had success with Skype 2.1.0.47 in Jaunty can you please tell me your sound settings and what webcam you're using? Thanks.

---

### Post by greenewbie on 2009-10-23
[SIZE=4]_**PROBLEM: NO SOUND TRANSMISSION **_[/SIZE][SIZE=4]_Skype Version 2.1.0.47 (beta)_[/SIZE]


 **As "donsy" asked above: My first question to you all is: has anybody actually got the latest version of Skype** for Linux **2.1.0.47 (beta) **working on any Ubuntu release?! I've spent so much time in the past trying to get Skype to work in Ubuntu and this time round it's proving to be just as tiresome.I don't hear any sound at all, either when Skype is loading or when I click on the “Test sound” button or when I call the Echo test, another Skype user online or a landline.  My voice is not transmitted either.  I have the same problem using Ubuntu 8.04 (my main hard disk) and 9.04.  I tried the latter switching hard disks; I then upgraded it to 9.10 Beta (nothing ventured, nothing gained I thought!) but it still doesn't work.  I don't know about 8.10 yet (that's on another hard disk again and I've got a separate issue of not being able to get to my desktop on it).
 The only things Skype will do at the moment (but in complete silence!) is that it will load up fine; the dialog box tells me I can successfully connect to other Skype users; it will make a landline ring; when I ring the Echo Test, it appears to get through but nothing happens when I speak whilst “speaking” is displayed in the box.  I can also make Instant messages with no problem.
It appears to be a **software problem** rather than a hardware problem, as I can use Audacity fine (It captures and replays my voice perfectly); Gizmo too, using the same PC as when I try to call on Skype.  When I use the same PC but an old hard disk with XP on it, I can use Skype perfectly with the latest version 4.1 for Windows.  My PC meets all the **hardware requirements **listed on its Linux download page (I have an Intel 1.7 Ghz CPU and 512 Mb RAM); however the only thing I'm not sure about is “Video card driver with Xv support”, as I don't actually have a webcam yet, nor am I trying to make video calls (I'm just using a good-quality Plantronics headset for the time being).  Can anybody confirm to me please that this is not an issue, if I'm not trying to make video calls?  And if it is, how can I check that my video card has Xv support? (it's all Chinese to me!)
 I've looked at Synaptic to see if the **software requirements** listed on the Linux download page [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/) are met:
  
[LIST]
[*]Qt 4.2.1+ 												
[*]D-Bus 1.0.0 						
[*]libasound2 1.0.12 					
[*]PulseAudio 0.9.10+ (optional) 			
[*][COLOR=#800080]PulseAudio 0.9.15+ (optional 	recommended) [/COLOR]	
[/LIST]
 
Below are the Synaptic packages installed both in **8.04** (my preferred Ubuntu release for the time being) and also in **9.04** (mainly for comparison purposes for those “in the know”, but I'm not too optimistic on this release, as it's not even mentioned on the Skype Linux download page). In 8.04 I installed 2 packages **manually** through Synaptic (labelled as such below), as they seemed relevant to me. But I tried using Skype before and after EACH of these manual installations.  For each 8.04 and 9.04 release below I also mention the packages which are NOT installed which don't appear to be related to getting Skype to work (so please let me know if you think I DO need to install any of these).
 [SIZE=2]But before you look at all of the below, it seems to me that the last software listed [/SIZE][SIZE=2][COLOR=#800080]PulseAudio 0.9.15+ (optional recommended) [/COLOR][/SIZE][SIZE=2]is the most likely candidate to be causing a problem: it isn't listed in Synaptic in either 8.04 or 9.04.  What do you think? I downloaded [/SIZE][SIZE=2][COLOR=#800080]PulseAudio 0.9.15 [/COLOR][/SIZE][SIZE=2]from their [/SIZE]website (I hesitated about downloading the latest version 0.9.19), I extracted the file and then opened it but I can't find a way to open it. [SIZE=3]
[/SIZE]


 [COLOR=#ff0000][SIZE=4]	Qt 4.2.1+ [/SIZE][/COLOR] 
 [SIZE=4]**Ubuntu 8.04**[/SIZE]
[SIZE=3]**INSTALLED **[/SIZE]qt4-qtconfig 4.3.4-0ubuntu3.1 [COLOR=#ff0000](INSTALLED MANUALLY)[/COLOR]
**NOT installed**. The only other packages listed in Synaptic are:
 * Qt 4 API documentation;  Qt 4 designer and Qt 4 development tool packages.



 [SIZE=4]**Ubuntu 9.04**[/SIZE]
 [SIZE=3]**INSTALLED **[/SIZE]qt4-qtconfig 4.5.0-0ubuntu4.2. 
**NOT installed: **
[SIZE=1]S[/SIZE][SIZE=1]everal other “qt4.5.0-0ubuntu4.2 ” packages ( Qt 4 qmake Makefile generator tool, doc, dev-tools, designer and demonstration).[/SIZE]
 [SIZE=3]

	[/SIZE][COLOR=#ff0000][SIZE=4]D-Bus 1.0.0 [/SIZE][/COLOR][SIZE=3]	
[/SIZE][SIZE=4]**Ubuntu 8.04**[/SIZE][SIZE=3]
[/SIZE][SIZE=3][B]INSTALLED 
[/B][/SIZE]d-Bus 1.1.2.0-1ubuntu3.3
dbus-x11 1.1.20-1ubuntu3.3(simple interprocess messaging system (X11 deps))  
 
[SIZE=3]**NOT installed**[/SIZE][SIZE=3]: [SIZE=2]dbus-1-doc (documentation)[/SIZE][/SIZE]
 [SIZE=3]
[/SIZE][SIZE=4]**Ubuntu 9.04**[/SIZE][SIZE=3][B]
INSTALLED [/B][/SIZE][SIZE=3][SIZE=2]d-Bus 1.2.12-0 ubuntu2.1 (simple process messaging system).  [/SIZE]

[/SIZE][SIZE=3]**NOT installed:**[/SIZE][SIZE=3]
[SIZE=2]* dbus-1-doc (documentation)[/SIZE][/SIZE]
 [SIZE=3][SIZE=2]* dbus-java-bin (Java Binaries[/SIZE])

[/SIZE]


 [COLOR=#ff0000][SIZE=4]	libasound2 1.0.12 [/SIZE][/COLOR][COLOR=#ff0000][SIZE=3]
[/SIZE][/COLOR][COLOR=#000000][SIZE=4]**Ubuntu 8.04**[/SIZE][/COLOR][COLOR=#ff0000][SIZE=3]
[/SIZE][/COLOR]**INSTALLED:** 
libasound2 1.0.15-3ubuntu4 (ALSA library)
libasound2-plugins 1.0.15-1ubuntu3(ALSA library additional plugins) [COLOR=#ff0000]INSTALLED MANUALLY[/COLOR]
 

 [SIZE=3]**NOT installed:**[/SIZE]
 [SIZE=2]libasound2-dev (Development files)
libasound2-doc  (developer documentation)
[/SIZE]
[SIZE=4]**Ubuntu 9.04**[/SIZE]
 [SIZE=3]**INSTALLED**: 
[SIZE=2]* libasound2 1.0.18-1ubuntu9 (shared library for ALSA applications)[/SIZE][/SIZE]
 [SIZE=3][SIZE=2]* libasound2-plugins 1.0.18-1ubuntu4 (ALSA library additional plugins)[/SIZE]
[/SIZE]


  [SIZE=3]**NOT installed**: (As 8.04 above)
[/SIZE]


 [COLOR=#ff0000][SIZE=4]	PulseAudio 0.9.10+ (optional) [/SIZE][/COLOR][SIZE=3]
[/SIZE][COLOR=#000000][SIZE=4]**Ubuntu 8.04**[/SIZE][/COLOR][SIZE=3]
[/SIZE][SIZE=3]**INSTALLED (ALL 0.9.10-1ubuntu1.1 ): **[/SIZE] 
 pulseaudio  **0.9.10-1ubuntu1.1** (PulseAudio sound server)
 pulseaudio-esound-compat  (PulseAudio ESD compatibility layer)
 pulseaudio-module-gconf  (GConf module for PulseAudio sound server)
 pulseaudio-module-hal  (HAL device detection module for PulseAudio sound server)
 pulseaudio-module-x11  (X11 module for PulseAudio sound server)
 pulseaudio-utils  (Command line tools for the PulseAudio sound server)
 


 [SIZE=3]**NOT installed (ALL 0.9.10-1ubuntu1.1 )**:[/SIZE]
 [SIZE=2]pulseaudio-dbg (PulseAudio sound server detached debugging symbols)[/SIZE]
 [SIZE=2]pulseaudio-esound-compat-dbg (PulseAudio ESD compatibility layer debugging symbols)[/SIZE]
 [SIZE=2]pulseaudio-module-gconf-dbg (GConf module for PulseAudio sound server debugging symbols)[/SIZE]
 [SIZE=2]pulseaudio-module-hal-dbg (HAL module for PulseAudio sound server debugging symbols)[/SIZE]
 [SIZE=2]pulseaudio-module-lirc (lirc module for PulseAudio sound server)[/SIZE]
 [SIZE=2]pulseaudio-module-lirc-dbg (lirc module for PulseAudio sound server debugging symbols)[/SIZE]
 [SIZE=2]pulseaudio-module-x11-dbg (X11 module for PulseAudio sound server debugging symbols)[/SIZE]
 [SIZE=2]pulseaudio-module-zeroconf (Zeroconf module for PulseAudio sound server)[/SIZE]
 [SIZE=2]pulseaudio-module-zeroconf-dbg (Zeroconf module for PulseAudio sound server debugging symbols)[/SIZE]
 [SIZE=2]pulseaudio-utils-dbg (PulseAudio command line tools detached debugging symbols)[/SIZE]
 
[SIZE=4]**Ubuntu 9.04**[/SIZE][SIZE=4]
[/SIZE][SIZE=3]**INSTALLED (ALL 1.0.9.14-0ubuntu20.2 ): **[/SIZE][SIZE=3]
[SIZE=2]* pulseaudio [/SIZE][/SIZE][SIZE=2]**1.0.9.14-0ubuntu20.2**[/SIZE][SIZE=2] (PulseAudio sound server)
* pulseaudio-esound-compat (PulseAudio ESD compatibility layer)[/SIZE]
 [SIZE=2]* pulseaudio-module-gconf  (GConf module for PulseAudio sound server)[/SIZE]
 [SIZE=3][SIZE=2]* pulseaudio-module-hal  (HAL device detection module for PulseAudio sound server)
* pulseaudio-module-x11 (X11 module for PulseAudio sound server)
* pulseaudio-utils  (Command line tools for the PulseAudio sound server)
[/SIZE]
[/SIZE][SIZE=3]**Pulseaudio 1.0.9.14-0ubuntu20.2 NOT installed:**[/SIZE][SIZE=3]
As 8.04 above.

I'd be very grateful for any help, particularly for replies which bear in mind that my technical knowledge :confused: is practically zero!  For this reason and as video calling isn't paramount for me, do you think it would be easier to download an older Linux version of Skype? If so, which one?[/SIZE]
 [SIZE=3]

[/SIZE]


 


 


 


 


 


 [SIZE=3]
[/SIZE]


 


 [SIZE=3]
[/SIZE]

---

### Post by phillw on 2009-10-23
> **donsy said:**
> If anyone has had success with Skype 2.1.0.47 in Jaunty can you please tell me your sound settings and what webcam you're using? Thanks.


[http://ubuntuforums.org/showthread.php?t=1195190](http://ubuntuforums.org/showthread.php?t=1195190)

He did, try the method he was told to follow.

I have skype on, but not had chance to really try it out yet (sound & vid test works okay)

Phill.

---

### Post by donsy on 2009-10-23
> **phillw said:**
> [http://ubuntuforums.org/showthread.php?t=1195190](http://ubuntuforums.org/showthread.php?t=1195190)

He did, try the method he was told to follow.

I have skype on, but not had chance to really try it out yet (sound & vid test works okay)

Phill.

No, I never got it to work, so I uninstalled it and subsequently use the Windows version on my dual-boot system.

---

### Post by greenewbie on 2009-10-24
Ok, thanks very much Donsy and Phillw for your help .  My guess now is that I'd be better off going back to a previous version of Linux Skype.....so I'll look up the forum more to see Skypers' experiences

---

### Post by phillw on 2009-10-24
Hi,

This link, at least, lets you know where skype are about up to ..

[http://share.skype.com/sites/garage/2009/09/skype_21_beta_for_linux.html](http://share.skype.com/sites/garage/2009/09/skype_21_beta_for_linux.html)

I'll have a play with it soon, but am a bit tied up with work atm. I'm suprised no-one has it working.

Regards,

Phill.

---

### Post by greenewbie on 2009-10-25
Thanks Phill, I looked at the link you posted but most of it is beyond me I'm afraid!.......I read with great interest however that many of the feature disparities between the Windows and Linux versions have now been closed (high quality video even which I didn't know about), GREAT NEWS! :guitar:
But with my slow broadband line I suspect that low quality video would be ample for me (if it avoids all the technical problems of the latest Beta release, that would be great). As I'm starting from scratch again with Skype, at the moment I don't know which Ubuntu release (8.04, 8.10 or 9.04) to try on which Skype version.  I'm planning to trawl through forum postings today, so any help in the meantime would be most welcome

---

### Post by phillw on 2009-10-26
I'm soz, I'm still tied with work - I'll try and have a go at it this sometime this week.

Have u had a look at this thread yet ?

[http://beginlinux.wordpress.com/2009/04/28/installing-skype-on-ubuntu-904/](http://beginlinux.wordpress.com/2009/04/28/installing-skype-on-ubuntu-904/)

I've lost track of the ones I'm following !!!

They seem to be having various degrees of  success and, importantly, it seems to be a 'live' thread
and not an archive.

Regards,

Phill.

---

### Post by AnthonyPapillion on 2009-10-26
It seems that Skype is an ongoing problem for Linux users as evidenced by the posts on their own forum. Basically, the consensus is that it is unreliable and nearly completely unusable on Linux. In my situation, I can do text messaging (sometimes, and sometimes, that crashes the program) and I can make outbound calls. BUT when the other side answers and I say anything, that immediately crashes the program.

IMHO Skype does not really have a Linux client. It's a sad state but I wish they would take Linux more seriously - especially with the slew of netbooks coming out.

---

### Post by Nick Brohman on 2009-10-26
> **phillw said:**
> [http://ubuntuforums.org/showthread.php?t=1195190](http://ubuntuforums.org/showthread.php?t=1195190)

He did, try the method he was told to follow.

I have skype on, but not had chance to really try it out yet (sound & vid test works okay)

Phill.
  
I used the terminal commands in that thread to download [COLOR=Red]2.0.0.72[/COLOR] & have it working fine with good video & reasonably good audio.
[COLOR=Red]
Getting Skype from the repositories will give you all of the dependencies needed to run it & is the easiest way of installing it.[/COLOR]
[COLOR=Indigo]
I had downloaded 2.1.0.47 [/COLOR]but had audio problems which I solved following another thread although the full list of pkgs.to get from Synaptic Manager has to be edited or Skype will disappear.

[COLOR=Red]Read the full post before doing anything[/COLOR]. I'm sorry I'm not up to scratch with links but "Sound Solutions in Jaunty"  should give you the thread & I think markbuntu is the poster.

[COLOR=Red]Downloading from Skype needs extra work[/COLOR]

I have my Volume Control sound theme turned off, no surround sound, no mic boost, just Master, PCM, Front, Front Mic,Line-In & Mic enabled. The device is my HDA NVidea (Alsa mixer) and, as I write, I'm talking to a mate in Nth. Qld.

The Sound Device in Skype needs to be set to your card, as above, not default.

I use Mic in options & use a Logitec headset but will get a stand-alone mic as I don't seem to get any audio from either camera (not yet anyway...more work...)

Any scratchiness/ garble is dedendent on where you are in relation to the mic but I see threads where I'll look for possible solutions.

The best test is calling someone so that you can get feedback as to your settings etc,,

The only thing I don't have is my litte window showing self but I know what I look like so that is no problem. My mate is getting my video just fine.

I have two cameras:- a Micordia 0c45:62e0 & Microeletrical 0ac8:3o3b & both work well.

Follow the tip in Skype help (FAQ), to get better motion from the camera & use Cheese to set your resolution. I have 640x480 on one cam & 800x600 on the other & find that to be good for transmission/real time motion.

I use Cheese not Camerama as I found the latter too hard to work out.

I also found that a little adjustment with the focus ring is needed as well.

I am a PC novice but have found that copy & paste is the best skill I have attained. Copy & paste the commands in the link, one at a time, pressing enter/return each time.

You will have to enter your password for the first command & then y if you want to go ahead. C&P the second line, enter, then sit back & watch Skype be installed. Better still, have a coffee break & play shisen -sho for 30 mins.

This is my experience and it worked for me.

Cheers,  

Nicko

**The Thread referred to is "Jaunty 9.04 Sound Solutions" & markbuntu is the poster. **

---

### Post by greenewbie on 2009-10-28
Thanks very much for your help guys! And thanks Nicko for your detailed posting above; that encouraged me to try out the terminal commands posted in the above link.  I was astonished to find that I successfully downloaded Skype [COLOR=Red]2.0.0.72 [COLOR=Black](I expected to find the current [/COLOR][/COLOR][COLOR=Indigo]2.1.0.47 [COLOR=Black]version).  The result so far is that when I used "Test sound" and the Echo Test[/COLOR][/COLOR][COLOR=Red][COLOR=Black], the sound (including my replayed voice in the latter) is audible but unfortunately bad hiss and crackle when somebody is speaking (which stops during pauses in the speaking).
I tried all the options available in the Skype program for my sound card (curious because there's only one sound card installed on my PC) but it didn't make any difference.  My aim now is to get reasonable sound on [/COLOR][/COLOR][COLOR=Black]2.0.0.72 (I'll look into video later). At the moment this is installed on my main HDD in 8.04 Hardy. But I'd like to make a fresh install of Jaunty 9.04 either on another HDD (I have 2 others and I've got myself into quite a pickle on both of them) or on a separate partition on my main one (although I set up partitions when I formatted it recently, I don't know how to do that yet, I may have to shout for help on that in a separate posting!)
Well, this is quite a war......I'll keep you posted on the next battles........
John ;)
[/COLOR]

---

### Post by Psycho.mario on 2009-10-28
If your webcam isn't working, try starting skype with this:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
```
That command made my webcam work.

---

### Post by diablo75 on 2009-10-28
I had to revert back to the previous version.  The sound in 2.1 didn't work (my mic recorded static; a bug on Skype's end apparently that we'll have to wait on to see fixed).

---

### Post by matthewbpt on 2009-10-28
Funny, I installed skype 2.1 and it worked immediately with no trouble at all, much better than it used to work =S I'd recomend installing the package 'padevchooser' then going to Applications > Sound and Video > PulseAudio Volume Control. There should be a "Recording" tab, I suspect that pulseaudio is using the wrong recording source. While in a call on skype go to the recording tab and you should see skype listed recording sound, and arrow next to it, click on the arrow and you can change the recording source on the fly, change it to your microphone. (Also in the Input Devices tab you can set which device is the default recording device, change that too)

---

### Post by Nick Brohman on 2009-10-28
> **greenewbie said:**
> Thanks very much for your help guys! And thanks Nicko for your detailed posting above; that encouraged me to try out the terminal commands posted in the above link.  I was astonished to find that I successfully downloaded Skype [COLOR=Red]2.0.0.72 [COLOR=Black](I expected to find the current [/COLOR][/COLOR][COLOR=Indigo]2.1.0.47 [COLOR=Black]version).  The result so far is that when I used "Test sound" and the Echo Test[/COLOR][/COLOR][COLOR=Red][COLOR=Black], the sound (including my replayed voice in the latter) is audible but unfortunately bad hiss and crackle when somebody is speaking (which stops during pauses in the speaking).
I tried all the options available in the Skype program for my sound card (curious because there's only one sound card installed on my PC) but it didn't make any difference.  My aim now is to get reasonable sound on [/COLOR][/COLOR][COLOR=Black]2.0.0.72 (I'll look into video later). At the moment this is installed on my main HDD in 8.04 Hardy. But I'd like to make a fresh install of Jaunty 9.04 either on another HDD (I have 2 others and I've got myself into quite a pickle on both of them) or on a separate partition on my main one (although I set up partitions when I formatted it recently, I don't know how to do that yet, I may have to shout for help on that in a separate posting!)
Well, this is quite a war......I'll keep you posted on the next battles........
John ;)
[/COLOR]
John,

It's all about experiment with the Volume Control

One thing I forgot to mention is that I had downloaded Restricted Ubuntu from Synaptic manager before getting Skype.

As far as the latest Skype, I had followed a thread titled "Jaunty 9.04 Sound Solutions" by markbuntu to get it working but trying to get two screens going, I lost my nVidea driver & had to do a fresh install. 

I'm really good at ruining my setup but mistakes like that are giving me knowledge

When you work out how to partition, let me know. That's what has caused me to get Skype from the command line.

I'm glad I could help as I have been helped in other matters in these forums.

It's like the old story, help others as you would have them help you.

BTW my computing experience is zilch and Linux is the only OS I have ever used exceot for one or two weeks of MeSser which was a year too long.

Cheers.....Nicko :o

---

### Post by drif13 on 2009-11-05
> **matthewbpt said:**
> Funny, I installed skype 2.1 and it worked immediately with no trouble at all, much better than it used to work =S I'd recomend installing the package 'padevchooser' then going to Applications > Sound and Video > PulseAudio Volume Control. There should be a "Recording" tab, I suspect that pulseaudio is using the wrong recording source. While in a call on skype go to the recording tab and you should see skype listed recording sound, and arrow next to it, click on the arrow and you can change the recording source on the fly, change it to your microphone. (Also in the Input Devices tab you can set which device is the default recording device, change that too)

[matthewbpt]("http://ubuntuforums.org/member.php?u=574872"), you are 100% correct, thanks for your suggestion. Now I get voice audible. Cheers

---

### Post by philak on 2009-11-05
Hi. I spent a bunch of time reading, searching and trying various suggestions. A YouTube vid mentioned Ubuntu Tweak. I installed that and removed Skype via Synaptic package manager. Then I installed Skype thru Tweak and all is well. Hope this helps.

---

### Post by yottabit on 2010-01-24
> **Psycho.mario said:**
> If your webcam isn't working, try starting skype with this:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
```
That command made my webcam work.

You are awesome! I've had a few issues here getting my Logitech Quickcam Pro 5000 to work with Skype 2.1.0.81.

First, even the test video wouldn't work. Nothing, nada. Yet Ekiga would work fine with it (although Ekiga isn't very usable to me since more often than not the video seems to 'loopback' and the parties only see themselves instead of the opposite party...).

I also have a Logitech Quickcam 4000 and it worked fine with Skype, so I was a little annoyed since the 5000 has much higher video quality and resolution...

Your command-line trick to specify the V4L compatibility library seems to do the trick for my 5000! Thanks so much; this is the first mention I've seen of this trick!!

---

### Post by Francewhoa on 2010-03-14
The following worked for me [http://ubuntuforums.org/showpost.php?p=8919096&postcount=6](http://ubuntuforums.org/showpost.php?p=8919096&postcount=6)

---

### Post by ken78724 on 2010-03-15
Many thanks Nick. I downloaded 2.1.0.47 [wouldn't work]& followed w/synaptic package manager w/skype updates. I got a crisp reply voice by calling a buddy. He could respond but my Mic failed. So, I am hunting what'll make it work. Below I saw a post; will try to post after a try out this week.

I feel the full download, which did not extract and run but did run when I did the update means synaptic manager has a cure we need to study so I bet the mic ? is solvable.

---

