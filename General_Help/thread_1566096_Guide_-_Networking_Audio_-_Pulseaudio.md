---
title: "Guide - Networking Audio - Pulseaudio"
date: 2010-09-01
forum: General Help
---

### Post by MetaDark on 2010-09-01
I could not find any current or easy guides to set up Pulseaudio's audio Networking on Ubuntu so I decided to make my own. This is my first guide so I hope it will be easy to follow.

Do you wish you could watch a movie on your laptop but have the ability to use those awesome surround sound speakers you have hooked up to your desktop? Or be able to record audio on your desktop straight from your laptop? Well, there is something called pulseaudio, it is not anything new, in fact, it has been the default audio driver of Ubuntu ever since Warty Warthog. If you want to figure out how to use these features not many people know about, follow the guide below.

To get started, type the following command (on all the machines you are networking) in the terminal to get the required tools.

```
sudo apt-get install paprefs pavucontrol
```

Once those are installed, run the following command in the terminal, on the machine that will host the audio.

```
paprefs
```

A dialog will pop up. Click on the "Network Access" tab and tick the check the box that says, "Make discoverable PulseAudio network sound devices available locally"

Once that is finished, open paprefs on your other machine, and in the second tab, "Network Sever" check, "Enable network access to local sound devices", "Allow other machines on the LAN to discover local sound devices", and just so we don't have to deal with authentication, check "Don't require authentication"

To make sure your machine hosting the audio can see your other machine, run the following command in the terminal on your hosting machine to open up another sound preference dialog.

```
pavucontrol
```

Click on the tab labeled, "Input Devices" and make sure it sees a sound monitor with an "@" symbol in the name.

In my case I will see, "Internal Audio Analog Stereo on **kurt@Kurtbuntu-mini**"

Where kurt is my username on the machine I want to send the audio to and Kurtbuntu-mini is the system name.

If it is not being listed, try checking and unchecking "Enable network access to local sound devices" on the audio receiving machine, if that doesn't work leave a comment below.

If you do have your machine listed, open a program like Rythmbox, Totem, Amarok... pretty much any program that can output sound.

Make sure you still have Volume Control (pavucontrol) open and click on the tab called "Playback"

You should see Rythmbox, Totem, Amarok or whatever you are using listed in the dialog if it is currently outputting sound.

If you don't see it, make sure the program is actually playing the song or outputting the audio. If it seems like it is and it is not being listed, click on the drop-down menu in the bottom right corner of the dialog and select "All Streams". If it is still not showing run the command;

```
killall pulseaudio
```

Now, if you do see it click on the drop-down menu beside the title and click on the option that has the same name as the name you saw earlier with the "@" symbol in it.

Once you've done that, slide up the volume to 100% on both the Right and Left slider, otherwise the playback will sound quieter on your other machine and have fun :D

---

