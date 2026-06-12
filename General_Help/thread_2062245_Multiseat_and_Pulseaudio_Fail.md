---
title: "Multiseat and Pulseaudio Fail"
date: 2012-09-24
forum: General Help
---

### Post by |Anthony| on 2012-09-24
**********************************UPDATE*********************************
* I have it mostly working. I'll share the details when i have it all figured out. *
***************************************************************************

I have a multi-seat setup working quite well. Hot plugging input devices  works as expected and such. The only issue I am still not able to  resolve is getting the audio for each seat.

Here is a summary of my attempts at getting audio to work:

1) Make ~/.pulse/default.pa dynamically configured based on which $DISPLAY the user logs in at.
  - [See this pastebin for the details]("http://pastebin.com/AsAjQTcy").

2) Load pulseaudio as a system-wide instance.
  - Couldn't get this to work. None of the audio hardware was accessible to the users.

3) Use udev rules to mark seats in ConsoleKit. Following udev guidelines found [here]("http://www.freedesktop.org/wiki/Software/systemd/multiseat").
  - I didn't think this would work, although it was "guaranteed" to work by someone in irc.freenode #pulseaudio

None  of those attempts yielded success, which is why I now turn to the  community for help. It is quite possible that the suggested methods work  and I just messed some aspect of it up, idk. This is the last piece of  the puzzle which is needed before I can go and update the [MultiseatX]("https://help.ubuntu.com/community/MultiseatX") page to include instructions for Ubuntu 12.04.


My understandings on the situation:
Access  to pulseaudio is restricted to the active session as marked by  ConsoleKit (something about an ACL). CK can only mark one session as  active at a time. This simple little fact of life leads me to believe  that the solution should involve pulseaudio being run as a system-wide  instance. Each user should connect to the pulse server and be limited to  a subset of all the hardware. Maybe each user connects to the pulse  server via localhost, idk. I do know that regardless of my attempts and  their failed results, I was always able to use **sudo aplay -D plughw:0,0 /usr/share/sounds/alsa/Front_Center.wav** to play something to any of the hardware.

I'm  grasping at straws and am now down to the last few hairs i can pull out  of my head. Please, help me figure this out so we can share the wealth.  Any additional information needed will be provided at your request.

Thanks
~ |Anthony|

---

### Post by |Anthony| on 2012-10-10
Well, I've got it all working now and have fully updated the [MultiseatX]("https://help.ubuntu.com/community/MultiseatX") page. Hopefully it will be useful to someone else.

---

### Post by poort on 2012-10-18
> **|Anthony| said:**
> **********************************UPDATE*********************************
* I have it mostly working. I'll share the details when i have it all figured out. *
***************************************************************************

I have a multi-seat setup working quite well. Hot plugging input devices  works as expected and such. The only issue I am still not able to  resolve is getting the audio for each seat.

Here is a summary of my attempts at getting audio to work:

1) Make ~/.pulse/default.pa dynamically configured based on which $DISPLAY the user logs in at.
  - [See this pastebin for the details]("http://pastebin.com/AsAjQTcy").

2) Load pulseaudio as a system-wide instance.
  - Couldn't get this to work. None of the audio hardware was accessible to the users.

3) Use udev rules to mark seats in ConsoleKit. Following udev guidelines found [here]("http://www.freedesktop.org/wiki/Software/systemd/multiseat").
  - I didn't think this would work, although it was "guaranteed" to work by someone in irc.freenode #pulseaudio

None  of those attempts yielded success, which is why I now turn to the  community for help. It is quite possible that the suggested methods work  and I just messed some aspect of it up, idk. This is the last piece of  the puzzle which is needed before I can go and update the [MultiseatX]("https://help.ubuntu.com/community/MultiseatX") page to include instructions for Ubuntu 12.04.


My understandings on the situation:
Access  to pulseaudio is restricted to the active session as marked by  ConsoleKit (something about an ACL). CK can only mark one session as  active at a time. This simple little fact of life leads me to believe  that the solution should involve pulseaudio being run as a system-wide  instance. Each user should connect to the pulse server and be limited to  a subset of all the hardware. Maybe each user connects to the pulse  server via localhost, idk. I do know that regardless of my attempts and  their failed results, I was always able to use **sudo aplay -D plughw:0,0 /usr/share/sounds/alsa/Front_Center.wav** to play something to any of the hardware.

I'm  grasping at straws and am now down to the last few hairs i can pull out  of my head. Please, help me figure this out so we can share the wealth.  Any additional information needed will be provided at your request.

Thanks
~ |Anthony|
Wel I am a professional multiseatcomputer seller 
Since users can take place at the seat they want ,i did need to make a script that sets a default sink according the display the user is on.But first I have to determine what soundcard is on what screen.i have also a detection script for that.
You need a default pulse sink per display, also if you have domain users.

---

### Post by |Anthony| on 2012-10-18
> **poort said:**
> Wel I am a professional multiseatcomputer seller ([www.multiseatcomputer.be]("http://www.multiseatcomputer.be"))
Since users can take place at the seat they want ,i did need to make a script that sets a default sink according the display the user is on.But first I have to determine what soundcard is on what screen.i have also a detection script for that.
You need a default pulse sink per display, also if you have domain users.
So are you going to share your script magic with the OpenSource/FreeSoftware community, or just link to your commercial site? ;)

---

### Post by poort on 2012-10-19
> **|Anthony| said:**
> So are you going to share your script magic with the OpenSource/FreeSoftware community, or just link to your commercial site? ;)
#!/bin/bash
sleep 7

if [ "$DISPLAY" ]
then
    if [ "$DISPLAY" = ":1" ]
    then
sleep 3
      pacmd "set-default-sink alsa_output.usb-0d8c_C-Media_USB_Headphone_Set-00-Set.analog-stereo"
pulseaudio -D
    fi
    if [ "$DISPLAY" = ":2" ]
    then
sleep 3
        pacmd "set-default-sink alsa_output.usb-SCEA_Inc._Logitech_USB_Headset-00-Headset.analog-stereo"
pulseaudio -D
    fi
if [ "$DISPLAY" = ":3" ]
    then
sleep 3
        pacmd "set-default-sink scherm3"
pulseaudio -D
    fi
if [ "$DISPLAY" = ":4" ]
    then
sleep 3
        pacmd "set-default-sink scherm4"
pulseaudio -D
    fi
if [ "$DISPLAY" = ":5" ]
    then
sleep 3
        pacmd "set-default-sink scherm5"
pulseaudio -D
    fi
if [ "$DISPLAY" = ":6" ]
    then
sleep 3
        pacmd "set-default-sink scherm6"
pulseaudio -D
    fi
fi

---

### Post by |Anthony| on 2012-10-19
> **poort said:**
> #!/bin/bash
sleep 7

if [ "$DISPLAY" ]
then
    if [ "$DISPLAY" = ":1" ]
    then
sleep 3
      pacmd "set-default-sink alsa_output.usb-0d8c_C-Media_USB_Headphone_Set-00-Set.analog-stereo"
pulseaudio -D
    fi

--SNIP--

    fi
fi

This doesn't make sense to me here. **pacmd** opens a cli to an existing pulseaudio daemon, but you're starting a new daemon after that statement with **pulseaudio -D**. This would also imply that you have suppressed starting pulseaudio by the normal means so that you can have your script launch each users pulseaudio daemon.

Also, this script would (ignoring that previous statement) imply that your are running PulseAudio in per user mode. It is not possible to do this in an Ubuntu multiseat environment unless you are also using the multiseat branches of ConsoleKit and GDM that i mention in the [MultiseatX wiki page]("https://help.ubuntu.com/community/MultiseatX#Introduction_To_Multiseat"). It could also be possible if you have modified the ACL for each file in /dev/snd (maybe, I haven't tested that yet).

Third. What calls this script? Is it appended to ~/.bashrc ? Is it a called by a startup .desktop file? Did you modify /etc/init.d/pulseaudio?

Share the knowledge sir :)

---

### Post by poort on 2012-10-19
> **|Anthony| said:**
> This doesn't make sense to me here. **pacmd** opens a cli to an existing pulseaudio daemon, but you're starting a new daemon after that statement with **pulseaudio -D**. This would also imply that you have suppressed starting pulseaudio by the normal means so that you can have your script launch each users pulseaudio daemon.

Also, this script would (ignoring that previous statement) imply that your are running PulseAudio in per user mode. It is not possible to do this in an Ubuntu multiseat environment unless you are also using the multiseat branches of ConsoleKit and GDM that i mention in the [MultiseatX wiki page]("https://help.ubuntu.com/community/MultiseatX#Introduction_To_Multiseat"). It could also be possible if you have modified the ACL for each file in /dev/snd (maybe, I haven't tested that yet).

Third. What calls this script? Is it appended to ~/.bashrc ? Is it a called by a startup .desktop file? Did you modify /etc/init.d/pulseaudio?

Share the knowledge sir :)
I do not think pulseaudio -D is needed.Sometimes pulseaudio dies, so i make sure is will start.
Pulseaudio is started per user session, do not ever start it systemwide.
I am still using gdm 2.20 or in debian gdm.Gdm3 does not support multiseat.And gdm-2.20 can be installed manually in ubu 12.04 or 12.10.Lightdm has not many features yet.
The pulse script is started in /etc/gdm/PreSession/Default, so when the user is logging in, he gets his default sink.
The pulse script needs to sleep a few seconds until the user his session is completed.
Note that i always talking about multiseat on one card: per video-card output a session.
Multiseat with one session per video-card is oldfasion: windows multiseat systems have plugandplay session per video output(gpu).Imagine six seat ubuntu multiseat: six videocards?No way.
I have also pulse sink detection scripts if you want.

There is only one good solution to avoid all these problems: assign a usb hub to a display(without writing udev rules,,).
Than you do not need all this coding.
And for multiseat on one card: multi drm nodes per videocard (they are working on this:[http://www.phoronix.com/scan.php?page=news_item&px=MTA3OTU](http://www.phoronix.com/scan.php?page=news_item&px=MTA3OTU))

---

### Post by |Anthony| on 2012-10-19
> **poort said:**
> I do not think pulseaudio -D is needed.Sometimes pulseaudio dies, so i make sure is will start.
Pulseaudio is started per user session, do not ever start it systemwide.
I am still using gdm 2.20 or in debian gdm.Gdm3 does not support multiseat.And gdm-2.20 can be installed manually in ubu 12.04 or 12.10.Lightdm has not many features yet.
The pulse script is started in /etc/gdm/PreSession/Default, so when the user is logging in, he gets his default sink.
The pulse script needs to sleep a few seconds until the user his session is completed.
Note that i always talking about multiseat on one card: per video-card output a session.
Multiseat with one session per video-card is oldfasion: windows multiseat systems have plugandplay session per video output(gpu).Imagine six seat ubuntu multiseat: six videocards?No way.
I have also pulse sink detection scripts if you want.

There is only one good solution to avoid all these problems: assign a usb hub to a display(without writing udev rules,,).
Than you do not need all this coding.
And for multiseat on one card: multi drm nodes per videocard (they are working on this:[http://www.phoronix.com/scan.php?page=news_item&px=MTA3OTU](http://www.phoronix.com/scan.php?page=news_item&px=MTA3OTU))


So you must be using xephyr if you have a single gpu running multiseat. The downside to that is there is no hardware acceleration or OpenGL support.

The one thing that confuses me is that I know for a fact that when multiple users are logged into the system ConsoleKit will only mark one session as active. ConsoleKit does not support multiseat at all. It is not yet seat aware. All "seats" we create through whatever means are considered (by ConsoleKit) as sessions of seat1. When a seat is considered active by CK, there are udev-acl rules applied to hardware. The first session to become active will be the one that has access to any of the audio hardware. all others will get Dummy Output in PulseAudio. I know this not only from extensive testing, but also because i have had several informative chats with CK and PulseAudio devs. So, are you using the multiseat branch of ConsoleKit, or maybe you are using systemd instead?

And how are you assigning a usb hub to a $DISPLAY without udev rules?

---

### Post by poort on 2012-10-20
> **|Anthony| said:**
> So you must be using xephyr if you have a single gpu running multiseat. The downside to that is there is no hardware acceleration or OpenGL support.

The one thing that confuses me is that I know for a fact that when multiple users are logged into the system ConsoleKit will only mark one session as active. ConsoleKit does not support multiseat at all. It is not yet seat aware. All "seats" we create through whatever means are considered (by ConsoleKit) as sessions of seat1. When a seat is considered active by CK, there are udev-acl rules applied to hardware. The first session to become active will be the one that has access to any of the audio hardware. all others will get Dummy Output in PulseAudio. I know this not only from extensive testing, but also because i have had several informative chats with CK and PulseAudio devs. So, are you using the multiseat branch of ConsoleKit, or maybe you are using systemd instead?

And how are you assigning a usb hub to a $DISPLAY without udev rules?

I am using Xgl + xevdevserver.
Assigning a usb hub to a $DISPLAY would be the solution, but it is not possible yet.

---

### Post by |Anthony| on 2012-10-20
> **poort said:**
> I am using Xgl + xevdevserver.
Assigning a usb hub to a $DISPLAY would be the solution, but it is not possible yet.
So you are using depreciated components ;)

Assigning a usb hub to a $DISPLAY is possible with udev as I have explained [here]("https://help.ubuntu.com/community/MultiseatX#Udev"). Doing that will also ensure that all devices plugged into the hub are assigned to the correct seat.

You still haven't commented on how your are overcoming the ACLs that consolekit is assigning to /dev/snd so that each user can access the sound hardware.

---

### Post by poort on 2012-10-21
> **|Anthony| said:**
> So you are using depreciated components ;)

Assigning a usb hub to a $DISPLAY is possible with udev as I have explained [here]("https://help.ubuntu.com/community/MultiseatX#Udev"). Doing that will also ensure that all devices plugged into the hub are assigned to the correct seat.

You still haven't commented on how your are overcoming the ACLs that consolekit is assigning to /dev/snd so that each user can access the sound hardware.
How do you mean depreciated components?gdm-2.20,xgl is installable in ubuntu 12.10 en debian 6(called gdm).
Can it be easier than this:
[https://www.youtube.com/watch?v=ryP0M2Jz2pg](https://www.youtube.com/watch?v=ryP0M2Jz2pg)

no special configuration for pulseaudio.All users can access all usb-audio.
The user has no access to any sound configuration.Only the pulse script is run upon login to set default sink.

Maybe for home self-made use the udev is possible, but customers need to be able to configure their mouse-keyboard and sound themselves.

---

