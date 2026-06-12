---
title: "Skype and Quickcam 900"
date: 2009-08-30
forum: General Help
---

### Post by Benzaa on 2009-08-30
I was wondering if some of you know how to change the input device in skype (new version).

It happens that I was able to simple select the input from the usb mic that comes integrated in the webcam but this new version only accepts PulseAudio. It doesnt let me select other option.

Does anyone knows a trick for this problem??

By the way, I tried installing pavucontrol and I can see the usb mic there, but I dont know how to make it as default.

---

### Post by whitethorn on 2009-08-30
Ah hah I had this problem today as well.  I can't use pavucontrol but I think that would probably be the fastest.  Open pavucontrol go to the tab for recording and set your mic to be the default microphone.  Oh I think you have to right click on it and choose set as default (that's how it was in 8.10)


If that doesn't work, then we have to change the a line in your ~/.pulse folder.  What we have to change is in the file ~/.pulse/something\default-source

First we make a backup of the folder.

```
cp -r ~/.pulse ~/pulse-backup
```

Next we have a look at the different microphones using the following command, and pipe the output to a file called output.

```
pactl list >> ~/output
```

Now open the file using gedit

```
gedit ~/output
```

Now have a look at the different modules what your looking for is the name pulse uses for the microphone you want to use.  Mine looks like this. Module 9 was default in pulse but I wanted to use the mic on my webcam, so I had to take the name from module 8

> 
Module #8
        Name: module-alsa-source
        Argument: device_id=1 source_name=alsa_input.usb_device_46d_990_210EEDE9_if2_sound_card_0_alsa_capture_0 tsched=0
        Usage counter: n/a
        Properties:


Module #9
        Name: module-alsa-source
        Argument: device_id=0 source_name=alsa_input.pci_8086_3a3e_sound_card_0_alsa_capture_0 tsched=0
        Usage counter: n/a
        Properties:


Ok so now we copy out the name of the sound device in my case

> alsa_input.usb_device_46d_990_210EEDE9_if2_sound_card_0_alsa_capture_0

So after the ...= till the empty space (have to be careful here)

Next we copy that line into the ~/.pulse/something:default-source file, just replace the line in there with the one you have and save it.  I had to restart my pc before it worked for me, logging out and back in didn't work. 

Oh and don't forget to delete the file when you're done 

```
rm ~/output
```

If you make a mistake or something just restore the backup

```
cp -r ~/pulse-backup ~/.pulse
```
But it should be easier just setting it to default in pavucontrol.

---

### Post by Benzaa on 2009-08-30
Thanks whitethorn,

Actually I was playing with pavucontrol and I found how it works. Now I understand how to change to different streams while recording in skype and other programs. Now that I see all the things that pulse can do, it seems that it could be quite useful.

Regarding your explanation, it helped me to understand some things that I didnt have quite clear. 

See you another time

---

