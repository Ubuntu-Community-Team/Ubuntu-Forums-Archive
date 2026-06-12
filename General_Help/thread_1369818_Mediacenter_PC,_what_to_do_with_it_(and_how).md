---
title: "Mediacenter PC, what to do with it (and how)?"
date: 2010-01-01
forum: General Help
---

### Post by blueturtl on 2010-01-01
I received a Fujitsu Siemens Scaleo E HTPC as a "Christmas present".

The owner said he bought it on a moment's whim and then it just sat in his garage until I went over to set up his new home theater just two days ago. It has some abuse marks on it (dented case, front door hinges broken) but today I fired it up supposedly for the second time that's ever been done and it ran just fine.

Specs as far as I know are:

[LIST]
[*]Intel Core2 Duo E6300 CPU
[*]1 GB RAM (my guess)
[*]320 GB HDD
[*]Intel integrated video (I think GMA965)
[*]Optiarc Dual-layer DVD-burner
[*]ASUS DVB-C tv-tuner
[*]Intel wired and Atheros wireless networking
[*]USB2 and firewire connectivity
[*]Realtek 7.1 channel built-in audio
[*]Component, VGA, S-Video, HDMI, and SCART outputs
[*]Memory card reader, RCA and S-VIDEO inputs
[/LIST]

Shortcomings:

[LIST]
[*]missing wireless antenna (can only connect via RJ45)
[*]wireless keyboard not functioning (I assume missing USB dongle)
[*]runs Windows XP Media Center (yuck)
[/LIST]

I was thinking about replacing the family PVR with this thing but a couple of questions linger: Can I replace the antenna to connect it to our LAN via wireless? Where would I find those (are they standard parts)? Is the CPU sufficient to use for say decoding hi-def content? If I were to use it as a PVR, will I need to get another tv-tuner for it (to view and record simultaneously)?

In short, how much am I going to have to invest to make this thing work for me?

Also obviously I'd prefer to run Ubuntu on it. :) I've been looking at the Moovida Media Center and I have to say this system could really rock in the living room. The only question is hardware support. I know Intel and Atheros are all good, but there are a LOT of special (and I suspect non-standard) hardware solutions in this system including the multiple sound and video inputs/outputs. What are my chances for getting those to work in Linux? Does anyone here have experience from setting up a similar system?

---

### Post by cariboo on 2010-01-01
A wireless antenna should be available from any well stocked computer/stationary store. THe only thing you have to watch out for is the connector, as there are a couple of different sizes.

I would suggest using the Live CD to see if all the hardware works.

---

### Post by blueturtl on 2010-01-02
Confirmed RAM at 1 GB, video card is GMA965 (aka X1300). I was thinking about hooking this up to our LCD-television directly via VGA. Is HDMI better though?

Bought a new wireless keyboard and antenna today. The antenna is compatible at least physically so I think it should work.

I'm going to test using a LiveCD once I get back home.

Couldn't find anything on the TV-tuner (ASUS TV7162V) but according to [this list]("http://www.linuxtv.org/wiki/index.php/DVB-C_PCIe_Cards") it shouldn't be supported as it's a PCI-express card.

I've got one free PCI slot though, so if I wanted PVR functionality I could look for a known compatible replacement. Recommendations are heartily welcomed as I know from experience even listed compatible hardware can some times be a no go.

---

### Post by blueturtl on 2010-01-05
So far looks very promising. Ubuntu installed great, I get working wired and wireless networking, 3D acceleration and sound!

The remote control doesn't work (not that important to me anyway).

The only thing that bugs me is that the screen resolution is a little off...

My Bravia does 1366x768 but I only get 1280x768 in my display preferences. This means there is a small area of the screen that goes unused in normal use and I get small black bars both at the top and at the bottom of the screen when viewing video.

Since there is no xorg.conf any more these days I'm a little unsure on how to proceed. How do I use the native mode of the TV?

---

### Post by blueturtl on 2010-04-29
Ok... turns out the Bravia will only accept 1280x768 through the VGA input. To use 1366x768 you need to use HDMI.

---

### Post by eriktheblu on 2010-04-29
For your second card, I know Hauppauge works pretty well. I use a WinTV HVR 1600 on my Mythbuntu machine, but I have no clue if that will work in Finland. The only issue is the Hauppauge card conflicts with the proprietary driver for my Nvidia card. A simple boot parameter edit corrected that.

---

### Post by blueturtl on 2010-12-06
I've been mistreating this thread for the past year, probably because I had so many things going on at the same time. Anyway, it's time for an update and the latest challenge...

For the tuner, I replaced the original with a Terratec Cinergy C HD which is [now supported]("http://ubuntuforums.org/showthread.php?t=1594805") directly in the kernel with just a few tweaks.

I also upgraded the video card because the built-in Intel was giving uneven performance (some HD videos would jerk) and also because for some reason the built-in HDMI connector refuses to work properly (and I wanted to use the full resolution of the Bravia).

The only low-profile video card my retailer had on-shelf was an ATi HD 4650 which I understand is a decent low-end card. It works really well, but runs really hot.

I also [upgraded the audio solution]("http://ubuntuforums.org/showthread.php?t=1539189") because surprisingly it was very substandard for home-theater use.

Also I found [this really cool wireless keyboard]("http://ubuntuforums.org/showthread.php?p=9980925#post9980925") .

The HTPC has been ultra-reliable in service, with Compiz, suspend and everything working wonderfully. However after the video card upgrade, it has been running rather hot: The CPU seems to idle around 74 degrees and I don't even dare measure the video card.

The cause seems simple as well, there is only one low-rpm fan cooling the CPU and the case has no proper air exhaust.

[IMG]http://www.saunalahti.fi/anmodino/scaleo/case_reopened.jpg[/IMG]

I was thinking about making a hole on top for a 80x80mm fan and setting that to pull air out of the case right from off the top of the video card. Due to the height of the case this would have to be an external installation (meaning very, very ugly) but for the time being, I can't think of another solution.

Any suggestions appreciated...

---

### Post by blueturtl on 2011-02-04
Final post. I've updated my website, and while at it finished tinkering with the computer.

The guide I've made can be found [here]("http://www.saunalahti.fi/anmodino/scaleo/"). It is mostly about tweaking the hardware though, I found that using the regular Gnome interface was a lot more easy for some reason than using any of the media center applications...

---

