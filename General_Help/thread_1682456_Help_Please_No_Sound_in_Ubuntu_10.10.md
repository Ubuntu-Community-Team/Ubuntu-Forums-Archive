---
title: "Help Please No Sound in Ubuntu 10.10"
date: 2011-02-05
forum: General Help
---

### Post by Moga3331 on 2011-02-05
Hi, I have recently installed Ubuntu 10.10, everything is working fine apart from my sound.

I think all the drivers are installed correctly for my onboard sound but it's not working.

I'm using a Gigabyte K8NF-9 Ultra Motherboard with Onboard Sound.

CK805, ALC850. With Jack Sensing input/outputs.

I have a program in Windows XP where I can setup the Jack Sensing.

Is there a similar program for Ubuntu Linux.

Any help would be gratefully appreciated.

Kind Regards

Moga3331

---

### Post by Perfect Storm on 2011-02-06
1. Have you checked if the sound is disable/muted?

2. Go to System ---> Preferences ---> Sound

Check "Hardware", Input" and "Output" is correctly set.

---

### Post by Moga3331 on 2011-02-06
Hi, thank you for your reply.

I've checked, my sound isn't muted and I also removed the "MM" in Alsamixer

Still not working :(

Any idea's

Regards

Moga3331 :)

---

### Post by Perfect Storm on 2011-02-07
Okay.

Are you using Analog or digital? Which profile is available under sound and where is it plugged in in the computer?

---

### Post by Moga3331 on 2011-02-07
In Sound Preferences Output says Internal Audio Analog Stereo, and the bottom the connector is Analog Output/Amplifier.

I just have 2.0 speaker setup, 2 speakers plugged into 1 Jack socket.

Does this info help any ?.

Regards

Moga3331

---

### Post by dfarrell07 on 2011-02-07
I also have had problems with sound after a fresh Ubuntu install in the past, although none of my troubles ended up being serious or a driver issue.

Just generally, under sound preferences, check if the selected profile is correct. You can use the 'test speakers' functionality to test any profile you choose. Also, check the sound preferences -> output tab. Generally, have you examined everything under sound preferences closely?

---

### Post by dfarrell07 on 2011-02-07
> **Moga3331 said:**
> In Sound Preferences Output says Internal Audio Analog Stereo, and the bottom the connector is Analog Output/Amplifier.

I just have 2.0 speaker setup, 2 speakers plugged into 1 Jack socket.

Does this info help any ?.

Regards

Moga3331

Check the profile you have selected under the Sound Preferences -> Hardware tab (duplex works for me). Also, check the connector under analog Sound Preferences -> Output (analog speakers works for me, but play around with the other options).

^^common issues imho

---

### Post by Moga3331 on 2011-02-08
Hi Guys,

 I'm going to play about with Sound Preferences, I'll let you know how I get on :).

Kind Regards

Moga3331 :)

---

### Post by Moga3331 on 2011-02-08
Hi,

 Still no luck, no sound :(. My onboard sound is an AC97 and I thought it would work out the box. I'm sure all the drivers are in.

When playing about on Sound Preferences and testing various configurations, I did manage to get a crackle when I pressed test lol, but that was all.

Can I load and play a .mp3 and change settings while in Sound ?. I'm new to Ubuntu but could it be a Jack Sensing problem. Everything works in XP.

Thank you for your help :).

:)

Kind Regards

Moga3331

---

### Post by Perfect Storm on 2011-02-08
I know in previous release of Ubuntu with your soundcard, if you enable "Software modem" in "Additional Drivers" for specific modems it would turn off the motherboard sound card.
I'm not sure if it's still a problem? Did you enable something like that?


Lets dig a little further:
```
cat /proc/asound/modules
cat /etc/modprobe.d/alsa-base.conf

aplay -l

lshw -C multimedia
```

---

### Post by Moga3331 on 2011-02-08
Hi Guys,

 Thank you very very much for your help :).

My sound is now working! :).

I had to select 5.1 Sound Output in Preferences :).

I also had to put the speakers in another Jack on the back of my puter :).

Is there a good program you can recommend for .mp3 playback in Ubuntu, I used Winamp in XP ?.

Thank you again for all your help :).

Kind Regards

Moga3331 :)

---

### Post by Perfect Storm on 2011-02-08
Audacious looks/act like winamp in many things.

But if you're looking for player & music library the default Rhythmebox can do it.

---

### Post by Moga3331 on 2011-02-08
Hi Guys,

 My sound is now working!!! :-).

I had to select 5.1 Surround Sound and put the speakers in another Jack behind the computer :).

Thank you very very much for your help :).

Is there a good mp3 player like Winamp in XP.

Thank you very much again :).

Kind Regards

Moga3331 :)

---

### Post by Moga3331 on 2011-02-08
Hi again,

 As you know I have the sound working, I can play files in Audacious.

I cant hear any sound when it plays in Rhythmbox ?.

Thanks

Moga3331 :)

---

### Post by Perfect Storm on 2011-02-08
I don't have Rhythmbox installed so I can't help you there (I'm using Banshee Media Player instead).

---

