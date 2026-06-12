---
title: "no sound in headphones?"
date: 2009-10-14
forum: General Help
---

### Post by abhilashm86 on 2009-10-14
when i plug in headphones, no sound is coming, i checked preferences and settings, don't know what to do??
exrernal system sound works, but not headphones??

---

### Post by abhilashm86 on 2009-10-14
```
abhilash@abhi:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
abhilash@abhi:~$ 

```
this is my configrations.....

---

### Post by macabrem on 2009-10-14
> **abhilashm86 said:**
> when i plug in headphones, no sound is coming, i checked preferences and settings, don't know what to do??
exrernal system sound works, but not headphones??


Have headphones ever worked on your computer?

Do the headphones work on anything else, such as a radio?

I'm assuming you've already checked that the volume isn't muted?  

Does the volume work just fine without the headphones?

Try rebooting...  Also, try rebooting with the headphones plugged in...

---

### Post by abhilashm86 on 2009-10-14
> **macabrem said:**
> Have headphones ever worked on your computer?

Do the headphones work on anything else, such as a radio?

I'm assuming you've already checked that the volume isn't muted?  

Does the volume work just fine without the headphones?

Try rebooting...  Also, try rebooting with the headphones plugged in...

oh yes headphone works fine, also i tested on my ipod!! i tried rebooting, no results?? any problem in jaunty?

---

### Post by macabrem on 2009-10-14
I'm still fairly new to Ubuntu, but I found these threads which might help...

[http://www.linuxforums.org/forum/ubuntu-help/146987-headphone-jack-internal-speakers-problem.html](http://www.linuxforums.org/forum/ubuntu-help/146987-headphone-jack-internal-speakers-problem.html)

[http://ubuntuforums.org/showthread.php?t=1086379](http://ubuntuforums.org/showthread.php?t=1086379)

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Maybe something with the Alsa upgrade might help?  I'm not sure, I know that some of these posts are for other version of Ubuntu, but maybe if you can wade through the info it will help.  Let me know if this does help.

---

### Post by abhilashm86 on 2009-10-15
> **macabrem said:**
> I'm still fairly new to Ubuntu, but I found these threads which might help...

[http://www.linuxforums.org/forum/ubuntu-help/146987-headphone-jack-internal-speakers-problem.html](http://www.linuxforums.org/forum/ubuntu-help/146987-headphone-jack-internal-speakers-problem.html)

[http://ubuntuforums.org/showthread.php?t=1086379](http://ubuntuforums.org/showthread.php?t=1086379)

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Maybe something with the Alsa upgrade might help?  I'm not sure, I know that some of these posts are for other version of Ubuntu, but maybe if you can wade through the info it will help.  Let me know if this does help.

oh thanks for those links, now everytings fine, in volumecontrol->preferences, there is Independent HP, i made it off, now headphones are working:) 
btw, a suggestion, i'd plugged in headphone in myears, then i did this work, volume was damn full high, i got a big shock and attack!! oh god the sound just came from nowhere and blasted my ears!! was crazy:)

---

### Post by macabrem on 2009-10-17
Good, I'm glad they are working.  Sorry about the sound blast to your ears.  :)

---

### Post by juliobahar on 2009-12-04
Thanks this solved my problem...
Great job

---

### Post by fabrixx on 2009-12-30
> **abhilashm86 said:**
> oh thanks for those links, now everytings fine, in volumecontrol->preferences, there is Independent HP, i made it off, now headphones are working



In Ubuntu 9,10 in don't have volumecontrol->preferences 

What is independent HP ?

You have installed Alsa upgrade (links above) to solve ?

I have same problem with VT1708B  :(

---

### Post by shivankgandhi on 2010-04-01
I downloaded ALSA Mixer and did upgrade ALSA script 
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137). Worked for me ;).

---

### Post by jmboyd on 2010-05-03
Quick fix for no sound coming out of headphones in Karmic and Lucid.

After you have installed and upgraded Ubuntu click on Applications - Accessories - 

Terminal. Type in alsamixer. Use the up arrow key to take the Master F column to its 

highest. Use right arrow key to make the columns of Headphone, PCM, Front and Front 

Mi to the top of their columns. When you get to LFE just keep hitting the right arrow key

until you get to Independent and switch this to the off position with the down arrow.

Reboot and you should have sound coming out of your headphones. This works on my

machine.

AMD Phenom II x4 945
1 GB Radeon HD 3600
5 GB RAM
VIA VT1708B 8-CH
1 500 GB HDD for Windows 7 x64
1 500 GB HDD for Lucid Lynx 10.04 x64
ASUS M3A78-CM Motherboard

Regards,
John




> **fabrixx said:**
> In Ubuntu 9,10 in don't have volumecontrol->preferences 

What is independent HP ?

You have installed Alsa upgrade (links above) to solve ?

I have same problem with VT1708B  :(

---

### Post by fabrixx on 2010-05-03
I've solved with lucid swithing on Independent HP column in alsamixer.

I've write also a guide (in italian)
[http://www.osside.net/?p=3321](http://www.osside.net/?p=3321)

Ciao :)

---

### Post by pwabrahams on 2010-11-03
If you think you've solved the problem, look at the headphone setting in alsamixer.  If it's grayed out, changing Independent HP won't help.

---

### Post by fabrixx on 2010-11-03
I solved for Ubuntu 10.04 Lucid but i have same problem in Ubuntu 10.10, Hp independ setting is not gray but in Maverick change it have no effects :(

---

### Post by Crazedpsyc on 2010-11-03
Every sound problem I ever had was fixed by tweaking a few simple settings in padevchooser (Pulse Audio Device Chooser)
```
sudo apt-get install padevchooser
```

---

### Post by fabrixx on 2010-11-03
I know that tool but what settings you have modified?

---

### Post by pwabrahams on 2010-11-03
I've downloaded padevchooser and started it up, but I have no clue as to how to use it to solve the headphone problem.  It seems oriented towards network issues, and this does not seem in any way like a network-related issue.

---

### Post by Crazedpsyc on 2010-11-05
You have to go to Volume Control in padevchooser not the Manager. In that, everything is quite simple and pretty much self-explanatory such as the drop-down menu labeled Port: in the Output Devices tab where you can choose between (for me at least) "Analog Speakers" "Analog Output" (I use this most of the time because it automatically uses headphones when they are plugged in and then switches back to speakers when they are not) and finally "Analog Headphones"

---

