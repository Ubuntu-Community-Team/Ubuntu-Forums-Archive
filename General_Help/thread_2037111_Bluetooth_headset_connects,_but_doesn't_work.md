---
title: "Bluetooth headset connects, but doesn't work"
date: 2012-08-03
forum: General Help
---

### Post by UnknownDiety on 2012-08-03
I've got a bluetooth adapter plugged into my laptop. I can receive/send files to and from cellphones just fine, but whenever I try to use my bluetooth headset it simply connects to the adapter and then that's it.

It doesn't output any sound to the speaker of the headset and it doesn't input any sound via the microphone.

The headset connects and actually inputs/outputs sound if I'm on Windows, but when using Ubuntu 12.04 it won't input/output anything once it connects to the adapater.

---

### Post by gordintoronto on 2012-08-03
Run system settings, sound. What does it show for input and output? On the Output tab, what "connector" is shown?

---

### Post by UnknownDiety on 2012-08-06
> **gordintoronto said:**
> Run system settings, sound. What does it show for input and output? On the Output tab, what "connector" is shown?

Output Tab:
Digital Output (S/PDIF) Built-in Audio
Analog Output Built-in Audio

Input Tab:
Microphone Built-in Audio
Internal Microphone Built-in Audio

The bluetooth headset doesn't show up in the output or input tabs for some reason.

---

### Post by jolyon on 2012-09-09
I've got the same problem.

Running Ubuntu 12.04 on a Toshiba portege Z830. The bluetooth connects well to my old motorola HT820 headset - sounds great.

My Nokia BH-905 headset claims to be connected, but in the sound output tab it doesn't appear at all. In the bluetooth settings tab it claims to be a 'Headset', same as the motorla HT820.

Any help would be much appreciated.

---

### Post by UnknownDiety on 2012-09-30
To be able to get the bluetooth headset to show up in the sound settings I had to reinstall ubuntu.

Though even with it showing it doesn't play any sound when I hit the test sound button and my microphone didn't record sound whenever I tried to test it.

---

### Post by UnknownDiety on 2012-10-01
Output:
[img]http://i.imgur.com/RaQGq.png[/img]

Input:
[img]http://i.imgur.com/HEsc7.png[/img]

Can't hear anything and the microphone doesn't pick up anything.

---

### Post by UnknownDiety on 2012-11-03
Bump

---

### Post by quequotion on 2012-11-03
> **UnknownDiety said:**
> I've got a bluetooth adapter plugged into my laptop. I can receive/send files to and from cellphones just fine, but whenever I try to use my bluetooth headset it simply connects to the adapter and then that's it.

It doesn't output any sound to the speaker of the headset and it doesn't input any sound via the microphone.

The headset connects and actually inputs/outputs sound if I'm on Windows, but when using Ubuntu 12.04 it won't input/output anything once it connects to the adapater.

I also have [a thread about this]("http://ubuntuforums.org/showthread.php?p=12319168"), and [a report on launchpad for this bug]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1065380").

This needs to be addressed in bluez (the bluetooth driver stack), but the bugtracker for bluez is MIA and last I tried talking to the bluez team in IRC, I was told it's a pulseaudio problem (*it's not*) and to take it to that development team.

When the headset connects, it may have several *bluetooth profiles* (distinguished from *audio profiles*) available, like "input" (for the buttons), "headset" (for telephony), and "audio sink" (for high-fidelity audio devices). Theoretically, bluez should connect to both the "headset" and "audio sink" profiles when a paired headset connects.

This is not happening. The device is recognized and connected, but no bluetooth profile is ever negotiated. If you install **blueman**, it provides an indicator applet that will allow you to take this step manually; **gnome-bluetooth** is useless.

You will also need to make some changes to pulseaudio's configuration (see my thread for details) to enable automatically switching the audio over to the headset and back. *This is the part that gets the first issue blamed on pulseaudio but it isn't the same issue at all.*
Once configured properly, pulseaudio can swtich the audio stream to the bluetooth headset and back to the speakers very well and with no hands-on interaction. Unfortunately, since bluez never provides a bluetooth profile, and thus never creates an audio device interface, pulseaudio is never informed that a headset has been connected. 

blueman has options to select the bluetooth profile manually, which works around the problem, but requires that you be at your computer and use the mouse or keyboard--there is no way to switch audio to and from a bluetooth headset *hands-free* in Ubuntu.

---

### Post by UnknownDiety on 2012-11-05
After doing all those changes in that  rundown post I still don't get any sound in my bluetooth headset.

Whenever I click the Blueman Icon > Devices > Right Click Headset and hit Connect to Input Service it tells me" Connection Failed: Operation is not supported "

The Right Click and Connect to Headset service connected and I can see the headset in the Output/Input tabs of the sound settings, but again there's no output through the headsets speaker or input from the microphone.

The only audio profiles for my headset (or ones that show up) are off & Telephony Duplex (HSP/HFP)
I've got it set to Telephony Duplex.

I've tried without the Headset Emulation enabled in the Local Services of blueman and I've tried with it enabled. (Rebooting after changing the setting)

I don't know what you mean by bluetooth profiles. Like it may show up as multiple devices in blueman's device list? If that's what you mean it doesn't. It only shows up as a single device.

---

### Post by quequotion on 2012-11-05
> **UnknownDiety said:**
> After doing all those changes in that  rundown post I still don't get any sound in my bluetooth headset. Ahh... please read carefully! You probably don't need to make *all* of those changes. Particularly, I have redacted one *after* replying to your thread.> I don't know what you mean by bluetooth profiles. Like it may  show up as multiple devices in blueman's device list? If that's what you  mean it doesn't. It only shows up as a single device.It should  appear as a single device, but may have several profiles ("*Input Service*", "*Headset Service*", "*Audio Sink*",  etc...) which determine how the computer will interact with the device  (as a remote control, a telephone headset, a set of headphones, etc). These are the right-click selections you found in blueman.> Whenever I click the Blueman Icon > Devices > Right Click Headset and hit Connect to Input Service it tells me" Connection Failed: Operation is not supported " "*Input Service*" is the bluetooth profile for remote control functions (buttons, not sound) and probably isn't what you want. I don't know if it even works.> The Right Click and Connect to Headset service connected and I can see the headset in the Output/Input tabs of the sound settings, but again there's no output through the headsets speaker or input from the microphone. "*Headset Service*" is the profile for telephony function (low-fidelity audio, microphone input). I don't have any software to test this service with, but it probably won't be used for audio output automatically because it's not intended for general-purpose audio. If you want to use telephony software, *you may need to configure the settings in that software to use the headset's speaker and microphone, rather than the default output and input*.  It's also possible to configure pulseaudio to use the microphone and speaker on the headset as the default input and output, but that's probably not what you want in the long run.

"*Audio Sink*" provides a general-purpose audio device (high-fidelity, stereo if available, no microphone input). Once activated, pulseaudio will switch to this device automatically when configured to do so (cut off the main speakers and activate the headset speaker(s)). If you want to use your headphones to listen to music, videos, or whatever, you need this profile. 

Unfortunately, something is wrong with the bluetooth driver in Ubuntu (bluez). The driver should automatically provide both "*Headset Service*" and "*Audio Sink*" as audio devices for the sound subsystem (pulseaudio) to configure,* but it does not*. You will have to select one of the two, manually, in blueman.

My description of this in the other thread is perhaps overly technical. *There's another, distinct, problem with pulseaudio*: the default configuration does not include the settings to switch from the main speakers to your headset when you connect it. For this, you need to edit the settings file **/etc/pulse/system.pa **and add, at the end of the file:```

### Automatically redirect to newly available sinks
load-module module-switch-on-connect
```Keep in mind, even with pulseaudio configured and working correctly, Ubuntu will not automagically redirect audio to your headset because bluez is broken. When you connect the headset, you must click one of the audio profiles in blueman, and then pulseaudio will automatically switch over the sound.> The only audio profiles for my headset (or ones that show up) are off & Telephony Duplex (HSP/HFP)
I've got it set to Telephony Duplex.Probably because bluez doesn't provide the other devices for pulseaudio to profile, but make sure to check your headset's manual/box for what it should be supporting.> I've tried without the Headset Emulation enabled in the Local Services of blueman and I've tried with it enabled. (Rebooting after changing the setting)I don't think that is what you need...
___________________________________

So it goes like this:
0a. Pair your headset
0b. Configure pulseaudio to use module-switch-on-connect

1. Activate the headset.
2. Once connected, right-click to choose a profile in blueman.*
3a. For "*Headset Service*" you need to setup your telephony programs to use the headset's speaker and mic.
3b. For "*Audio Sink*" you need to do nothing, audio will be redirected to your headphones.
4. Deactivate the headset.
5. Audio should revert to the main speakers and microphone.


* This (2.)  would not be necessary if bluez was working properly.

---

### Post by UnknownDiety on 2012-11-05
> **quequotion said:**
> Ahh... please read carefully! You probably don't need to make all of those changes. Particularly, I have redacted one after replying to your thread.

Well by doing all of them I meant I meant all of them but this one as it's the only one that I saw was told not to be done:

    ### Automatically detect bluetooth devices load-module module-bluetooth-discover #Maybe this does more harm than good

> It should appear as a single device, but may have several profiles ("Input Service", "Headset Service", "Audio Sink", etc...) which determine how the computer will interact with the device (as a remote control, a telephone headset, a set of headphones, etc). These are the right-click selections you found in blueman.

Well it's showing as just a single device, but it only has two profiles. Input & Headset. It doesn't have the Audio Sink one.

> "Input Service" is the bluetooth profile for remote control functions (buttons, not sound) and probably isn't what you want. I don't know if it even works.

So I don't really need to worry about the Input one then.


> "Headset Service" is the profile for telephony function (low-fidelity audio, microphone input). I don't have any software to test this service with, but it probably won't be used for audio output automatically because it's not intended for general-purpose audio. If you want to use telephony software, you may need to configure the settings in that software to use the headset's speaker and microphone, rather than the default output and input. It's also possible to configure pulseaudio to use the microphone and speaker on the headset as the default input and output, but that's probably not what you want in the long run.

I've mainly been trying to get it to work with skype, but the only option I end up getting in skype's options for the Microphone, Speakers, and Ringing is PulseAudio Server (local).

> "Audio Sink" provides a general-purpose audio device (high-fidelity, stereo if available, no microphone input). Once activated, pulseaudio will switch to this device automatically when configured to do so (cut off the main speakers and activate the headset speaker(s)). If you want to use your headphones to listen to music, videos, or whatever, you need this profile.

Unfortunately, something is wrong with the bluetooth driver in Ubuntu (bluez). The driver should automatically provide both "Headset Service" and "Audio Sink" as audio devices for the sound subsystem (pulseaudio) to configure, but it does not. You will have to select one of the two, manually, in blueman.

Ahh. If I could get it to have an Audio Sink profile and to actually function it'd be nice, but I'm mainly wanting to get the Headset service working properly.

> My description of this in the other thread is perhaps overly technical. There's another, distinct, problem with pulseaudio: the default configuration does not include the settings to switch from the main speakers to your headset when you connect it. For this, you need to edit the settings file /etc/pulse/system.pa and add, at the end of the file:```

### Automatically redirect to newly available sinks
load-module module-switch-on-connect
```


I've already got that added at the bottom even with this at the end of the second line: ```
#Probably necessary... probably...
```

> Keep in mind, even with pulseaudio configured and working correctly, Ubuntu will not automagically redirect audio to your headset because bluez is broken. When you connect the headset, you must click one of the audio profiles in blueman, and then pulseaudio will automatically switch over the sound.

Talking about configuring it from editing the files that were told to be changed in that other thread you linked? Because I've followed the steps except for the one that is said to cause problems instead of helping. After doing those configurations I've tried opening Blue's Devices and then connecting to the headset service. Sometimes it won't connect on the first try, but sometimes it will. Whenever it does connect I go to the Sound Settings and set everything to my headset so that I can try to use skype, but nothing works. Not the speaker of the headset or the microphone.

> Probably because bluez doesn't provide the other devices for pulseaudio to profile, but make sure to check your headset's manual/box for what it should be supporting.

The manual says it can be used with PS3 or for Mobile Phone. It doesn't actually mention any kind of profile other than that though from what I understood. It's actually the Sony Official PS3 Headset Model CECH-0075. On Windows both the Headset's speaker and microphone work fine. I can talk to people or I can listen to music with it if I so choose without being stuck right next to my computer.

> I don't think that is what you need...

Ahh ok. I've disabled it, but whether it's enabled or not I've seen no difference. I restarted after enabling and again after disabling.

> 
___________________________________

So it goes like this:
0a. Pair your headset
0b. Configure pulseaudio to use module-switch-on-connect

1. Activate the headset.
2. Once connected, right-click to choose a profile in blueman.*
3a. For "Headset Service" you need to setup your telephony programs to use the headset's speaker and mic.
3b. For "Audio Sink" you need to do nothing, audio will be redirected to your headphones.
4. Deactivate the headset.
5. Audio should revert to the main speakers and microphone.


* This (2.) would not be necessary if bluez was working properly.

Assuming 0b means adding that one line to the bottom of /etc/pulse/system.pa: ```
### Automatically redirect to newly available sinks
load-module module-switch-on-connect #Probably necessary... probably...
```


I can't get the sound to work with Headset service (or I don't know how to get it to work?) and I don't have an Audio Sink profile.

Hopefully there's I haven't misunderstood anything, but if I have I apologize.

---

### Post by quequotion on 2012-11-06
> **UnknownDiety said:**
> Well by doing all of them I meant I meant all of them but this one as it's the only one that I saw was told not to be done:

    ### Automatically detect bluetooth devices load-module module-bluetooth-discover #Maybe this does more harm than good Nice catch. I was worried about that one especially. Unfortunately few of these configuration options are adequately documented, or documented at all. I'm also going on advice I picked up in various forums (mostly gentoo's and archlinux's).> Well it's showing as just a single device, but it only has two profiles. Input & Headset. It doesn't have the Audio Sink one.A ha! I dug up the manual for this. That headset only supports HSP and HFP profiles ("*Headset Service*"), so no "*Audio Sink*" (the A2DP profile). I suppose it's designed for use to communicate in games *while* listening to the game audio (sfx, music, etc) through main speakers.> I've mainly been trying to get it to work with skype, but the only option I end up getting in skype's options for the Microphone, Speakers, and Ringing is PulseAudio Server (local).I've not used skype for a while. I'll take a look at this if I can find the time. Perhaps skype doesn't look deeply into your audio configuration and relies on pulseaudio to take care of the details--which probably means reconfiguring pulseaudio with **paman** and **pavucontrol**.> I've already got that added at the bottom even with this at the end of the second line: ```
#Probably necessary... probably...
```OK, probably good then. Again, it's not well documented. > I've tried opening Blue's Devices and then connecting to the headset service. Sometimes it won't connect on the first try, but sometimes it will. Whenever it does connect I go to the Sound Settings and set everything to my headset so that I can try to use skype, but nothing works. Not the speaker of the headset or the microphone. That's not good. Maybe something is wrong with the volume configuration? take a look at **alsamixer** in a terminal. It will open with a view of your default sound card's volume levels, but you can select your headset's by pressing **[F6]** and selecting it from the menu.> The manual says it can be used with PS3 or for Mobile Phone. It doesn't actually mention any kind of profile other than that though from what I understood. It's actually the Sony Official PS3 Headset Model CECH-0075.Take a look at the last page for the "Product Specifications". > On Windows both the Headset's speaker and microphone work fine. I can talk to people or I can listen to music with it if I so choose without being stuck right next to my computer.I think this is possible in linux, and the configuration options are available for bluez, alsa and pulseaudio; but the default configurations are not good enough in Ubuntu, and the drivers aren't as advanced. Things are getting better, but gradually.> Ahh ok. I've disabled it, but whether it's enabled or not I've seen no difference. I restarted after enabling and again after disabling.Yeah, I don't really know anything about the headset emulation myself.> Hopefully there's I haven't misunderstood anything, but if I have I apologize.Not at all! Forgive *me*, I'm actually not used to communicating this well here.

---

### Post by UnknownDiety on 2012-11-06
> **quequotion said:**
> Nice catch. I was worried about that one especially. Unfortunately few of these configuration options are adequately documented, or documented at all. I'm also going on advice I picked up in various forums (mostly gentoo's and archlinux's).

Sounds like it's good advice thus far.

> A ha! I dug up the manual for this. That headset only supports HSP and HFP profiles ("Headset Service"), so no "Audio Sink" (the A2DP profile). I suppose it's designed for use to communicate in games *while* listening to the game audio (sfx, music, etc) through main speakers.Yeah It's same shape/design as a cellphone bluetooth headset.

> I've not used skype for a while. I'll take a look at this if I can find the time. Perhaps skype doesn't look deeply into your audio configuration and relies on pulseaudio to take care of the details--which probably means reconfiguring pulseaudio with **paman** and **pavucontrol**.I wouldn't have the slightest clue of how to reconfigure them or I guess what would be needed.

> OK, probably good then. Again, it's not well documented.Ahh. Maybe they'll add more documentation down the road.

> That's not good. Maybe something is wrong with the volume configuration? take a look at alsamixer in a terminal. It will open with a view of your default sound card's volume levels, but you can select your headset's by pressing [F6] and selecting it from the menu.The only things that show up in the Sound Card part of AlsaMixer are - (default), 0 HDA Intel, and enter device name.

> Take a look at the last page for the "Product Specifications".Ahh. I just figured it would've been on the page where it told how to use it with a phone. Now I know to always check the product specifications page.

> I think this is possible in linux, and the configuration options are available for bluez, alsa and pulseaudio; but the default configurations are not good enough in Ubuntu, and the drivers aren't as advanced. Things are getting better, but gradually.That's encouraging to see.

> Yeah, I don't really know anything about the headset emulation myself.I don't either.

> Not at all! Forgive me, I'm actually not used to communicating this well here.I think you've been doing swell. I just know sometimes I misread things so I was making sure.

---

### Post by UnknownDiety on 2012-11-07
Bump

---

### Post by UnknownDiety on 2012-11-08
Bump

---

### Post by UnknownDiety on 2012-11-09
Bump

---

### Post by AleveSicofante on 2012-11-10
> **UnknownDiety said:**
> Output:
[IMG]http://i.imgur.com/RaQGq.png[/IMG]

Input:
[IMG]http://i.imgur.com/HEsc7.png[/IMG]

Can't hear anything and the microphone doesn't pick up anything.

I saw that screen the first time I paired my Nokia BH-210 headset. No sound was input or output. Next time I opened the sound settings the wireless headset had dissapeared from the list of devices and it never got back. Removing the device, re-pairing, rebooting Ubuntu, etc., etc., etc. nothing made it come back. Of course there's no way to get audio to or from the headset.

I do hear a beep, however, when I connect or disconnect the headset from the bluetooth indicator. (It's a different one for connecting and disconnecting.) This means Ubuntu is perfectly aware the device is being connected and disconnected. IMO the audio subsystem (PulseAudio)  isn't being informed properly and so there's no way to stream audio to and from the headset.

I'll try all of that blueman advices here, but this should work out of the box.

---

### Post by UnknownDiety on 2012-11-11
Hopefully the advice works for you even though it didn't for me.

Bump

---

### Post by quequotion on 2012-11-12
> **AleveSicofante said:**
> I saw that screen the first time I paired my Nokia BH-210 headset. No sound was input or output. Next time I opened the sound settings the wireless headset had dissapeared from the list of devices and it never got back. Removing the device, re-pairing, rebooting Ubuntu, etc., etc., etc. nothing made it come back. Of course there's no way to get audio to or from the headset.

I do hear a beep, however, when I connect or disconnect the headset from the bluetooth indicator. (It's a different one for connecting and disconnecting.) This means Ubuntu is perfectly aware the device is being connected and disconnected. IMO the audio subsystem (PulseAudio)  isn't being informed properly and so there's no way to stream audio to and from the headset.

I'll try all of that blueman advices here, but this should work out of the box. *Please please please* [join my bug report]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1065380").

---

### Post by quequotion on 2012-11-12
> **UnknownDiety said:**
> Hopefully the advice works for you even though it didn't for me.

BumpI was playing around last night, and found that it is quite possible to play music through the HSP/HFP profile. Using settings in **blueman** and **pavucontrol**, I reconfigured my device as a Headset, then used pulseaudio to route to the headset.

It works, after a fashion. The audio quality is not great, it's telephony. Monaural only, low fidelity audio. It might sound better on a single-ear device, and not a pair of stereo headphones ([mine]("http://www.trywin.co.jp/item_detail/item_000025.html"), *Japanese* page).

Anyway, I'll give you more detail later if you need it:
1. Activate your paired bluetooth headset.
2. Use blueman to select the "Headset Service" profile (this should happen automatically, but there is [a bug]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1065380").
3. In pavucontrol (or "Sound Settings" may suffice) to connect to the HSP/HFP Device.
4. Set this device for output.
5. Later, when you dissconnect the device, pulseaudio will automatically return audio control to your default speakers (*that part works!*).

You have to do it all over again, each time.

---

### Post by UnknownDiety on 2012-11-12
> **quequotion said:**
> I was playing around last night, and found that it is quite possible to play music through the HSP/HFP profile. Using settings in **blueman** and **pavucontrol**, I reconfigured my device as a Headset, then used pulseaudio to route to the headset.

It works, after a fashion. The audio quality is not great, it's telephony. Monaural only, low fidelity audio. It might sound better on a single-ear device, and not a pair of stereo headphones ([mine]("http://www.trywin.co.jp/item_detail/item_000025.html"), *Japanese* page).

Anyway, I'll give you more detail later if you need it:
1. Activate your paired bluetooth headset.
2. Use blueman to select the "Headset Service" profile (this should happen automatically, but there is [a bug]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1065380").
3. In pavucontrol (or "Sound Settings" may suffice) to connect to the HSP/HFP Device.
4. Set this device for output.
5. Later, when you dissconnect the device, pulseaudio will automatically return audio control to your default speakers (*that part works!*).

You have to do it all over again, each time.

In pavucontrol they show up and the configuration tab says, "Headset Profile: Telephony Duplex." Though I don't know how to set the headset to be output or input in pavucontrol. I see a button to set as fallback, but I don't know what that means.

---

### Post by AleveSicofante on 2012-11-12
> **quequotion said:**
> *Please please please* [join my bug report]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1065380").

Sure. Done it. I wouldn't hold my breath, though. Many serious bugs affecting hundreds of people are ignored.  Canonical is more preoccupied about making Ubuntu "work" on tablets than making it just work. Hopefully a generous independent developer has the same problem and finds some free time to fix it.

---

### Post by quequotion on 2012-11-12
> **UnknownDiety said:**
> In pavucontrol they show up and the configuration tab says, "Headset Profile: Telephony Duplex." Though I don't know how to set the headset to be output or input in pavucontrol. I see a button to set as fallback, but I don't know what that means.In my case I have to select "Audio Sink" first, and then I can use those options in pavucontrol. I hoped this would not be necessary for your device, but I don't have a similar one to work with. Maybe you'll have to connect output another way.

Give the orinary sound settings dialog a shot.
1. Click the speaker icon (sound-indicator)
2. choose "Sound Settings..." from the menu. This should give you a dialog with tabs for "Output" and "Input" with a list of available audio devices.
Click once on a device to switch to it.
This crashes sometimes.

Somehow you need to get bluez to create initiate a bluetooth audio device, which is what happens when the "Audio Sink" profile is connected. I thought this profile only applied to H2DP, but perhaps it is also necessary for headsets...?

---

### Post by UnknownDiety on 2012-11-12
> **quequotion said:**
> In my case I have to select "Audio Sink" first, and then I can use those options in pavucontrol. I hoped this would not be necessary for your device, but I don't have a similar one to work with. Maybe you'll have to connect output another way.

Give the orinary sound settings dialog a shot.
1. Click the speaker icon (sound-indicator)
2. choose "Sound Settings..." from the menu. This should give you a dialog with tabs for "Output" and "Input" with a list of available audio devices.
Click once on a device to switch to it.
This crashes sometimes.

Somehow you need to get bluez to create initiate a bluetooth audio device, which is what happens when the "Audio Sink" profile is connected. I thought this profile only applied to H2DP, but perhaps it is also necessary for headsets...?

Hopefully having Audio Sink isn't necessary for this to work.

Whenever I do that I'm not getting any sound from headset and the microphone doesn't pick up any sound either whenever I try talking into it.

I don't know how to do that.

I appreciate your continued advice.

---

### Post by UnknownDiety on 2012-11-14
Bump

---

### Post by UnknownDiety on 2012-11-15
Bump

---

### Post by UnknownDiety on 2012-11-17
Bump

---

### Post by JoaoMachado on 2012-11-17
Still not fixed in 12.10!

This used to work so well, you would think Pulse Audio and Bluez would get this figured out. Thank God for Blueman!

Dell XPS13 - Ubuntu 12.10 - 64Bit

---

### Post by UnknownDiety on 2012-11-18
Bump

---

### Post by UnknownDiety on 2012-11-19
Bump

---

### Post by UnknownDiety on 2012-11-21
Bump

---

### Post by UnknownDiety on 2012-11-22
Bump

---

### Post by UnknownDiety on 2012-11-23
Bump

---

### Post by UnknownDiety on 2012-11-24
Bump

---

### Post by UnknownDiety on 2012-11-28
Bump

---

### Post by UnknownDiety on 2012-11-29
Bump

---

### Post by UnknownDiety on 2012-11-30
Bump

---

### Post by UnknownDiety on 2012-12-01
Bump

---

### Post by UnknownDiety on 2012-12-03
Bump

---

### Post by UnknownDiety on 2012-12-05
Bump

---

### Post by UnknownDiety on 2012-12-07
Bump

---

### Post by UnknownDiety on 2012-12-08
Bump

---

### Post by fercho15 on 2012-12-09
> **UnknownDiety said:**
> Bump

If your bluetooth device shows connectivity then your problem is not the device but the sound system itself. Once you gain connectivity follow these instructions.

1. Go to sound configuration --> you can use the finder that comes built-in with Ubuntu just write sound in the language of your system.

2. Once in the sound configuration utility, go to the hardware label. You must be able to see you handset below the icon of your hardware card. Select the Handset.

3. Down in the same place, you will find a dropbox with label "Profile". By default the option is "Duplex Telephony", change it to be "High Fidelity reproduction".

4. Test your handset using the button next to the dropbox (this is optional). 

5. Enjoy it. !!! (Mandatory)

---

### Post by UnknownDiety on 2012-12-11
> **fercho15 said:**
> If your bluetooth device shows connectivity then your problem is not the device but the sound system itself. Once you gain connectivity follow these instructions.

1. Go to sound configuration --> you can use the finder that comes built-in with Ubuntu just write sound in the language of your system.

2. Once in the sound configuration utility, go to the hardware label. You must be able to see you handset below the icon of your hardware card. Select the Handset.

3. Down in the same place, you will find a dropbox with label "Profile". By default the option is "Duplex Telephony", change it to be "High Fidelity reproduction".

4. Test your handset using the button next to the dropbox (this is optional). 

5. Enjoy it. !!! (Mandatory)

The only option is Duplex Telephony whenever I do that. I was under the impression that "HFR" was only for output.

Anytime I hit the test button it simply makes no sound.

---

### Post by UnknownDiety on 2012-12-13
Bump

---

### Post by UnknownDiety on 2012-12-17
Bump

---

### Post by UnknownDiety on 2012-12-19
Bump

---

### Post by UnknownDiety on 2012-12-22
Bump

---

### Post by UnknownDiety on 2012-12-23
Bump

---

### Post by UnknownDiety on 2012-12-25
Bump

---

### Post by UnknownDiety on 2012-12-29
Bump

---

### Post by UnknownDiety on 2012-12-31
Bump

---

### Post by UnknownDiety on 2013-01-01
Bump

---

### Post by UnknownDiety on 2013-01-03
Bump

---

### Post by UnknownDiety on 2013-01-10
Bump

---

### Post by UnknownDiety on 2013-01-18
Bump

---

### Post by UnknownDiety on 2013-01-19
Bump

---

### Post by targon on 2013-01-29
Thanks [quequotion]("http://ubuntuforums.org/member.php?u=711808") your post solved my problem.  I had been listening music in 12.04 about 3 months  in Asus G75V with BT headset using just default install with no problems whatsoever. Last weekend after playing with voip (so switching between A2DB and HSP/HFP profiles) suddenly sounds dissappeared. 

Headset didn't show up as output device in Sound Settings. Removing BT and repairing didn't bring audio back, but as you told installing blueman brings you back the control of output profiles.

---

### Post by Z8002 on 2013-02-10
First post, please be gentle.

Samsung NP3530EC laptop / Logitec headset. The combination works as expected under Windows 8 and XP.

With Xubuntu 12.10 I cannot get audio to play over the headphones: playback over the machine's speakers worked "out of the box".

I have Pulse audio and Blueman.

Blueman offers Audi Sink and Headset service, and thinks it's providing these: it does warn that the services are experimental.

Nowhere can I find the headset as an output device. My output choices are simply "speakers" or "headphones" .

Am I being a daft noob, or is this a related problem? Any suggestions?

Thanks,

Nick (Z8002)

---

### Post by marko5231 on 2013-02-19
Hello
I had really almost same problems until few days ago when my friend told me about one site.
It has great reviews of many bluetooth headsets and since webmasters are experts they helped me to solve my problem. I hope they can help you like they helped me.
[Bluetooth Headset]("http://www.best-bluetoothheadset.com/")

---

### Post by mrkusrk on 2014-01-08
First of all, the previous post is a spammer.

Secondly, I too am having this problem-- I can pair with my bluetooth headset through blueman, but I can't connect it to any services, nor see it with pavucontrol.
I have added this line to /etc/pulse/system.pa AND to /etc/pulse/default.pa
```
[COLOR=#000000][FONT=Ubuntu Mono]### Automatically redirect to newly available sinks
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]load-module module-switch-on-connect #Probably necessary... probably....[/FONT][/COLOR]
```

And added ```
[General]Enable=Source,Sink,Headset,Gateway,Control,Socket
Disable=Media
```

to /etc/bluetooth/audio.conf

These are, as far as I can tell, the two most common suggestions as far as how to get a working headset. Has any more progress been made?

---

